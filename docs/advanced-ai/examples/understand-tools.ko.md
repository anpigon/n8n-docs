---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: AI에서 도구란 무엇인가요?
description: AI의 맥락에서 도구를 이해합니다. n8n에서 도구의 특별한 점에 대해 알아보세요.
contentType: explanation
---

# AI에서 도구란 무엇인가요?

AI에서 '도구'는 특별한 의미를 갖습니다. 도구는 AI가 추가 컨텍스트나 리소스에 액세스하는 데 사용할 수 있는 애드온처럼 작동합니다.

이를 표현하는 다른 몇 가지 방법은 다음과 같습니다.

> 도구는 에이전트가 세상과 상호 작용하는 데 사용할 수 있는 인터페이스입니다. ([출처](https://langchain-ai.github.io/langgraphjs/how-tos/tool-calling/){:target=_blank .external-link})

<!--  -->

> 우리는 이러한 도구를 AI 모델이 호출할 수 있는 함수와 거의 같다고 생각할 수 있습니다. ([출처](https://www.udemy.com/course/chatgpt-and-langchain-the-complete-developers-masterclass/){:target=_blank .external-link})

## n8n의 AI 도구

n8n은 [AI 에이전트](/glossary.md#ai-agent)에 연결할 수 있는 도구 [하위 노드](/glossary.md#sub-node-n8n)를 제공합니다. [Wikipedia](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.toolwikipedia.md) 및 [SerpAPI](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.toolserpapi.md)와 같은 일부 인기 있는 도구를 제공하는 것 외에도 n8n은 특히 강력한 세 가지 도구를 제공합니다.

* [n8n 워크플로우 도구 호출](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.toolworkflow.md): 이를 사용하여 모든 n8n 워크플로우를 도구로 로드합니다.
* [사용자 지정 코드 도구](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.toolcode.md): 에이전트가 실행할 수 있는 코드를 작성합니다.
* [HTTP 요청 도구](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.toolhttprequest.md): 웹사이트나 API의 데이터를 가져오기 위해 호출합니다.

다음 세 가지 예는 n8n 워크플로우 도구 호출을 강조합니다.

- [Google Sheets와 채팅](/advanced-ai/examples/data-google-sheets.md)
- [API를 호출하여 데이터 가져오기](/advanced-ai/examples/api-workflow-tool.md)
- [인간 대체 설정](/advanced-ai/examples/human-fallback.md)

또한 [`$fromAI()` 함수를 사용하여 AI가 도구에 대한 매개변수를 동적으로 지정하도록 하는 방법](/advanced-ai/examples/using-the-fromai-function.md)을 배울 수 있습니다.
