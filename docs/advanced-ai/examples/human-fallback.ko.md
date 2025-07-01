---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
contentType: howto
title: AI 워크플로우에 대한 인간 대체 설정
description: AI가 도움을 줄 수 없을 때 인간의 답변을 트리거하는 워크플로우를 만듭니다.
---

# AI 워크플로우에 대한 인간 대체 설정

이것은 표준 GPT-4 모델을 사용하여 사용자 쿼리에 답변하려고 시도하는 워크플로우입니다. 답변할 수 없는 경우 Slack으로 메시지를 보내 사람의 도움을 요청합니다. 사용자에게 이메일 주소를 제공하라는 메시지를 표시합니다.

이 워크플로우는 [채팅 트리거](/integrations/builtin/core-nodes/n8n-nodes-langchain.chattrigger/index.md)를 사용하여 채팅 인터페이스를 제공하고 [n8n 워크플로우 호출 도구](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.toolworkflow.md)를 사용하여 이메일 주소를 확인하고 Slack 메시지를 보내는 두 번째 워크플로우를 호출합니다.

[[ workflowDemo("file:///advanced-ai/examples/ask_a_human.json") ]]

## 주요 기능

이 워크플로우는 다음을 사용합니다.

* [채팅 트리거](/integrations/builtin/core-nodes/n8n-nodes-langchain.chattrigger/index.md): 워크플로우를 시작하고 사용자 채팅 상호 작용에 응답합니다. 이 노드는 사용자 지정 가능한 채팅 인터페이스를 제공합니다.
* [에이전트](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.agent/index.md): AI 워크플로우의 핵심 부분입니다. 에이전트는 워크플로우의 다른 구성 요소와 상호 작용하고 사용할 도구를 결정합니다.
* [n8n 워크플로우 호출 도구](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.toolworkflow.md): n8n 워크플로우를 사용자 지정 도구로 연결합니다. AI에서 도구는 AI가 세상과 상호 작용하는 데 사용할 수 있는 인터페이스입니다(이 경우 워크플로우에서 제공하는 데이터). AI 모델이 내장된 데이터 세트를 넘어서는 정보에 액세스할 수 있도록 합니다.

## 예제 사용

--8<-- "_snippets/examples-color-key.md"
