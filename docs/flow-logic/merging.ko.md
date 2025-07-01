---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
contentType: howto
description: n8n 워크플로우에서 데이터 스트림을 병합합니다.
---

# 데이터 병합

병합은 여러 데이터 스트림을 하나로 모읍니다. 워크플로우 요구 사항에 따라 다른 노드를 사용하여 이를 달성할 수 있습니다.

- 다른 데이터 스트림 또는 노드의 데이터 병합: [병합](/integrations/builtin/core-nodes/n8n-nodes-base.merge.md) 노드를 사용하여 다양한 소스의 데이터를 하나로 결합합니다.
- 여러 노드 실행의 데이터 병합: 노드 또는 여러 노드의 여러 실행에서 데이터를 병합해야 하는 복잡한 시나리오에는 [코드](/integrations/builtin/core-nodes/n8n-nodes-base.code/index.md) 노드를 사용합니다.
- 데이터 비교 및 병합: [데이터 세트 비교](/integrations/builtin/core-nodes/n8n-nodes-base.comparedatasets.md) 노드를 사용하여 비교를 기반으로 데이터 스트림을 비교, 병합 및 출력합니다.

아래 섹션에서 각 방법을 자세히 살펴보십시오.

## 다른 데이터 스트림의 데이터 병합

워크플로우가 [분할](/flow-logic/splitting.md)되면 별도의 스트림을 다시 하나의 스트림으로 결합합니다.

다음은 데이터 세트 추가, 새 항목만 유지, 기존 항목만 유지 등 다양한 유형의 병합을 보여주는 [예제 워크플로우](https://n8n.io/workflows/1747-joining-different-datasets/)입니다. [병합 노드](/integrations/builtin/core-nodes/n8n-nodes-base.merge.md) 설명서에는 각 병합 작업에 대한 세부 정보가 포함되어 있습니다.

[[ workflowDemo("https://api.n8n.io/workflows/templates/1747") ]]

## 다른 노드의 데이터 병합

워크플로우가 별도의 데이터 스트림으로 분할되지 않은 경우에도 병합 노드를 사용하여 이전 두 노드의 데이터를 결합할 수 있습니다. 이는 여러 노드에서 생성된 데이터에서 단일 데이터 세트를 생성하려는 경우에 유용할 수 있습니다.

<figure markdown="span">
![이전 두 노드의 데이터 병합. 다이어그램은 순차적으로 정렬된 세 개의 노드를 보여줍니다. 첫 번째 노드는 데이터 가져오기, 두 번째 노드는 데이터 수정, 세 번째 노드는 병합: 두 데이터 세트 모두 추가로 레이블이 지정되어 있습니다. 화살표는 노드 1에서 2, 2에서 3, 1에서 3으로 연결됩니다.](/_images/flow-logic/merging/merge-node-data.png)
<figcaption>이전 두 노드의 데이터 병합</figcaption>
</figure>

## 여러 노드 실행의 데이터 병합

코드 노드를 사용하여 여러 노드 실행의 데이터를 병합합니다. 이는 일부 [반복](/flow-logic/looping.md) 시나리오에서 유용합니다.

/// note | 노드 실행 및 워크플로우 실행
이 섹션에서는 여러 노드 실행의 데이터를 병합하는 방법을 설명합니다. 이는 단일 워크플로우 실행 중에 노드가 여러 번 실행될 때입니다.
///
항목 반복 및 대기를 사용하여 인위적으로 여러 실행을 생성하는 이 [예제 워크플로우](https://n8n.io/workflows/1814-merge-multiple-runs-into-one/){:target=_blank .external-link}를 참조하십시오.

[[ workflowDemo("https://api.n8n.io/workflows/templates/1814") ]]

## 비교, 병합 및 다시 분할

[데이터 세트 비교](/integrations/builtin/core-nodes/n8n-nodes-base.comparedatasets.md) 노드는 병합하기 전에 데이터 스트림을 비교합니다. 최대 4개의 다른 데이터 스트림을 출력합니다.

예제는 이 [예제 워크플로우](https://n8n.io/workflows/1943-comparing-data-with-the-compare-datasets-node/){:target=_blank .external-link}를 참조하십시오.

[[ workflowDemo("https://api.n8n.io/workflows/templates/1943") ]]
