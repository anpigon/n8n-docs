---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: AI에서 체인이란 무엇인가요?
description: AI의 맥락에서 체인을 이해합니다. n8n의 체인에 대해 알아보세요.
contentType: explanation
---

# AI에서 체인이란 무엇인가요?

[체인](/glossary.md#ai-chain)은 AI의 다양한 구성 요소를 모아 응집력 있는 시스템을 만듭니다. 구성 요소 간의 호출 순서를 설정합니다. 이러한 구성 요소에는 모델과 [메모리](/glossary.md#ai-memory)가 포함될 수 있습니다(단, n8n에서는 체인이 메모리를 사용할 수 없다는 점에 유의하세요).


## n8n의 체인

n8n은 세 가지 체인 노드를 제공합니다.

* [기본 LLM 체인](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.chainllm.md): 추가 구성 요소 없이 LLM과 상호 작용하는 데 사용합니다.
* [질의응답 체인](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.chainretrievalqa/index.md): 리트리버를 사용하여 [벡터 저장소](/glossary.md#ai-vector-store)에 연결하거나 워크플로우 리트리버 노드를 사용하여 n8n 워크플로우에 연결할 수 있습니다. 특정 문서에 대한 질문을 지원하는 워크플로우를 만들려면 이 노드를 사용하세요.
* [요약 체인](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.chainsummarization.md): 입력을 받아 요약을 반환합니다.

n8n과 LangChain과 같은 다른 도구의 체인 사이에는 중요한 차이점이 있습니다. 체인 노드 중 어느 것도 메모리를 지원하지 않습니다. 즉, 이전 사용자 쿼리를 기억할 수 없습니다. LangChain을 사용하여 AI 애플리케이션을 코딩하는 경우 애플리케이션에 메모리를 제공할 수 있습니다. n8n에서 워크플로우가 메모리를 지원해야 하는 경우 에이전트를 사용하세요. 사용자가 앱과 자연스러운 대화를 계속할 수 있도록 하려면 이것이 필수적입니다.
