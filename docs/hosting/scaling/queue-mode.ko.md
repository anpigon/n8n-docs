---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
contentType: howto
---

# 큐 모드

필요에 따라 n8n을 다른 모드로 실행할 수 있습니다. 큐 모드는 최고의 확장성을 제공합니다.

/// note | 바이너리 데이터 저장소
n8n은 파일 시스템의 바이너리 데이터 저장소와 함께 큐 모드를 지원하지 않습니다. 워크플로우가 큐 모드에서 바이너리 데이터를 유지해야 하는 경우 [S3 외부 저장소](./external-storage.md)를 사용할 수 있습니다.
///

## 작동 방식

큐 모드에서 실행할 때 여러 n8n 인스턴스가 설정되어 있으며, 하나의 주 인스턴스는 워크플로우 정보(예: 트리거)를 수신하고 작업자 인스턴스는 실행을 수행합니다.

각 작업자는 자체 Node.js 인스턴스이며 `main` 모드에서 실행되지만 높은 IOPS(초당 입출력 작업)로 인해 여러 동시 워크플로우 실행을 처리할 수 있습니다.

작업자 인스턴스를 사용하고 큐 모드에서 실행하면 워크로드 처리에 필요한 만큼 n8n을 확장(작업자 추가) 및 축소(작업자 제거)할 수 있습니다.

프로세스 흐름은 다음과 같습니다.

