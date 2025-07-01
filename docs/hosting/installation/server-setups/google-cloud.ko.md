---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
contentType: tutorial
---

# Google Cloud에서 n8n 호스팅

이 호스팅 가이드는 Google Cloud(GCP)에서 n8n을 자체 호스팅하는 방법을 보여줍니다. Kubernetes를 사용하여 필요한 리소스와 리버스 프록시를 관리하는 데이터베이스 백엔드로 Postgres와 함께 n8n을 사용합니다.

## 전제 조건

- [gcloud 명령줄 도구](https://cloud.google.com/sdk/gcloud/){:target="_blank" .external-link}
- [gke-gcloud-auth-plugin](https://cloud.google.com/blog/products/containers-kubernetes/kubectl-auth-changes-in-gke){:target="_blank" .external-link} (먼저 gcloud CLI 설치)

--8<-- "_snippets/self-hosting/warning.md"

--8<-- "_snippets/self-hosting/installation/latest-next-version.md"

## 호스팅 옵션

Google Cloud는 Cloud Run(컨테이너 실행에 최적화됨), Compute Engine(VM) 및 Kubernetes Engine(Kubernetes로 실행되는 컨테이너)을 포함하여 n8n 호스팅에 적합한 여러 옵션을 제공합니다.

이 가이드에서는 Google Kubernetes Engine(GKE)을 호스팅 옵션으로 사용합니다. Kubernetes를 사용하려면 몇 가지 추가적인 복잡성과 구성이 필요하지만 수요 변화에 따라 n8n을 확장하는 가장 좋은 방법입니다.

이 가이드의 대부분의 단계에서는 Google Cloud UI를 사용하지만 [gcloud 명령줄 도구](https://cloud.google.com/sdk/gcloud/){:target="_blank" .external-link}를 사용하여 모든 단계를 수행할 수도 있습니다.

## 프로젝트 생성

GCP는 리소스와 구성을 논리적으로 구성하기 위해 프로젝트를 만들 것을 권장합니다. Google Cloud Console에서 n8n 배포를 위한 새 프로젝트를 만듭니다. 프로젝트 드롭다운 메뉴를 선택한 다음 **새 프로젝트** 버튼을 선택합니다. 그런 다음 새로 만든 프로젝트를 선택합니다. 이 가이드의 다른 단계를 따를 때 올바른 프로젝트가 선택되었는지 확인하십시오.

## Kubernetes Engine API 활성화

GKE는 기본적으로 활성화되어 있지 않습니다. 상단 검색 창에서 "Kubernetes"를 검색하고 결과에서 "Kubernetes Engine"을 선택합니다.

**활성화**를 선택하여 이 프로젝트에 대한 Kubernetes Engine API를 활성화합니다.

## 클러스터 생성

[GKE 서비스 페이지](https://console.cloud.google.com/kubernetes/list/overview){:target="_blank" .external-link}에서 **클러스터** > **생성**을 선택합니다. "표준" 클러스터 옵션을 선택했는지 확인하십시오. n8n은 "Autopilot" 클러스터에서 작동하지 않습니다. 위치와 같이 특별히 변경해야 할 사항이 없는 한 클러스터 구성을 기본값으로 둘 수 있습니다.

## Kubectl 컨텍스트 설정

이 가이드의 나머지 단계에서는 GCP 인스턴스를 Kubectl 컨텍스트로 설정해야 합니다. 클러스터 인스턴스의 세부 정보 페이지를 열고 **연결**을 선택하여 클러스터 인스턴스의 연결 세부 정보를 찾을 수 있습니다. 표시된 코드 조각은 gcloud CLI 도구에 대한 연결 문자열을 보여줍니다. gcloud CLI에 코드 조각을 붙여넣고 실행하여 로컬 Kubernetes 설정을 새 gcloud 클러스터를 사용하도록 변경합니다.

## 구성 리포지토리 복제

Kubernetes와 n8n에는 일련의 구성 파일이 필요합니다. [이 리포지토리](https://github.com/n8n-io/n8n-kubernetes-hosting/tree/gcp){:target="_blank" .external-link}에서 로컬로 복제할 수 있습니다. 다음 단계에서는 파일 구성과 정보를 추가하는 방법을 설명합니다.

다음 명령으로 리포지토리를 복제합니다.

```shell
git clone https://github.com/n8n-io/n8n-kubernetes-hosting.git -b gcp
```

그리고 복제한 리포지토리의 루트로 디렉토리를 변경합니다.

```shell
cd n8n-kubernetes-hosting
```

## Postgres 구성

더 큰 규모의 n8n 배포의 경우 Postgres는 SQLite보다 더 강력한 데이터베이스 백엔드를 제공합니다.

### 영구 저장을 위한 볼륨 생성

포드 재시작 간에 데이터를 유지하려면 Postgres 배포에 영구 볼륨이 필요합니다. GCP에서 Postgres를 실행하려면 특정 Kubernetes 스토리지 클래스가 필요합니다. 자세한 내용은 [이 가이드](https://cloud.google.com/architecture/deploying-highly-available-postgresql-with-gke){:target="_blank" .external-link}를 참조할 수 있지만 `storage.yaml` 매니페스트가 이를 생성합니다. `allowedTopologies` > `matchedLabelExpressions` > `values` 키 아래에서 스토리지를 생성할 지역을 변경할 수 있습니다. 기본적으로 `us-central`로 설정되어 있습니다.

```yaml
…
allowedTopologies:
  - matchLabelExpressions:
      - key: failure-domain.beta.kubernetes.io/zone
        values:
          - us-central1-b
          - us-central1-c
```

### Postgres 환경 변수

Postgres는 컨테이너에서 실행되는 애플리케이션에 전달하기 위해 일부 환경 변수를 설정해야 합니다.

예제 `postgres-secret.yaml` 파일에는 자체 값으로 바꿔야 하는 자리 표시자가 포함되어 있습니다. Postgres는 데이터베이스를 만들 때 이러한 세부 정보를 사용합니다.

`postgres-deployment.yaml` 매니페스트는 이 매니페스트 파일의 값을 사용하여 애플리케이션 포드에 보냅니다.

## n8n 구성

### 파일 저장을 위한 볼륨 생성

n8n 실행에 필수적이지는 않지만 영구 볼륨을 사용하는 것은 다음에 필요합니다.

* 바이너리 데이터 노드와 같이 파일과 상호 작용하는 노드 사용.
* 재시작 간에 [수동 n8n 암호화 키](/hosting/configuration/environment-variables/deployment.md)를 유지하려는 경우. 이렇게 하면 시작 중에 키가 포함된 파일을 파일 저장소에 저장합니다.

`n8n-claim0-persistentvolumeclaim.yaml` 매니페스트는 이를 생성하고 n8n 배포는 `n8n-deployment.yaml` 매니페스트의 `volumes` 섹션에서 해당 클레임을 마운트합니다.

```yaml
…
volumes:
  - name: n8n-claim0
    persistentVolumeClaim:
      claimName: n8n-claim0
…
```

### 포드 리소스

[Kubernetes를 사용하면](https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/) 선택적으로 애플리케이션 컨테이너에 필요한 최소 리소스와 실행할 수 있는 제한을 지정할 수 있습니다. 위에 복제된 예제 YAML 파일에는 `n8n-deployment.yaml` 및 `postgres-deployment.yaml` 파일의 `resources` 섹션에 다음이 포함되어 있습니다.

```yaml
…
resources:
  requests:
    memory: "250Mi"
  limits:
    memory: "500Mi"
…    
```

이는 컨테이너당 최소 250MB, 최대 500MB를 정의하고 Kubernetes가 CPU를 처리하도록 합니다. 필요에 맞게 이러한 값을 변경할 수 있습니다. 참고로 n8n 클라우드 제품의 리소스 값은 다음과 같습니다.

--8<-- "_snippets/self-hosting/installation/suggested-pod-resources.md"

### 선택 사항: 환경 변수

환경 변수를 사용하여 n8n 설정 및 동작을 구성할 수 있습니다.

`n8n-secret.yaml` 파일을 만듭니다. n8n 환경 변수 세부 정보는 [환경 변수](/hosting/configuration/environment-variables/index.md)를 참조하십시오.

## 배포

두 배포 매니페스트(`n8n-deployment.yaml` 및 `postgres-deployment.yaml`)는 n8n 및 Postgres 애플리케이션을 Kubernetes에 정의합니다.

매니페스트는 다음을 정의합니다.

- 정의된 환경 변수를 각 애플리케이션 포드에 보냅니다.
- 사용할 컨테이너 이미지를 정의합니다.
- `resources` 개체로 리소스 소비 제한을 설정합니다.
- 이전에 정의된 `volumes` 및 컨테이너에 볼륨을 마운트할 경로를 정의하는 `volumeMounts`.
- 확장 및 재시작 정책. 예제 매니페스트는 각 포드의 인스턴스 하나를 정의합니다. 필요에 맞게 이를 변경해야 합니다.

## 서비스

두 서비스 매니페스트(`postgres-service.yaml` 및 `n8n-service.yaml`)는 각각 포트 5432 및 5678을 사용하여 Kubernetes 로드 밸런서를 사용하여 서비스를 외부 세계에 노출합니다.

## Kubernetes 클러스터로 보내기

다음 명령으로 모든 매니페스트를 클러스터로 보냅니다.

```shell
kubectl apply -f .
```

/// note | 네임스페이스 오류
해당 리소스가 아직 준비되지 않았기 때문에 "n8n" 네임스페이스를 찾을 수 없다는 오류 메시지가 표시될 수 있습니다. 동일한 명령을 다시 실행하거나 다음 명령으로 먼저 네임스페이스 매니페스트를 적용할 수 있습니다.

```shell
kubectl apply -f namespace.yaml
```
///


## DNS 설정

n8n은 일반적으로 하위 도메인에서 작동합니다. 공급자와 함께 하위 도메인에 대한 DNS 레코드를 만들고 n8n 서비스의 IP 주소로 지정합니다. **엔드포인트** 열 아래에서 사용하려는 클러스터의 **서비스 및 수신** 메뉴 항목에서 n8n 서비스의 IP 주소를 찾습니다.

/// note | GKE 및 IP 주소
GKE 및 Kubernetes 리소스와 함께 예약된 IP 주소가 작동하는 방식에 대한 자세한 내용은 [이 GKE 자습서](https://cloud.google.com/kubernetes-engine/docs/tutorials/configuring-domain-name-static-ip#configuring_your_domain_name_records){:target="_blank" .external-link}를 참조하십시오.
///
## 리소스 삭제

다음 명령으로 매니페스트에서 생성된 리소스를 제거합니다.

```shell
kubectl delete -f .
```

## 다음 단계

--8<-- "_snippets/self-hosting/installation/server-setups-next-steps.md"
