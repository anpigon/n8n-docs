#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
contentType: howto
description: 다른 워크플로우에서 워크플로우를 호출하고 큰 워크플로우를 더 작은 구성 요소로 분할합니다.
---

# 하위 워크플로우

한 워크플로우에서 다른 워크플로우를 호출할 수 있습니다. 이를 통해 모듈식 마이크로서비스와 같은 워크플로우를 구축할 수 있습니다. 또한 워크플로우가 [메모리 문제](/hosting/scaling/memory-errors.md)를 겪을 만큼 커지는 경우에도 도움이 될 수 있습니다. 하위 워크플로우를 만들려면 [워크플로우 실행](/integrations/builtin/core-nodes/n8n-nodes-base.executeworkflow.md) 및 [하위 워크플로우 실행 트리거](/integrations/builtin/core-nodes/n8n-nodes-base.executeworkflowtrigger.md) 노드를 사용합니다.

하위 워크플로우 실행은 플랜의 월간 실행 또는 활성 워크플로우 한도에 포함되지 않습니다.

## 하위 워크플로우 설정 및 사용

이 섹션에서는 상위 워크플로우와 하위 워크플로우를 모두 설정하는 과정을 안내합니다.

--8<-- "_snippets/flow-logic/subworkflow-usage.md"

## 워크플로우 간 데이터 전달 방식

--8<-- "_snippets/flow-logic/subworkflow-data-flow.md"

## 하위 워크플로우 변환

기존 워크플로우를 하위 워크플로우로 나누는 방법은 [하위 워크플로우 변환](/workflows/subworkflow-conversion.md)을 참조하십시오.