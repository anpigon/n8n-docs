---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: n8n 고급 AI 설명서 및 가이드
description: n8n의 LangChain 통합을 사용하여 워크플로우 내에서 AI 기반 기능을 구축합니다. LangChain 기능을 다른 데이터 소스 및 서비스에 연결합니다.
contentType: overview
---

# 고급 AI

자신만의 챗봇을 만드는 것부터 AI를 사용하여 다른 소스의 문서와 데이터를 처리하는 것까지 n8n을 사용하여 AI 기능을 구축하세요.

/// info | 기능 가용성
이 기능은 버전 1.19.4 이상에서 클라우드 및 자체 호스팅 n8n에서 사용할 수 있습니다.
///

<div class="grid cards" markdown>

-   __시작하기__

    짧은 튜토리얼을 통해 n8n에서 AI 워크플로우를 구축하는 기본 사항을 알아보세요.

    [:octicons-arrow-right-24: 튜토리얼](/advanced-ai/intro-tutorial.md)

-   __스타터 키트 사용__

    n8n의 자체 호스팅 AI 스타터 키트를 사용하여 AI 워크플로우를 빠르게 구축해 보세요.

    [:octicons-arrow-right-24: 자체 호스팅 AI 스타터 키트](/hosting/starter-kits/ai-starter-kit.md)

-   __예제 및 개념 탐색__

	구축에 도움이 되는 예제 및 워크플로우 템플릿을 찾아보세요. 중요한 AI 개념에 대한 설명이 포함되어 있습니다.

    [:octicons-arrow-right-24: 예제](/advanced-ai/examples/introduction.md)

-   __n8n이 LangChain을 사용하는 방법__

    n8n이 LangChain을 기반으로 구축되는 방법에 대해 자세히 알아보세요.

    [:octicons-arrow-right-24: n8n의 LangChain](/advanced-ai/langchain/overview.md)

-   __AI 템플릿 찾아보기__

    n8n 웹사이트에서 다양한 AI 워크플로우 템플릿을 살펴보세요.

    [:octicons-arrow-right-24: n8n.io의 AI 워크플로우](https://n8n.io/workflows/?categories=25){:target=_blank .external-link}

</div>

## 관련 리소스

관련 설명서 및 도구.

### 노드 유형

이 기능은 함께 작동하는 [루트](/integrations/builtin/cluster-nodes/root-nodes/index.md) 및 [하위](/integrations/builtin/cluster-nodes/sub-nodes/index.md) 노드 그룹인 [클러스터 노드](/integrations/builtin/cluster-nodes/index.md)를 사용합니다.

--8<-- "_snippets/integrations/builtin/cluster-nodes/cluster-nodes-summary.md"

### 워크플로우 템플릿

앱 내 또는 n8n 웹사이트 [워크플로우](https://n8n.io/workflows/?categories=25,26){:target=_blank .external-link} 페이지에서 [워크플로우 템플릿](/glossary.md#template-n8n)을 찾아볼 수 있습니다.

앱 내에서 템플릿에 액세스하는 방법에 대한 정보는 [템플릿](/workflows/templates.md)을 참조하세요.

### 채팅 트리거

[n8n 채팅 트리거](/integrations/builtin/core-nodes/n8n-nodes-langchain.chattrigger/index.md)를 사용하여 채팅 상호 작용을 기반으로 워크플로우를 트리거합니다.

### 챗봇 위젯

n8n은 AI 기반 채팅 워크플로우의 프런트엔드로 사용할 수 있는 챗봇 위젯을 제공합니다. 사용 정보는 [@n8n/chat npm 페이지](https://www.npmjs.com/package/@n8n/chat){:target=_blank .external-link}를 참조하세요.
