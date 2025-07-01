---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
contentType: explanation
title: 에이전트 대 체인
description: 에이전트와 체인 간의 주요 차이점을 보여주는 워크플로우 예제입니다.
---

# 에이전트와 체인 간의 주요 차이점 시연

이 워크플로우에서는 채팅 쿼리가 [에이전트](/glossary.md#ai-agent) 또는 [체인](/glossary.md#ai-chain)으로 이동할지 선택할 수 있습니다. 에이전트가 체인보다 더 강력한 몇 가지 방법을 보여줍니다.

[[ workflowDemo("file:///advanced-ai/examples/agents_vs_chains.json") ]]

## 주요 기능

이 워크플로우는 다음을 사용합니다.

* [채팅 트리거](/integrations/builtin/core-nodes/n8n-nodes-langchain.chattrigger/index.md): 워크플로우를 시작하고 사용자 채팅 상호 작용에 응답합니다. 이 노드는 사용자 지정 가능한 채팅 인터페이스를 제공합니다.
* [스위치 노드](/integrations/builtin/core-nodes/n8n-nodes-base.switch.md): 쿼리에서 지정한 내용에 따라 쿼리를 에이전트 또는 체인으로 보냅니다. "agent"라고 말하면 에이전트로 보내고 "chain"이라고 말하면 체인으로 보냅니다.
* [에이전트](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.agent/index.md): 에이전트 노드는 워크플로우의 다른 구성 요소와 상호 작용하고 사용할 [도구](/glossary.md#ai-tool)에 대한 결정을 내립니다.
* [기본 LLM 체인](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.chainllm.md): 기본 LLM 체인 노드는 연결된 LLM과의 채팅을 지원하지만 [메모리](/glossary.md#ai-memory)나 도구는 지원하지 않습니다.


## 예제 사용

--8<-- "_snippets/examples-color-key.md"
