#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 흐름 로직
description: n8n 워크플로우에서 로직을 표현하는 방법입니다.
contentType: overview
---

# 흐름 로직

n8n을 사용하면 워크플로우에서 복잡한 로직을 표현할 수 있습니다.

[[% import "_macros/section-toc.html" as sectionToc %]]

이 섹션에서는 다음을 다룹니다.

[[ sectionToc.sectionToc(page) ]]

## 관련 섹션

[데이터 구조](/data/data-structure.md) 및 [노드 내 데이터 흐름](/data/data-flow-nodes.md)을 포함하여 n8n의 [데이터](/data/index.md)에 대한 약간의 이해가 필요합니다.

로직을 구축할 때 다음을 포함한 n8n의 [코어 노드](/integrations/builtin/core-nodes/index.md)를 사용하게 됩니다.

* 분할: [IF](/integrations/builtin/core-nodes/n8n-nodes-base.if.md) 및 [Switch](/integrations/builtin/core-nodes/n8n-nodes-base.switch.md).
* 병합: [Merge](/integrations/builtin/core-nodes/n8n-nodes-base.merge.md), [Compare Datasets](/integrations/builtin/core-nodes/n8n-nodes-base.comparedatasets.md) 및 [Code](/integrations/builtin/core-nodes/n8n-nodes-base.code/index.md).
* 반복: [IF](/integrations/builtin/core-nodes/n8n-nodes-base.if.md) 및 [Loop Over Items](/integrations/builtin/core-nodes/n8n-nodes-base.splitinbatches.md).
* 대기: [Wait](/integrations/builtin/core-nodes/n8n-nodes-base.wait.md).
* 하위 워크플로우 생성: [Execute Workflow](/integrations/builtin/core-nodes/n8n-nodes-base.executeworkflow.md) 및 [Execute Workflow Trigger](/integrations/builtin/core-nodes/n8n-nodes-base.executeworkflowtrigger.md).
* 오류 처리: [Stop And Error](/integrations/builtin/core-nodes/n8n-nodes-base.stopanderror.md) 및 [Error Trigger](/integrations/builtin/core-nodes/n8n-nodes-base.errortrigger.md).