1. 주 n8n 인스턴스는 타이머 및 웹훅 호출을 처리하여 워크플로우 실행을 생성(실행하지는 않음)합니다.
2. 실행 ID를 메시지 브로커인 [Redis](#start-redis)에 전달합니다. Redis는 보류 중인 실행 큐를 유지하고 다음 사용 가능한 작업자가 선택할 수 있도록 합니다.
3. 풀의 작업자가 Redis에서 메시지를 선택합니다.
4. 작업자는 실행 ID를 사용하여 데이터베이스에서 워크플로우 정보를 가져옵니다.
5. 워크플로우 실행을 완료한 후 작업자는 다음을 수행합니다.
	- 결과를 데이터베이스에 씁니다.
	- 실행이 완료되었다고 Redis에 게시합니다.
6. Redis는 주 인스턴스에 알립니다.


!["주 n8n 인스턴스, Redis, n8n 작업자 및 n8n 데이터베이스 간의 데이터 흐름을 보여주는 다이어그램"](/_images/hosting/scaling/queue-mode-flow.png)

## 작업자 구성

작업자는 실제 작업을 수행하는 n8n 인스턴스입니다. 주 n8n 프로세스에서 실행해야 하는 워크플로우에 대한 정보를 수신하고 워크플로우를 실행하며 각 실행 후 상태를 업데이트합니다.

### 암호화 키 설정

n8n은 첫 시작 시 자동으로 암호화 키를 생성합니다. 원하는 경우 [환경 변수](/hosting/configuration/environment-variables/index.md)를 사용하여 사용자 지정 키를 제공할 수도 있습니다.

주 n8n 인스턴스의 암호화 키는 모든 작업자 및 웹훅 프로세서 노드와 공유되어야 이러한 작업자 노드가 데이터베이스에 저장된 자격 증명에 액세스할 수 있습니다.

[구성 파일](/hosting/configuration/configuration-methods.md)에서 각 작업자 노드에 대한 암호화 키를 설정하거나 해당 환경 변수를 설정하여 설정합니다.

```bash
export N8N_ENCRYPTION_KEY=<main_instance_encryption_key>
```

### 실행 모드 설정

/// note | 데이터베이스 고려 사항
n8n은 Postgres 13 이상을 사용하는 것을 권장합니다. 실행 모드가 `queue`로 설정된 n8n을 SQLite 데이터베이스와 함께 실행하는 것은 권장되지 않습니다.
///

다음 명령을 사용하여 주 인스턴스 및 모든 작업자에서 환경 변수 `EXECUTIONS_MODE`를 `queue`로 설정합니다.

```bash
export EXECUTIONS_MODE=queue
```

또는 [구성 파일](/hosting/configuration/environment-variables/index.md)에서 `executions.mode`를 `queue`로 설정할 수 있습니다.

### Redis 시작

/// note | 별도의 컴퓨터에서 Redis 실행
별도의 컴퓨터에서 Redis를 실행할 수 있으며, n8n 인스턴스에서 액세스할 수 있는지 확인하십시오.
///

Docker 컨테이너에서 Redis를 실행하려면 아래 지침을 따르십시오.

다음 명령을 실행하여 Redis 인스턴스를 시작합니다.

```
docker run --name some-redis -p 6379:6379  -d redis
```

기본적으로 Redis는 암호 없이 `localhost`의 포트 `6379`에서 실행됩니다. Redis 구성에 따라 주 n8n 프로세스에 대해 다음 구성을 설정합니다. 이렇게 하면 n8n이 Redis와 상호 작용할 수 있습니다.

| 구성 파일 사용 | 환경 변수 사용 | 설명 |
| ------ | ------ | ----- |
| `queue.bull.redis.host:localhost` | `QUEUE_BULL_REDIS_HOST=localhost` | 기본적으로 Redis는 `localhost`에서 실행됩니다. |
| `queue.bull.redis.port:6379` | `QUEUE_BULL_REDIS_PORT=6379` | 기본 포트는 `6379`입니다. Redis가 다른 포트에서 실행 중인 경우 값을 구성하십시오. |

다음 선택적 구성을 설정할 수도 있습니다.

| 구성 파일 사용 | 환경 변수 사용 | 설명 |
| ------ | ------ | ----- |
| `queue.bull.redis.username:USERNAME` | `QUEUE_BULL_REDIS_USERNAME` | 기본적으로 Redis는 사용자 이름이 필요하지 않습니다. 특정 사용자를 사용하는 경우 변수를 구성하십시오. |
| `queue.bull.redis.password:PASSWORD` | `QUEUE_BULL_REDIS_PASSWORD` | 기본적으로 Redis는 암호가 필요하지 않습니다. 암호를 사용하는 경우 변수를 구성하십시오. |
| `queue.bull.redis.db:0` | `QUEUE_BULL_REDIS_DB` | 기본값은 `0`입니다. 이 값을 변경하면 구성을 업데이트하십시오. |
| `queue.bull.redis.timeoutThreshold:10000ms` | `QUEUE_BULL_REDIS_TIMEOUT_THRESHOLD` | Redis를 사용할 수 없는 경우 n8n이 종료되기 전에 대기해야 하는 시간을 알려줍니다. 기본값은 `10000`(ms)입니다. |
| `queue.bull.gracefulShutdownTimeout:30` | `N8N_GRACEFUL_SHUTDOWN_TIMEOUT` | 작업자가 프로세스를 종료하기 전에 작업을 완료하기 위한 정상 종료 시간 초과입니다. 기본값은 `30`초입니다. |


이제 n8n 인스턴스를 시작하면 Redis 인스턴스에 연결됩니다.

### 작업자 시작

n8n이 워크플로우를 실행하려면 작업자 프로세스를 시작해야 합니다. 별도의 컴퓨터에서 작업자를 호스팅하려면 컴퓨터에 n8n을 설치하고 Redis 인스턴스 및 n8n 데이터베이스에 연결되어 있는지 확인하십시오.

루트 디렉토리에서 다음 명령을 실행하여 작업자 프로세스를 시작합니다.

```
./packages/cli/bin/n8n worker
```

Docker를 사용하는 경우 다음 명령을 사용하십시오.

```
docker run --name n8n-queue -p 5679:5678 docker.n8n.io/n8nio/n8n worker
```

여러 작업자 프로세스를 설정할 수 있습니다. 모든 작업자 프로세스가 Redis 및 n8n 데이터베이스에 액세스할 수 있는지 확인하십시오.

#### 작업자 서버

각 작업자 프로세스는 선택적 엔드포인트를 노출하는 서버를 실행합니다.

- `/healthz`: `QUEUE_HEALTH_CHECK_ACTIVE` 환경 변수를 활성화하면 작업자가 실행 중인지 여부를 반환합니다.
- `/healthz/readiness`: `QUEUE_HEALTH_CHECK_ACTIVE` 환경 변수를 활성화하면 작업자의 DB 및 Redis 연결이 준비되었는지 여부를 반환합니다.
- [자격 증명 재정의 엔드포인트](https://docs.n8n.io/embed/configuration/#credential-overwrites)
- [`/metrics`](https://docs.n8n.io/hosting/configuration/configuration-examples/prometheus/)

#### 실행 중인 작업자 보기

/// info | 기능 가용성
* 자체 호스팅 엔터프라이즈 플랜에서 사용 가능.
* 클라우드 엔터프라이즈에서 이 기능에 액세스하려면 [n8n에 문의](https://n8n-community.typeform.com/to/y9X2YuGa){:target=_blank .external-link}하십시오.
///

**설정** > **작업자**를 선택하여 n8n에서 실행 중인 작업자와 해당 성능 메트릭을 볼 수 있습니다.

## 큐로 n8n 실행

큐로 n8n을 실행하면 모든 프로덕션 워크플로우 실행이 작업자 프로세스에 의해 처리됩니다. 즉, 웹훅 호출도 작업자 프로세스에 위임되어 오버헤드와 추가 대기 시간이 발생할 수 있습니다.

Redis는 메시지 브로커 역할을 하고 데이터베이스는 데이터를 유지하므로 둘 다에 대한 액세스가 필요합니다. 이 설정으로 분산 시스템을 SQLite를 통해 실행하는 것은 지원되지 않습니다.

/// note | 데이터 마이그레이션
한 데이터베이스에서 다른 데이터베이스로 데이터를 마이그레이션하려면 내보내기 및 가져오기 명령을 사용할 수 있습니다. 이러한 명령을 사용하는 방법을 알아보려면 [n8n용 CLI 명령](/hosting/cli-commands.md#export-workflows-and-credentials) 설명서를 참조하십시오.
///

## 웹훅 프로세서

/// note | 명심하세요
웹훅 프로세스는 Redis에 의존하며 `EXECUTIONS_MODE` 환경 변수도 설정해야 합니다. 웹훅 프로세서 노드를 설정하려면 위의 [작업자 구성](#configuring-workers) 섹션을 따르십시오.
///

웹훅 프로세서는 n8n의 또 다른 확장 계층입니다. 웹훅 프로세서 구성은 선택 사항이며 들어오는 웹훅 요청을 확장할 수 있습니다.

이 방법을 사용하면 n8n이 엄청난 수의 병렬 요청을 처리할 수 있습니다. 웹훅 프로세스와 작업자를 적절하게 추가하기만 하면 됩니다. 웹훅 프로세스는 동일한 포트(기본값: `5678`)에서 요청을 수신합니다. 이러한 프로세스를 컨테이너 또는 별도의 컴퓨터에서 실행하고 요청을 적절하게 라우팅하는 로드 밸런싱 시스템을 갖추십시오.

n8n은 주 프로세스를 로드 밸런서 풀에 추가하는 것을 권장하지 않습니다. 주 프로세스를 풀에 추가하면 요청과 과도한 부하를 받을 수 있습니다. 이로 인해 n8n UI 편집, 보기 및 상호 작용 성능이 저하됩니다.

루트 디렉토리에서 다음 명령을 실행하여 웹훅 프로세서를 시작할 수 있습니다.

```
./packages/cli/bin/n8n webhook
```

Docker를 사용하는 경우 다음 명령을 사용하십시오.

```
docker run --name n8n-queue -p 5679:5678 -e "EXECUTIONS_MODE=queue" docker.n8n.io/n8nio/n8n webhook
```

### 웹훅 URL 구성

웹훅 URL을 구성하려면 주 n8n 인스턴스를 실행하는 컴퓨터에서 다음 명령을 실행하십시오.

```bash
export WEBHOOK_URL=https://your-webhook-url.com
```

구성 파일에서 이 값을 설정할 수도 있습니다.

### 로드 밸런서 구성

여러 웹훅 프로세스를 사용하는 경우 요청을 라우팅하려면 로드 밸런서가 필요합니다. n8n 인스턴스와 웹훅에 동일한 도메인 이름을 사용하는 경우 다음과 같이 요청을 라우팅하도록 로드 밸런서를 설정할 수 있습니다.

- `/webhook/*`과 일치하는 모든 요청을 웹훅 서버 풀로 리디렉션합니다.
- 다른 모든 경로(n8n 내부 API, 편집기용 정적 파일 등)는 주 프로세스로 라우팅되어야 합니다.

**참고:** 수동 워크플로우 실행의 기본 URL은 `/webhook-test/*`입니다. 이러한 URL이 주 프로세스로 라우팅되는지 확인하십시오.

구성 파일 `endpoints.webhook` 또는 `N8N_ENDPOINT_WEBHOOK` 환경 변수를 사용하여 이 경로를 변경할 수 있습니다. 이를 변경하는 경우 로드 밸런서를 적절하게 업데이트하십시오.

### 주 프로세스에서 웹훅 처리 비활성화(선택 사항)

워크플로우를 실행할 웹훅 프로세서가 있습니다. 주 프로세스에서 웹훅 처리를 비활성화할 수 있습니다. 이렇게 하면 모든 웹훅 실행이 웹훅 프로세서에서 실행됩니다. 구성 파일에서 `endpoints.disableProductionWebhooksOnMainProcess`를 `true`로 설정하여 n8n이 주 프로세스에서 웹훅 요청을 처리하지 않도록 합니다.

또는 다음 명령을 사용할 수 있습니다.

```bash
export N8N_DISABLE_PRODUCTION_MAIN_PROCESS=true
```

주 프로세스에서 웹훅 프로세스를 비활성화할 때 주 프로세스를 실행하고 로드 밸런서의 웹훅 풀에 추가하지 마십시오.

## 작업자 동시성 구성

`concurrency` 플래그를 사용하여 작업자가 병렬로 실행할 수 있는 작업 수를 정의할 수 있습니다. 기본값은 `10`입니다. 변경하려면 다음을 수행하십시오.

```bash
n8n worker --concurrency=5
```

## 동시성 및 확장 권장 사항

n8n은 작업자 인스턴스에 대해 동시성을 5 이상으로 설정하는 것을 권장합니다. 많은 수의 작업자와 함께 낮은 동시성 값을 설정하면 데이터베이스의 연결 풀이 소진되어 처리 지연 및 오류가 발생할 수 있습니다.

## 다중 주 설정

/// info | 기능 가용성
* 자체 호스팅 엔터프라이즈 플랜에서 사용 가능.
///

큐 모드에서는 고가용성을 위해 둘 이상의 `main` 프로세스를 실행할 수 있습니다.

단일 모드 설정에서 `main` 프로세스는 두 가지 작업을 수행합니다.

- **일반 작업**, 예: API 실행, UI 제공, 웹훅 수신 등
- **최대 한 번 작업**, 예: 비 HTTP 트리거(타이머, 폴러, RabbitMQ 및 IMAP와 같은 영구 연결) 실행, 실행 및 바이너리 데이터 정리 등

다중 주 설정에는 두 종류의 `main` 프로세스가 있습니다.

- **팔로워**, **일반 작업** 실행
- **리더**, **일반 및 최대 한 번 작업** 모두 실행

### 리더 지정

다중 주 설정에서 모든 주 인스턴스는 사용자에게 투명하게 리더십 프로세스를 처리합니다. 현재 리더가 충돌하거나 이벤트 루프가 너무 바빠서 사용할 수 없게 되면 다른 팔로워가 인계받을 수 있습니다. 이전 리더가 다시 응답하면 팔로워가 됩니다.

### 다중 주 설정 구성

n8n을 다중 주 설정으로 배포하려면 다음을 확인하십시오.

- 모든 `main` 프로세스가 큐 모드에서 실행 중이고 Postgres 및 Redis에 연결되어 있습니다.
- 모든 `main` 및 `worker` 프로세스가 동일한 버전의 n8n을 실행하고 있습니다.
- 모든 `main` 프로세스에 환경 변수 `N8N_MULTI_MAIN_SETUP_ENABLED`가 `true`로 설정되어 있습니다.
- 모든 `main` 프로세스가 세션 지속성(고정 세션)이 활성화된 로드 밸런서 뒤에서 실행되고 있습니다.

필요한 경우 리더 키 옵션을 조정할 수 있습니다.

| 구성 파일 사용 | 환경 변수 사용 | 설명 |
| ------ | ------ | ----- |
| `multiMainSetup.ttl:10` | `N8N_MULTI_MAIN_SETUP_KEY_TTL=10` | 다중 주 설정에서 리더 키의 수명(초)입니다. |
| `multiMainSetup.interval:3` | `N8N_MULTI_MAIN_SETUP_CHECK_INTERVAL=3` | 다중 주 설정에서 리더 확인 간격(초)입니다. |
