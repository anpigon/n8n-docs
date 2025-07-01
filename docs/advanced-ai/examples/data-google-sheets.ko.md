---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
contentType: howto
title: AI를 사용하여 Google Sheet과 채팅하기
description: n8n 워크플로우 도구를 사용하여 Google Sheets에서 AI 워크플로우로 데이터를 로드합니다.
---

# AI를 사용하여 Google Sheet과 채팅하기

n8n을 사용하여 자체 데이터를 AI로 가져옵니다. 이 워크플로우는 [채팅 트리거](/integrations/builtin/core-nodes/n8n-nodes-langchain.chattrigger/index.md)를 사용하여 채팅 인터페이스를 제공하고 [n8n 워크플로우 호출 도구](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.toolworkflow.md)를 사용하여 Google Sheets를 쿼리하는 두 번째 워크플로우를 호출합니다.

[[ workflowDemo("file:///advanced-ai/examples/chat_with_google_sheets_docs_version.json") ]]

## 주요 기능

이 워크플로우는 다음을 사용합니다.

* [채팅 트리거](/integrations/builtin/core-nodes/n8n-nodes-langchain.chattrigger/index.md): 워크플로우를 시작하고 사용자 채팅 상호 작용에 응답합니다. 이 노드는 사용자 지정 가능한 채팅 인터페이스를 제공합니다.
* [에이전트](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.agent/index.md): AI 워크플로우의 핵심 부분입니다. 에이전트는 워크플로우의 다른 구성 요소와 상호 작용하고 사용할 도구를 결정합니다.
* [n8n 워크플로우 호출 도구](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.toolworkflow.md): n8n 워크플로우를 사용자 지정 도구로 연결합니다. AI에서 도구는 AI가 세상과 상호 작용하는 데 사용할 수 있는 인터페이스입니다(이 경우 워크플로우에서 제공하는 데이터). AI 모델은 도구를 사용하여 내장된 데이터 세트를 넘어서는 정보에 액세스합니다.


## 예제 사용

--8<-- "_snippets/examples-color-key.md"
