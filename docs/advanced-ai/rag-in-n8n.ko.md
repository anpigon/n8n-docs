---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: n8n의 RAG
description: 검색 증강 생성(RAG)을 사용하면 모델이 컨텍스트별 리소스에 액세스하여 관련 답변을 생성하는 데 도움을 줄 수 있습니다. n8n에서 RAG가 어떻게 작동하고 사용하는지 알아보세요.
contentType: overview
---

<!-- vale from-microsoft.Contractions = NO -->
<!-- vale from-microsoft.HeadingPunctuation = NO -->

# n8n의 RAG

## RAG란 무엇인가

[검색 증강 생성(RAG)](/glossary.md#ai-retrieval-augmented-generation-rag)은 언어 모델을 외부 데이터 소스와 결합하여 AI 응답을 개선하는 기술입니다. RAG 시스템은 모델의 내부 학습 데이터에만 의존하는 대신 관련 문서를 검색하여 최신, 도메인별 또는 독점적인 지식에 응답을 [기반](/glossary.md#ai-groundedness)으로 합니다. RAG 워크플로우는 일반적으로 벡터 저장소를 사용하여 이 외부 데이터를 효율적으로 관리하고 검색합니다.

## 벡터 저장소란 무엇인가?

[벡터 저장소](/glossary.md#ai-vector-store)는 텍스트, 이미지 또는 기타 데이터의 숫자 표현인 고차원 벡터를 저장하고 검색하도록 설계된 특수 데이터베이스입니다. 문서를 업로드하면 벡터 저장소는 문서를 청크로 분할하고 [임베딩 모델](/glossary.md#ai-embedding)을 사용하여 각 청크를 벡터로 변환합니다.

키워드 일치가 아닌 *의미적 의미*를 기반으로 결과를 구성하는 유사성 검색을 사용하여 이러한 벡터를 쿼리할 수 있습니다. 이로 인해 벡터 저장소는 대규모 지식 집합을 검색하고 추론해야 하는 RAG 및 기타 AI 시스템의 강력한 기반이 됩니다.

## n8n에서 RAG를 사용하는 방법

/// note | RAG 템플릿으로 시작
👉 [RAG 스타터 템플릿](https://n8n.io/workflows/5010-rag-starter-template-using-simple-vector-stores-form-trigger-and-openai)으로 n8n에서 RAG를 사용해 보세요. 템플릿에는 파일 업로드용과 쿼리용의 두 가지 기성 워크플로우가 포함되어 있습니다.
///

### 벡터 저장소에 데이터 삽입

에이전트가 사용자 지정 지식에 액세스하기 전에 해당 데이터를 벡터 저장소에 업로드해야 합니다.

1. 소스 데이터를 가져오는 데 필요한 노드를 추가합니다.
2. **벡터 저장소** 노드(예: [단순 벡터 저장소](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.vectorstoreinmemory.md))를 삽입하고 **문서 삽입** 작업을 선택합니다.
3. 텍스트를 벡터 임베딩으로 변환하는 **임베딩 모델**을 선택합니다. [올바른 임베딩 모델 선택](#how-do-i-choose-the-right-embedding-model)에 대한 자세한 내용은 FAQ를 참조하세요.
4. 콘텐츠를 청크로 분할하는 [기본 데이터 로더](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.documentdefaultdataloader.md) 노드를 추가합니다. 기본 설정을 사용하거나 자신만의 청크 전략을 정의할 수 있습니다.
	* **문자 텍스트 분할기:** 문자 길이로 분할합니다.
	* **재귀 문자 텍스트 분할기:** 마크다운, HTML, 코드 블록 또는 단순 문자로 재귀적으로 분할합니다(대부분의 사용 사례에 권장).
	* **토큰 텍스트 분할기:** 토큰 수로 분할합니다.
5. (선택 사항) 각 청크에 **메타데이터**를 추가하여 컨텍스트를 풍부하게 하고 나중에 더 나은 필터링을 허용합니다.

### 데이터 쿼리

에이전트를 사용하거나 노드를 통해 직접 두 가지 주요 방법으로 데이터를 쿼리할 수 있습니다.

### 에이전트 사용

1. 워크플로우에 [에이전트](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.agent/index.md)를 추가합니다.
2. 벡터 저장소를 **도구**로 추가하고 에이전트가 언제 사용해야 하는지 이해하는 데 도움이 되도록 **설명**을 제공합니다.
	* 반환할 청크 수를 정의하려면 **제한**을 설정합니다.
	* 각 청크에 대한 추가 컨텍스트를 제공하려면 **메타데이터 포함**을 활성화합니다.
3. 데이터를 삽입할 때 사용한 것과 동일한 **임베딩 모델**을 추가합니다.

/// tip | 전문가 팁
비싼 모델에서 토큰을 절약하려면 먼저 [벡터 저장소 질문 답변 도구](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.toolvectorstore.md)를 사용하여 관련 데이터를 검색한 다음 결과를 에이전트에 전달할 수 있습니다. 이를 실제로 보려면 [이 템플릿](https://n8n.io/workflows/5011-save-costs-in-rag-workflows-using-the-qanda-tool-with-multiple-models)을 확인하세요.
///

### 노드를 직접 사용

1. 벡터 저장소 노드를 캔버스에 추가하고 **여러 개 가져오기** 작업을 선택합니다.
2. 쿼리 또는 프롬프트를 입력합니다.
	* 반환할 청크 수에 대한 **제한**을 설정합니다.
	* 필요한 경우 **메타데이터 포함**을 활성화합니다.

## FAQ

<!-- vale from-microsoft.FirstPerson = NO -->
### 올바른 임베딩 모델을 어떻게 선택하나요?
<!-- vale from-microsoft.FirstPerson = YES -->

올바른 임베딩 모델은 경우에 따라 다릅니다.

일반적으로 더 작은 모델(예: `text-embedding-ada-002`)은 더 빠르고 저렴하므로 짧고 범용적인 문서나 경량 RAG 워크플로우에 이상적입니다. 더 큰 모델(예: `text-embedding-3-large`)은 더 나은 의미 이해를 제공합니다. 긴 문서, 복잡한 주제 또는 정확성이 중요한 경우에 가장 좋습니다.

<!-- vale from-microsoft.FirstPerson = NO -->
### 내 사용 사례에 가장 적합한 텍스트 분할은 무엇인가요?
<!-- vale from-microsoft.FirstPerson = YES -->

이것은 다시 데이터에 따라 많이 다릅니다.

* 작은 청크(예: 200~500 토큰)는 세분화된 검색에 좋습니다.
* 큰 청크는 더 많은 컨텍스트를 전달할 수 있지만 희석되거나 노이즈가 발생할 수 있습니다.

AI가 청크의 컨텍스트를 이해하려면 올바른 겹침 크기를 사용하는 것이 중요합니다. 이것이 마크다운 또는 코드 블록 분할을 사용하면 종종 청크를 더 좋게 만드는 데 도움이 될 수 있는 이유이기도 합니다.

또 다른 좋은 접근 방식은 (예를 들어 청크가 나온 문서에 대해) 더 많은 컨텍스트를 추가하는 것입니다. 이에 대해 더 자세히 읽고 싶다면 [Anthropic의 이 훌륭한 기사](https://www.anthropic.com/news/contextual-retrieval)를 확인해 보세요.
