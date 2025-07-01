#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
contentType: tutorial
---

# Amazon Web Services에서 n8n 호스팅

이 호스팅 가이드는 Amazon Web Services(AWS)에서 n8n을 자체 호스팅하는 방법을 보여줍니다. Kubernetes를 사용하여 필요한 리소스와 리버스 프록시를 관리하는 데이터베이스 백엔드로 Postgres와 함께 n8n을 사용합니다.

## 호스팅 옵션

AWS는 EC2(가상 머신) 및 EKS(Kubernetes로 실행되는 컨테이너)를 포함하여 n8n 호스팅에 적합한 여러 가지 방법을 제공합니다.

이 가이드에서는 [EKS](https://aws.amazon.com/eks/){:target=_blank .external-link}를 호스팅 옵션으로 사용합니다. Kubernetes를 사용하려면 몇 가지 추가적인 복잡성과 구성이 필요하지만 수요 변화에 따라 n8n을 확장하는 가장 좋은 방법입니다.

## 전제 조건

이 가이드의 단계에서는 AWS UI와 [EKS용 eksctl CLI 도구](https://eksctl.io){:target=_blank .external-link}를 혼합하여 사용합니다.

eksctl 설명서에는 언급되어 있지 않지만 [AWS CLI 도구를 설치](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html){:target=_blank .external-link}하고 [도구의 인증을 구성](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html){:target=_blank .external-link}해야 합니다.

--8<-- "_snippets/self-hosting/warning.md"

--8<-- "_snippets/self-hosting/installation/latest-next-version.md"

## 클러스터 생성

eksctl 도구를 사용하여 다음 명령으로 이름과 지역을 지정하여 클러스터를 생성합니다.

```shell
eksctl create cluster --name n8n --region <your-aws-region>
```

클러스터를 생성하는 데 시간이 걸릴 수 있습니다.


클러스터가 생성되면 eksctl은 자동으로 kubectl 컨텍스트를 클러스터로 설정합니다.

## 구성 리포지토리 복제

Kubernetes와 n8n에는 일련의 구성 파일이 필요합니다. [이 리포지토리](https://github.com/n8n-io/n8n-kubernetes-hosting/tree/aws){:target=_blank .external-link}에서 복제할 수 있습니다. 다음 단계에서는 각 파일의 기능과 변경해야 할 설정을 설명합니다.

다음 명령으로 리포지토리를 복제합니다.

```shell
git clone https://github.com/n8n-io/n8n-kubernetes-hosting.git -b aws
```

그리고 복제한 리포지토리의 루트로 디렉토리를 변경합니다.

```shell
cd n8n-kubernetes-hosting
```

## Postgres 구성

더 큰 규모의 n8n 배포의 경우 Postgres는 SQLite보다 더 강력한 데이터베이스 백엔드를 제공합니다.

### 영구 저장을 위한 볼륨 구성

포드 재시작 간에 데이터를 유지하려면 Postgres 배포에 영구 볼륨이 필요합니다. 기본 AWS 스토리지 클래스인 [gp2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/general-purpose.html#EBSVolumeTypes_gp2){:target=_blank .external-link}는 이 목적에 적합합니다. 이는 `postgres-claaim0-persistentvolumeclaim.yaml` 매니페스트에 정의되어 있습니다.

```yaml
…
spec:
  storageClassName: gp2
  accessModes:
    - ReadWriteOnce
…
```

### Postgres 환경 변수

Postgres는 컨테이너에서 실행되는 애플리케이션에 전달하기 위해 일부 환경 변수를 설정해야 합니다.

예제 `postgres-secret.yaml` 파일에는 사용자 세부 정보 및 사용할 데이터베이스에 대해 자체 값으로 바꿔야 하는 자리 표시자가 포함되어 있습니다.

`postgres-deployment.yaml` 매니페스트는 이 매니페스트 파일의 값을 사용하여 애플리케이션 포드에 보냅니다.

## n8n 구성

### 파일 저장을 위한 볼륨 생성

n8n 실행에 필수적이지는 않지만 영구 볼륨을 사용하면 n8n을 사용하는 동안 업로드된 파일을 유지하는 데 도움이 되며 재시작 간에 [수동 n8n 암호화 키](/hosting/configuration/environment-variables/deployment.md)를 유지하려는 경우 시작 중에 키가 포함된 파일을 파일 저장소에 저장합니다.

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

[Kubernetes](https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/){:target=_blank .external-link}를 사용하면 애플리케이션 컨테이너에 필요한 최소 리소스와 실행할 수 있는 제한을 지정할 수 있습니다. 위에 복제된 예제 YAML 파일에는 `n8n-deployment.yaml` 파일의 `resources` 섹션에 다음이 포함되어 있습니다.

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
- 리소스 소비 제한을 설정합니다.
- 이전에 정의된 `volumes` 및 컨테이너에 볼륨을 마운트할 경로를 정의하는 `volumeMounts`.
- 확장 및 재시작 정책. 예제 매니페스트는 각 포드의 인스턴스 하나를 정의합니다. 필요에 맞게 이를 변경해야 합니다.

## 서비스

두 서비스 매니페스트(`postgres-service.yaml` 및 `n8n-service.yaml`)는 기본적으로 각각 포트 5432 및 5678을 사용하여 Kubernetes 로드 밸런서를 사용하여 서비스를 외부 세계에 노출합니다.

## Kubernetes 클러스터로 보내기

`n8n-kubernetes-hosting` 디렉토리에서 다음 명령을 실행하여 모든 매니페스트를 클러스터로 보냅니다.

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

n8n은 일반적으로 하위 도메인에서 작동합니다. 공급자와 함께 하위 도메인에 대한 DNS 레코드를 만들고 인스턴스의 정적 주소로 지정합니다.

인스턴스에서 실행 중인 n8n 서비스의 주소를 찾으려면:

1. AWS 콘솔의 **Amazon Elastic Kubernetes Service** 페이지의 **클러스터** 섹션을 엽니다.
2. 클러스터 이름을 선택하여 구성 페이지를 엽니다.
3. **리소스** 탭을 선택한 다음 **서비스 및 네트워킹** > **서비스**를 선택합니다.
4. **n8n** 서비스를 선택하고 **로드 밸런서 URL** 값을 복사합니다. DNS에 n8n 서비스 포트(5678)를 접미사로 붙인 이 값을 사용합니다.

/// note | HTTP 사용
이 가이드는 `n8n-deployment.yaml`과 같이 정의하는 서비스에 HTTP 연결을 사용합니다. 그러나 **로드 밸런서 URL** 값을 클릭하면 EKS가 "HTTPS" URL로 이동하여 오류가 발생합니다. 이 문제를 해결하려면 n8n 하위 도메인을 열 때 HTTP를 사용해야 합니다.
///
## 리소스 삭제

설정을 삭제해야 하는 경우 다음 명령으로 매니페스트에서 생성된 리소스를 제거할 수 있습니다.

```shell
kubectl delete -f .
```

## 다음 단계

--8<-- "_snippets/self-hosting/installation/server-setups-next-steps.md"