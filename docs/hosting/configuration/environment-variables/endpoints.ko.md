---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 엔드포인트 환경 변수
description: 자체 호스팅 n8n 인스턴스에 대한 환경 변수로 애플리케이션의 API 및 웹훅 엔드포인트를 사용자 지정합니다.
contentType: reference
tags:
  - 환경 변수
hide:
  - toc
  - tags
---

# 엔드포인트 환경 변수

--8<-- "_snippets/self-hosting/file-based-configuration.md"

이 페이지에는 n8n에서 엔드포인트를 사용자 지정하기 위한 환경 변수가 나열되어 있습니다.

| 변수 | 유형 | 기본값 | 설명 |
| :------- | :---- | :------- | :---------- |
| `N8N_PAYLOAD_SIZE_MAX` | 숫자 | `16` | 최대 페이로드 크기(MiB)입니다. |
| `N8N_FORMDATA_FILE_SIZE_MAX` | 숫자 | `200` | form-data 웹훅 페이로드의 파일에 대한 최대 페이로드 크기(MiB)입니다. |
| `N8N_METRICS` | 부울 | `false` | `/metrics` 엔드포인트를 활성화할지 여부입니다. |
| `N8N_METRICS_PREFIX` | 문자열 | `n8n_` | n8n 특정 메트릭 이름에 대한 선택적 접두사입니다. |
| `N8N_METRICS_INCLUDE_DEFAULT_METRICS` | 부울 | `true` | 기본 시스템 및 node.js 메트릭을 노출할지 여부입니다. |
| `N8N_METRICS_INCLUDE_CACHE_METRICS` | 부울 | false | 캐시 적중 및 누락에 대한 메트릭을 포함할지(true) 여부(false)입니다. |
| `N8N_METRICS_INCLUDE_MESSAGE_EVENT_BUS_METRICS` | 부울 | `false` | 이벤트에 대한 메트릭을 포함할지(true) 여부(false)입니다. |
| `N8N_METRICS_INCLUDE_WORKFLOW_ID_LABEL` | 부울 | `false` | 워크플로우 메트릭에 워크플로우 ID에 대한 레이블을 포함할지 여부입니다. |
| `N8N_METRICS_INCLUDE_NODE_TYPE_LABEL` | 부울 | `false` | 노드 메트릭에 노드 유형에 대한 레이블을 포함할지 여부입니다. |
| `N8N_METRICS_INCLUDE_CREDENTIAL_TYPE_LABEL` | 부울 | `false` | 자격 증명 메트릭에 자격 증명 유형에 대한 레이블을 포함할지 여부입니다. |
| `N8N_METRICS_INCLUDE_API_ENDPOINTS` | 부울 | `false` | API 엔드포인트에 대한 메트릭을 노출할지 여부입니다. |
| `N8N_METRICS_INCLUDE_API_PATH_LABEL` | 부울 | `false` | API 호출 경로에 대한 레이블을 포함할지 여부입니다. |
| `N8N_METRICS_INCLUDE_API_METHOD_LABEL` | 부울 | `false` | API 호출의 HTTP 메서드(GET, POST, ...)에 대한 레이블을 포함할지 여부입니다. |
| `N8N_METRICS_INCLUDE_API_STATUS_CODE_LABEL` | 부울 | `false` | API 호출의 HTTP 상태 코드(200, 404, ...)에 대한 레이블을 포함할지 여부입니다. |
| `N8N_METRICS_INCLUDE_QUEUE_METRICS` | 부울 | `false` | 스케일링 모드에서 작업에 대한 메트릭을 포함할지 여부입니다. 다중 메인 설정에서는 지원되지 않습니다. |
| `N8N_METRICS_QUEUE_METRICS_INTERVAL` | 정수 | `20` | 큐 메트릭을 업데이트하는 빈도(초)입니다. |
| `N8N_ENDPOINT_REST` | 문자열 | `rest` | REST 엔드포인트에 사용되는 경로입니다. |
| `N8N_ENDPOINT_WEBHOOK` | 문자열 | `webhook` | 웹훅 엔드포인트에 사용되는 경로입니다. |
| `N8N_ENDPOINT_WEBHOOK_TEST` | 문자열 | `webhook-test` | 테스트 웹훅 엔드포인트에 사용되는 경로입니다. |
| `N8N_ENDPOINT_WEBHOOK_WAIT` | 문자열 | `webhook-waiting` | 대기 웹훅 엔드포인트에 사용되는 경로입니다. |
| `WEBHOOK_URL` | 문자열 | - | 리버스 프록시 뒤에서 n8n을 실행할 때 웹훅 URL을 수동으로 제공하는 데 사용됩니다. 자세한 내용은 [여기](/hosting/configuration/configuration-examples/webhook-url.md)를 참조하십시오. |
| `N8N_DISABLE_PRODUCTION_MAIN_PROCESS` | 부울 | `false` | 주 프로세스에서 프로덕션 웹훅을 비활성화합니다. 이는 웹훅 특정 프로세스를 사용할 때 주 프로세스에 대한 HTTP 트래픽 부하가 없도록 하는 데 도움이 됩니다. |
