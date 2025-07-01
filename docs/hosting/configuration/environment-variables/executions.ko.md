#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 실행 환경 변수
description: 워크플로우 실행과 관련된 설정을 구성하는 환경 변수입니다.
contentType: reference
tags:
  - 환경 변수
hide:
  - toc
  - tags
---

# 실행 환경 변수

--8<-- "_snippets/self-hosting/file-based-configuration.md"

이 페이지에는 워크플로우 실행 설정을 구성하는 환경 변수가 나열되어 있습니다.

| 변수 | 유형 | 기본값 | 설명 |
| :------- | :---- | :------- | :---------- |
| `EXECUTIONS_MODE` | 열거형 문자열: `regular`, `queue` | `regular` | 실행을 직접 실행할지 또는 큐를 사용하여 실행할지 여부입니다.<br><br>자세한 내용은 [큐 모드](/hosting/scaling/queue-mode.md)를 참조하십시오. |
| `EXECUTIONS_TIMEOUT` | 숫자 | `-1` | n8n이 실행을 중지한 후 모든 워크플로우에 대한 기본 시간 초과(초)를 설정합니다. 사용자는 `EXECUTIONS_TIMEOUT_MAX`에 설정된 기간까지 개별 워크플로우에 대해 이 값을 재정의할 수 있습니다. 비활성화하려면 `EXECUTIONS_TIMEOUT`을 `-1`로 설정하십시오. |
| `EXECUTIONS_TIMEOUT_MAX` | 숫자 | `3600` | 사용자가 개별 워크플로우에 대해 설정할 수 있는 최대 실행 시간(초)입니다. |
| `EXECUTIONS_DATA_SAVE_ON_ERROR` | 열거형 문자열: `all`, `none` | `all` | n8n이 오류 발생 시 실행 데이터를 저장할지 여부입니다. |
| `EXECUTIONS_DATA_SAVE_ON_SUCCESS` | 열거형 문자열: `all`, `none` | `all` | n8n이 성공 시 실행 데이터를 저장할지 여부입니다. |
| `EXECUTIONS_DATA_SAVE_ON_PROGRESS` | 부울 | `false` | 실행된 각 노드에 대한 진행 상황을 저장할지(true) 여부(false)입니다. |
| `EXECUTIONS_DATA_SAVE_MANUAL_EXECUTIONS` | 부울 | `true` | 수동으로 시작했을 때 실행 데이터를 저장할지 여부입니다. |
| `EXECUTIONS_DATA_PRUNE` | 부울 | `true` | 과거 실행 데이터를 순차적으로 삭제할지 여부입니다. |
| `EXECUTIONS_DATA_MAX_AGE` | 숫자 | `336` | 삭제되기 전의 실행 기간(시간)입니다. |
| `EXECUTIONS_DATA_PRUNE_MAX_COUNT` | 숫자 | `10000` | 데이터베이스에 보관할 최대 실행 수입니다. 0 = 제한 없음 |
| `EXECUTIONS_DATA_HARD_DELETE_BUFFER` | 숫자 | `1` | 하드 삭제되기 위해 완료된 실행 데이터가 얼마나 오래되어야 하는지(시간)입니다. 기본적으로 이 버퍼는 사용자가 워크플로우를 빌드하는 동안 필요할 수 있으므로 최근 실행을 제외합니다. |
| `EXECUTIONS_DATA_PRUNE_HARD_DELETE_INTERVAL` | 숫자 | `15` | 실행 데이터를 얼마나 자주(분) 하드 삭제해야 하는지입니다. |
| `EXECUTIONS_DATA_PRUNE_SOFT_DELETE_INTERVAL` | 숫자 | `60` | 실행 데이터를 얼마나 자주(분) 소프트 삭제해야 하는지입니다. |
| `N8N_CONCURRENCY_PRODUCTION_LIMIT` | 숫자 | `-1` | 일반 및 확장 모드 모두에서 동시에 실행할 수 있는 최대 프로덕션 실행 수입니다. 일반 모드에서 비활성화하려면 `-1`입니다. |