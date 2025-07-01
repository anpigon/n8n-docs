#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
description: 상태 확인을 위한 메트릭 가져오기
contentType: howto
---

# 모니터링

인스턴스 상태를 확인하기 위해 호출할 수 있는 세 가지 API 엔드포인트가 있습니다: `/healthz`, `healthz/readiness` 및 `/metrics`.

<!-- vale off -->
## healthz 및 healthz/readiness
<!-- vale on -->
`/healthz` 엔드포인트는 표준 HTTP 상태 코드를 반환합니다. 200은 인스턴스에 연결할 수 있음을 나타냅니다. DB 상태를 나타내지는 않습니다. 자체 호스팅 및 클라우드 사용자 모두 사용할 수 있습니다.

엔드포인트에 액세스:

```
<your-instance-url>/healthz
```

`/healthz/readiness` 엔드포인트는 `/healthz` 엔드포인트와 유사하지만 DB가 연결되고 마이그레이션되어 인스턴스가 트래픽을 수락할 준비가 되면 HTTP 상태 코드 200을 반환합니다.

엔드포인트에 액세스:

```
<your-instance-url>/healthz/readiness
```


## 메트릭

`/metrics` 엔드포인트는 인스턴스의 현재 상태에 대한 자세한 정보를 제공합니다.

엔드포인트에 액세스:

```
<your-instance-url>/metrics
```

/// info | 기능 가용성
`/metrics` 엔드포인트는 n8n 클라우드에서 사용할 수 없습니다.
///
<!-- vale off -->
## 자체 호스팅 n8n에 대해 메트릭 및 healthz 활성화
<!-- vale on -->
`/metrics` 및 `/healthz` 엔드포인트는 기본적으로 비활성화되어 있습니다. 활성화하려면 n8n 인스턴스를 구성하십시오.

```shell
# 메트릭
N8N_METRICS=true
# healthz
QUEUE_HEALTH_CHECK_ACTIVE=true
```

환경 변수를 사용하여 인스턴스를 구성하는 방법에 대한 자세한 내용은 [구성 방법](/hosting/configuration/configuration-methods.md)을 참조하십시오.