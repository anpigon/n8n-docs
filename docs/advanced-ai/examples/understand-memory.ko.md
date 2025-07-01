---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: AI에서 메모리란 무엇인가요?
description: AI의 맥락에서 메모리를 이해합니다. n8n에서 메모리의 특별한 점에 대해 알아보세요.
contentType: explanation
---

# AI에서 메모리란 무엇인가요?

메모리는 AI 채팅 서비스의 핵심 부분입니다. [메모리](/glossary.md#ai-memory)는 이전 메시지의 기록을 유지하여 모든 상호 작용이 새로 시작되는 대신 AI와 지속적인 대화를 가능하게 합니다.

## n8n의 AI 메모리

AI 워크플로우에 메모리를 추가하려면 다음 중 하나를 사용할 수 있습니다.

* [단순 메모리](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.memorybufferwindow/index.md): 현재 세션에 대한 사용자 지정 가능한 길이의 채팅 기록을 저장합니다. 이것이 가장 쉽게 시작할 수 있는 방법입니다.
* n8n이 노드를 제공하는 메모리 서비스 중 하나. 여기에는 다음이 포함됩니다.
	* [Motorhead](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.memorymotorhead.md)
	* [Redis 채팅 메모리](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.memoryredischat.md)
	* [Postgres 채팅 메모리](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.memorypostgreschat.md) 
	* [Xata](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.memoryxata.md)
	* [Zep](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.memoryzep.md)

워크플로우에서 고급 AI 메모리 관리를 수행해야 하는 경우 [채팅 메모리 관리자](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.memorymanager.md) 노드를 사용하세요.

--8<-- "_snippets/integrations/builtin/cluster-nodes/langchain-sub-nodes/chat-memory-manager-purpose.md"
