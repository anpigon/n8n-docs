#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
description: If 및 Switch를 사용하여 워크플로우를 여러 경로로 분할
contentType: howto
---

# 조건부 노드로 워크플로우 분할

분할은 [IF](/integrations/builtin/core-nodes/n8n-nodes-base.if.md) 또는 [Switch](/integrations/builtin/core-nodes/n8n-nodes-base.switch.md) 노드를 사용합니다. 단일 분기 워크플로우를 다중 분기 워크플로우로 바꿉니다. 이것은 n8n에서 복잡한 논리를 나타내는 핵심 부분입니다.

이러한 워크플로우를 비교하십시오.

!["두 워크플로우를 나타내는 다이어그램. 하나는 세 단계가 있고 선형 프로세스를 따르며 사용자가 버그를 제출하고 워크플로우가 지원팀에 이메일을 보냅니다. 두 번째 워크플로우는 동일한 방식으로 시작하지만 사용자가 문제를 긴급으로 표시했는지 여부에 따라 분할됩니다. 그런 다음 사용자의 지원 계획에 따라 다시 분할됩니다."](/_images/flow-logic/splitting/single-multi-branch-workflow.png)

n8n에서 분할 및 조건부 노드의 힘입니다.

사용 세부 정보는 [IF](/integrations/builtin/core-nodes/n8n-nodes-base.if.md) 또는 [Switch](/integrations/builtin/core-nodes/n8n-nodes-base.switch.md) 설명서를 참조하십시오.