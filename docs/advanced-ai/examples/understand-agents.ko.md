---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: AI에서 에이전트란 무엇인가요?
description: AI의 맥락에서 에이전트를 이해합니다. n8n이 에이전트를 제공하는 방법을 알아보세요.
contentType: explanation
---

# AI에서 에이전트란 무엇인가요?

[에이전트](/glossary.md#ai-agent)를 생각하는 한 가지 방법은 결정을 내리는 방법을 아는 [체인](/advanced-ai/examples/understand-chains.md)입니다. 체인이 다른 AI 구성 요소에 대한 미리 정해진 호출 순서를 따르는 반면, 에이전트는 언어 모델을 사용하여 수행할 작업을 결정합니다.

에이전트는 의사 결정자 역할을 하는 AI의 일부입니다. 다른 에이전트 및 [도구](/glossary.md#ai-tool)와 상호 작용할 수 있습니다. 에이전트에 쿼리를 보내면 답변하는 데 사용할 최상의 도구를 선택하려고 시도합니다. 에이전트는 특정 쿼리와 동작을 구성하는 프롬프트에 적응합니다.

## n8n의 에이전트

n8n은 선택한 설정에 따라 다른 유형의 에이전트로 작동할 수 있는 하나의 에이전트 노드를 제공합니다. 사용 가능한 에이전트 유형에 대한 자세한 내용은 [에이전트 노드 설명서](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.agent/index.md)를 참조하세요.

에이전트가 포함된 워크플로우를 실행하면 에이전트가 여러 번 실행됩니다. 예를 들어 초기 설정을 수행한 다음 도구를 호출하기 위해 실행하고, 그런 다음 도구 응답을 평가하고 사용자에게 응답하기 위해 또 다른 실행을 수행할 수 있습니다.
