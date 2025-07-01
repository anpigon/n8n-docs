#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
contentType: tutorial
---

# Azure에서 n8n 호스팅

이 호스팅 가이드는 Azure에서 n8n을 자체 호스팅하는 방법을 보여줍니다. Kubernetes를 사용하여 필요한 리소스와 리버스 프록시를 관리하는 데이터베이스 백엔드로 Postgres와 함께 n8n을 사용합니다.

## 전제 조건

[Azure 명령줄 도구](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli){:target="_blank" .external-link}가 필요합니다.

--8<-- "_snippets/self-hosting/warning.md"

--8<-- "_snippets/self-hosting/installation/latest-next-version.md"

## 호스팅 옵션

Azure는 Azure Container Instances(컨테이너 실행에 최적화됨), Linux 가상 머신 및 Azure Kubernetes Service(Kubernetes로 실행되는 컨테이너)를 포함하여 n8n 호스팅에 적합한 여러 가지 방법을 제공합니다.

이 가이드에서는 Azure Kubernetes Service(AKS)를 호스팅 옵션으로 사용합니다. Kubernetes를 사용하려면 몇 가지 추가적인 복잡성과 구성이 필요하지만 수요 변화에 따라 n8n을 확장하는 가장 좋은 방법입니다.

이 가이드의 단계에서는 Azure UI와 명령줄 도구를 혼합하여 사용하지만 대부분의 작업을 수행하는 데 둘 중 하나를 사용할 수 있습니다.

## Azure Kubernetes Service 열기

[Azure 포털](https://portal.azure.com/){:target="_blank" .external-link}에서 **Kubernetes 서비스**를 선택합니다.

## 클러스터 생성

Kubernetes 서비스 페이지에서 **생성** > **Kubernetes 클러스터 생성**을 선택합니다.

필요에 맞는 구성 옵션을 선택한 다음 완료되면 **생성**을 선택할 수 있습니다.

## Kubectl 컨텍스트 설정

이 가이드의 나머지 단계에서는 Azure 인스턴스를 Kubectl 컨텍스트로 설정해야 합니다. 클러스터 인스턴스의 세부 정보 페이지를 열고 **연결** 버튼을 선택하여 클러스터 인스턴스의 연결 세부 정보를 찾을 수 있습니다. 결과 코드 조각은 로컬 Kubernetes 설정을 새 클러스터를 사용하도록 변경하기 위해 터미널에 붙여넣고 실행할 단계를 보여줍니다.

## 구성 리포지토리 복제

Kubernetes와 n8n에는 일련의 구성 파일이 필요합니다. [이 리포지토리](https://github.com/n8n-io/n8n-kubernetes-hosting/tree/azure){:target="_blank" .external-link}에서 복제할 수 있습니다. 다음 단계에서는 어떤 파일을 구성하고 무엇을 변경해야 하는지 설명합니다.

다음 명령으로 리포지토리를 복제합니다.

```shell
git clone https://github.com/n8n-io/n8n-kubernetes-hosting.git -b azure
```

그리고 복제한 리포지토리의 루트로 디렉토리를 변경합니다.

```shell
cd azure
```

## Postgres 구성

더 큰 규모의 n8n 배포의 경우 Postgres는 SQLite보다 더 강력한 데이터베이스 백엔드를 제공합니다.

### 영구 저장을 위한 볼륨 구성

포드 재시작 간에 데이터를 유지하려면 Postgres 배포에 영구 볼륨이 필요합니다. 기본 스토리지 클래스는 이 목적에 적합하며 `postgres-claim0-persistentvolumeclaim.yaml` 매니페스트에 정의되어 있습니다.

/// note | 특수 스토리지 클래스
스토리지 클래스에 대한 특수하거나 더 높은 요구 사항이 있는 경우 [설명서에서 Azure가 제공하는 옵션에 대해 자세히 알아보십시오](https://learn.microsoft.com/en-us/azure/aks/concepts-storage#storage-classes){:target="_blank" .external-link}.
///
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

[Kubernetes를 사용하면](https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/){:target="_blank" .external-link} 선택적으로 애플리케이션 컨테이너에 필요한 최소 리소스와 실행할 수 있는 제한을 지정할 수 있습니다. 위에 복제된 예제 YAML 파일에는 `n8n-deployment.yaml` 파일의 `resources` 섹션에 다음이 포함되어 있습니다.

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

n8n은 일반적으로 하위 도메인에서 작동합니다. 공급자와 함께 하위 도메인에 대한 DNS 레코드를 만들고 n8n 서비스의 IP 주소로 지정합니다. **외부 IP** 열 아래에서 사용하려는 클러스터의 **서비스 및 수신** 메뉴 항목에서 n8n 서비스의 IP 주소를 찾습니다. URL에 n8n 포트 "5678"을 추가해야 합니다.

/// note | AKS가 있는 정적 IP 주소
AKS와 함께 정적 IP 주소를 사용하는 방법에 대한 자세한 내용은 [이 자습서](https://learn.microsoft.com/en-us/azure/aks/static-ip){:target="_blank" .external-link}를 참조하십시오.
///
## 리소스 삭제

다음 명령으로 매니페스트에서 생성된 리소스를 제거합니다.

```shell
kubectl delete -f .
```

## 다음 단계

--8<-- "_snippets/self-hosting/installation/server-setups-next-steps.md"