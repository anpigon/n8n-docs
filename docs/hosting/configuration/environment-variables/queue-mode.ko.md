#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 큐 모드 환경 변수
description: 자체 호스팅 n8n 인스턴스에서 큐 모드를 구성하는 환경 변수입니다.
contentType: reference
tags:
  - 환경 변수
hide:
  - toc
  - tags
---

# 큐 모드 환경 변수

--8<-- "_snippets/self-hosting/file-based-configuration.md"

필요에 따라 n8n을 다른 모드로 실행할 수 있습니다. 큐 모드는 최고의 확장성을 제공합니다. 자세한 내용은 [큐 모드](/hosting/scaling/queue-mode.md)를 참조하십시오.

| 변수 | 유형 | 기본값 | 설명 |
| :------- | :---- | :------- | :---------- |
| `QUEUE_BULL_PREFIX` | 문자열 | - | 모든 큐 키에 사용할 접두사입니다. |
| `QUEUE_BULL_REDIS_DB` | 숫자 | `0` | 사용되는 Redis 데이터베이스입니다. |
| `QUEUE_BULL_REDIS_HOST` | 문자열 | `localhost` | Redis 호스트입니다. |
| `QUEUE_BULL_REDIS_PORT` | 숫자 | `6379` | 사용되는 Redis 포트입니다. |
| `QUEUE_BULL_REDIS_USERNAME` | 문자열 | - | Redis 사용자 이름입니다(Redis 버전 6 이상 필요). Redis < 6 호환성을 위해 정의하지 마십시오. |
| `QUEUE_BULL_REDIS_PASSWORD` | 문자열 | - | Redis 암호입니다. |
| `QUEUE_BULL_REDIS_TIMEOUT_THRESHOLD` | 숫자 | `10000` | Redis 시간 초과 임계값(ms)입니다. |
| `QUEUE_BULL_REDIS_CLUSTER_NODES` | 문자열 | - | Redis 클라이언트가 초기에 연결할 Redis 클러스터 노드의 쉼표로 구분된 목록(형식: `host:port`)을 예상합니다. 큐 모드(`EXECUTIONS_MODE = queue`)에서 실행 중인 경우 이 변수를 설정하면 Redis 클라이언트 대신 Redis 클러스터 클라이언트가 생성되고 n8n은 `QUEUE_BULL_REDIS_HOST` 및 `QUEUE_BULL_REDIS_PORT`를 무시합니다. |
| `QUEUE_BULL_REDIS_TLS` | 부울 | `false` | Redis 연결에서 TLS를 활성화합니다. |
| `QUEUE_BULL_REDIS_DUALSTACK` | 부울 | `false` | Redis 연결에서 이중 스택 지원(IPv4 및 IPv6)을 활성화합니다. |
| `QUEUE_WORKER_TIMEOUT` (**사용 중단됨**) | 숫자 | `30` | **사용 중단됨** 대신 `N8N_GRACEFUL_SHUTDOWN_TIMEOUT`을 사용하십시오.<br/><br/>종료 시 작업자 프로세스를 종료하기 전에 n8n이 실행 중인 실행을 기다려야 하는 시간(초)입니다. |
| `QUEUE_HEALTH_CHECK_ACTIVE` | 부울 | `false` | 상태 확인을 활성화할지(true) 또는 비활성화할지(false) 여부입니다. |
| `QUEUE_HEALTH_CHECK_PORT` | 숫자 | - | 상태 확인을 제공할 포트입니다. |
| `QUEUE_WORKER_LOCK_DURATION` | 숫자 | `30000` | 작업자가 메시지 작업을 수행하는 임대 기간(ms)입니다. |
| `QUEUE_WORKER_LOCK_RENEW_TIME` | 숫자 | `15000` | 작업자가 임대 시간을 갱신해야 하는 빈도(ms)입니다. |
| `QUEUE_WORKER_STALLED_INTERVAL` | 숫자 | `30000` | 작업자가 중단된 작업을 확인해야 하는 빈도입니다(사용 안 함의 경우 0 사용). |
| `QUEUE_WORKER_MAX_STALLED_COUNT` | 숫자 | `1` | 중단된 작업이 다시 처리될 최대 횟수입니다. |

## 다중 메인 설정

자세한 내용은 [다중 메인 설정 구성](/hosting/scaling/queue-mode.md#configuring-multi-main-setup)을 참조하십시오.

| 변수 | 유형 | 기본값 | 설명 |
| :------- | :---- | :------- | :---------- |
| `N8N_MULTI_MAIN_SETUP_ENABLED` | 부울 | `false` | 큐 모드에 대한 다중 메인 설정을 활성화할지 여부입니다(라이선스 필요). |
| `N8N_MULTI_MAIN_SETUP_KEY_TTL` | 숫자 | `10` | 다중 메인 설정에서 리더 키의 수명(초)입니다. |
| `N8N_MULTI_MAIN_SETUP_CHECK_INTERVAL` | 숫자 | `3` | 다중 메인 설정에서 리더 확인 간격(초)입니다. |