#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
contentType: howto
---

# n8n에서 반복하기

반복은 여러 항목을 처리하거나 주소록의 모든 연락처에 메시지를 보내는 것과 같이 작업을 반복적으로 수행하려는 경우에 유용합니다. n8n은 이 반복적인 처리를 자동으로 처리하므로 워크플로우에 루프를 특별히 빌드할 필요가 없습니다. 이것이 사실이 아닌 [일부 노드](#node-exceptions)가 있습니다.

## n8n에서 루프 사용하기

n8n 노드는 입력으로 임의의 수의 항목을 가져와 이러한 항목을 처리하고 결과를 출력합니다. 각 항목을 단일 데이터 포인트 또는 노드의 출력 테이블에 있는 단일 행으로 생각할 수 있습니다.

![고객 데이터 저장소 노드 출력](/_images/flow-logic/looping/customer_datastore_node.png)

노드는 일반적으로 각 항목에 대해 한 번 실행됩니다. 예를 들어 고객 데이터 저장소 노드에 있는 고객의 이름과 메모를 Slack에 메시지로 보내려면 다음을 수행합니다.

1. Slack 노드를 고객 데이터 저장소 노드에 연결합니다.
2. 매개변수를 구성합니다.
3. 노드를 실행합니다.

각 항목에 대해 하나씩 다섯 개의 메시지를 받게 됩니다.

이것이 노드를 루프로 명시적으로 연결하지 않고도 여러 항목을 처리할 수 있는 방법입니다.

### 노드 한 번 실행하기

수신된 모든 항목을 노드에서 처리하지 않으려는 경우(예: 첫 번째 고객에게만 Slack 메시지 보내기) 해당 노드의 **설정** 탭에서 **한 번 실행** 매개변수를 토글하여 수행할 수 있습니다. 이 설정은 들어오는 데이터에 여러 항목이 포함되어 있고 첫 번째 항목만 처리하려는 경우에 유용합니다.


## 루프 만들기

n8n은 일반적으로 들어오는 모든 항목에 대한 반복을 처리합니다. 그러나 모든 항목을 반복하기 위해 루프를 만들어야 하는 특정 시나리오가 있습니다. 모든 들어오는 항목을 자동으로 반복하지 않는 노드 목록은 [노드 예외](#node-exceptions)를 참조하십시오.

### 조건이 충족될 때까지 반복

n8n 워크플로우에서 루프를 만들려면 한 노드의 출력을 이전 노드의 입력에 연결합니다. 루프를 중지할 시기를 확인하기 위해 [IF](/integrations/builtin/core-nodes/n8n-nodes-base.if.md) 노드를 추가합니다.

다음은 `IF` 노드로 루프를 구현하는 [예제 워크플로우](https://n8n.io/workflows/1130)입니다.

![샘플 워크플로우의 편집기 UI 보기](/_images/flow-logic/looping/example_workflow.png)

### 모든 항목이 처리될 때까지 반복

모든 항목이 처리될 때까지 반복하려면 [항목 반복](/integrations/builtin/core-nodes/n8n-nodes-base.splitinbatches.md) 노드를 사용합니다. 각 항목을 개별적으로 처리하려면 **배치 크기**를 `1`로 설정합니다.

데이터를 그룹으로 묶어 이러한 배치를 처리할 수 있습니다. 이 접근 방식은 대량의 들어오는 데이터를 처리할 때 API 속도 제한을 피하거나 반환된 항목의 특정 그룹을 처리하려는 경우에 유용합니다.

항목 반복 노드는 들어오는 모든 항목이 배치로 나뉘어 워크플로우의 다음 노드로 전달된 후 실행을 중지하므로 루프를 중지하기 위해 IF 노드를 추가할 필요가 없습니다.

## 노드 예외

워크플로우에 루프를 설계해야 하는 노드 및 작업:

* [CrateDB](/integrations/builtin/app-nodes/n8n-nodes-base.cratedb.md)는 `insert` 및 `update`에 대해 한 번 실행됩니다.
* **모든 항목에 대해 한 번 실행** 모드의 [코드](/integrations/builtin/core-nodes/n8n-nodes-base.code/index.md) 노드: 입력된 코드 조각을 기반으로 모든 항목을 처리합니다.
* **모든 항목에 대해 한 번 실행** 모드의 [워크플로우 실행](/integrations/builtin/core-nodes/n8n-nodes-base.executeworkflow.md) 노드.
* [HTTP 요청](/integrations/builtin/core-nodes/n8n-nodes-base.httprequest/index.md): 페이지 매김을 직접 처리해야 합니다. API 호출이 페이지 매김된 결과를 반환하는 경우 한 번에 한 페이지씩 가져오기 위해 루프를 만들어야 합니다.
* [Microsoft SQL](/integrations/builtin/app-nodes/n8n-nodes-base.microsoftsql.md)은 `insert`, `update` 및 `delete`에 대해 한 번 실행됩니다.
* [MongoDB](/integrations/builtin/app-nodes/n8n-nodes-base.mongodb.md)는 `insert` 및 `update`에 대해 한 번 실행됩니다.
* [QuestDB](/integrations/builtin/app-nodes/n8n-nodes-base.questdb.md)는 `insert`에 대해 한 번 실행됩니다.
* [Redis](/integrations/builtin/app-nodes/n8n-nodes-base.redis.md):
	* 정보: 이 작업은 들어오는 데이터의 항목 수에 관계없이 한 번만 실행됩니다.
* [RSS 읽기](/integrations/builtin/core-nodes/n8n-nodes-base.rssfeedread.md)는 요청된 URL에 대해 한 번 실행됩니다.
* [TimescaleDB](/integrations/builtin/app-nodes/n8n-nodes-base.timescaledb.md)는 `insert` 및 `update`에 대해 한 번 실행됩니다.