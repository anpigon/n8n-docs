#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
contentType: howto
description: 실행 오류 처리 방법.
---

# 오류 처리

흐름 로직을 설계할 때 잠재적인 오류를 고려하고 이를 정상적으로 처리하는 방법을 설정하는 것이 좋습니다. 오류 워크플로우를 사용하면 n8n이 워크플로우 실행 실패에 응답하는 방식을 제어할 수 있습니다.

/// note | 오류 조사
실패한 실행을 조사하려면 다음을 수행할 수 있습니다.

* [단일 워크플로우](/workflows/executions/single-workflow-executions.md) 또는 [액세스 권한이 있는 모든 워크플로우](/workflows/executions/all-executions.md)에 대한 [실행](/workflows/executions/index.md)을 검토합니다. [이전 실행에서 데이터 로드](/workflows/executions/debug.md)를 현재 워크플로우로 가져올 수 있습니다.
* [로그 스트리밍](/log-streaming.md)을 활성화합니다.
///

## 오류 워크플로우 생성 및 설정

각 워크플로우에 대해 **워크플로우 설정**에서 오류 워크플로우를 설정할 수 있습니다. 실행이 실패하면 실행됩니다. 즉, 예를 들어 워크플로우 실행 오류 시 이메일 또는 Slack 알림을 보낼 수 있습니다. 오류 워크플로우는 [오류 트리거](/integrations/builtin/core-nodes/n8n-nodes-base.errortrigger.md)로 시작해야 합니다.

여러 워크플로우에 동일한 오류 워크플로우를 사용할 수 있습니다.

--8<-- "_snippets/flow-logic/create-set-error-workflow.md"

## 오류 데이터

--8<-- "_snippets/integrations/builtin/core-nodes/error-trigger/error-data.md"

## 중지 및 오류를 사용하여 워크플로우 실행 실패 유발

오류 워크플로우를 생성하고 설정하면 실행이 실패할 때 n8n이 실행합니다. 일반적으로 이는 노드 설정 오류 또는 워크플로우 메모리 부족과 같은 문제 때문입니다.

[중지 및 오류](/integrations/builtin/core-nodes/n8n-nodes-base.stopanderror.md) 노드를 워크플로우에 추가하여 선택한 상황에서 실행이 강제로 실패하도록 하고 오류 워크플로우를 트리거할 수 있습니다.