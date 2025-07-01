---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
contentType: explanation
title: n8n의 LangChain 개념
description: LangChain 개념이 n8n에 매핑되는 방식과 사용할 n8n 노드.
---

# n8n의 LangChain 개념

이 페이지에서는 LangChain 개념과 기능이 n8n 노드에 매핑되는 방식을 설명합니다.

이 페이지에는 n8n의 LangChain 중심 노드 목록이 포함되어 있습니다. LangChain과 상호 작용하는 워크플로우에서 모든 n8n 노드를 사용하여 LangChain을 다른 서비스에 연결할 수 있습니다. LangChain 기능은 n8n의 [클러스터 노드](/integrations/builtin/cluster-nodes/index.md)를 사용합니다.


/// note | n8n은 LangChain JS를 구현합니다
이 기능은 n8n의 [LangChain의 JavaScript 프레임워크](https://js.langchain.com/docs/get_started/introduction){:target=_blank .external-link} 구현입니다.
///
## 트리거 노드

[채팅 트리거](/integrations/builtin/core-nodes/n8n-nodes-langchain.chattrigger/index.md)

## 클러스터 노드

--8<-- "_snippets/integrations/builtin/cluster-nodes/cluster-nodes-summary.md"

### 루트 노드

각 클러스터는 하나의 [루트 노드](/glossary.md#root-node-n8n)로 시작합니다.

#### 체인

[체인](/glossary.md#ai-chain)은 단일 LLM만으로는 제공할 수 없는 기능을 지원하기 위해 함께 연결된 일련의 LLM 및 관련 도구입니다.

사용 가능한 노드:

* [기본 LLM 체인](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.chainllm.md)
* [검색 Q&A 체인](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.chainretrievalqa/index.md)
* [요약 체인](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.chainsummarization.md)
* [감성 분석](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.sentimentanalysis.md)
* [텍스트 분류기](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.text-classifier.md)

[LangChain의 체인](https://js.langchain.com/docs/concepts/lcel){:target=_blank .external-link}에 대해 자세히 알아보세요.

#### 에이전트

> [에이전트](/glossary.md#ai-agent){ data-preview}는 도구 모음에 액세스할 수 있으며 사용자 입력에 따라 사용할 도구를 결정합니다. 에이전트는 여러 도구를 사용할 수 있으며 한 도구의 출력을 다음 도구의 입력으로 사용할 수 있습니다. [출처](https://github.com/langchain-ai/langchainjs/blob/def3a26c054575e1ed40b9062087e8c0a8899633/docs/core_docs/docs/modules/agents/index.mdx){:target=_blank .external-link}

사용 가능한 노드:

* [에이전트](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.agent/index.md)

[LangChain의 에이전트](https://js.langchain.com/docs/concepts/agents){:target=_blank .external-link}에 대해 자세히 알아보세요.

#### 벡터 저장소

[벡터 저장소](/glossary.md#ai-vector-store)는 임베디드 데이터를 저장하고 벡터 검색을 수행합니다.

* [단순 벡터 저장소](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.vectorstoreinmemory.md)
* [PGVector 벡터 저장소](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.vectorstorepgvector.md)
* [Pinecone 벡터 저장소](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.vectorstorepinecone.md)
* [Qdrant 벡터 저장소](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.vectorstoreqdrant.md)
* [Supabase 벡터 저장소](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.vectorstoresupabase.md)
* [Zep 벡터 저장소](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.vectorstorezep.md)

[LangChain의 벡터 저장소](https://js.langchain.com/docs/concepts/vectorstores/){:target=_blank .external-link}에 대해 자세히 알아보세요.

#### 기타

유틸리티 노드.

[LangChain 코드](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.code.md): LangChain을 가져옵니다. 즉, n8n이 노드를 만들지 않은 필요한 기능이 있는 경우에도 사용할 수 있습니다.

### 하위 노드

각 루트 노드에는 하나 이상의 [하위 노드](/glossary.md#sub-node-n8n)가 연결될 수 있습니다.

#### 문서 로더

문서 로더는 데이터를 문서로 체인에 추가합니다. 데이터 소스는 파일 또는 웹 서비스일 수 있습니다.

사용 가능한 노드:

* [기본 문서 로더](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.documentdefaultdataloader.md)
* [GitHub 문서 로더](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.documentgithubloader.md)

[LangChain의 문서 로더](https://js.langchain.com/docs/concepts/document_loaders){:target=_blank .external-link}에 대해 자세히 알아보세요.

#### 언어 모델

[LLM(대규모 언어 모델)](/glossary.md#large-language-model-llm)은 데이터 세트를 분석하는 프로그램입니다. AI 작업의 핵심 요소입니다.

사용 가능한 노드:

* [Anthropic 채팅 모델](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.lmchatanthropic.md)
* [AWS Bedrock 채팅 모델](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.lmchatawsbedrock.md)
* [Cohere 모델](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.lmcohere.md)
* [Hugging Face 추론 모델](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.lmopenhuggingfaceinference.md)
* [Mistral 클라우드 채팅 모델](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.lmchatmistralcloud.md)
* [Ollama 채팅 모델](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.lmchatollama/index.md)
* [Ollama 모델](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.lmollama/index.md)
* [OpenAI 채팅 모델](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.lmchatopenai/index.md)

[LangChain의 언어 모델](https://js.langchain.com/docs/concepts/chat_models){:target=_blank .external-link}에 대해 자세히 알아보세요.

#### 메모리

[메모리](/glossary.md#ai-memory)는 일련의 쿼리에서 이전 쿼리에 대한 정보를 유지합니다. 예를 들어 사용자가 채팅 모델과 상호 작용할 때 애플리케이션이 사용자가 입력한 가장 최근 쿼리뿐만 아니라 전체 대화를 기억하고 호출할 수 있으면 유용합니다.

사용 가능한 노드:

* [Motorhead](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.memorymotorhead.md)
* [Redis 채팅 메모리](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.memoryredischat.md)
* [Postgres 채팅 메모리](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.memorypostgreschat.md) 
* [단순 메모리](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.memorybufferwindow/index.md)
* [Xata](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.memoryxata.md)
* [Zep](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.memoryzep.md)

[LangChain의 메모리](https://langchain-ai.github.io/langgraphjs/concepts/memory/){:target=_blank .external-link}에 대해 자세히 알아보세요.

#### 출력 파서

출력 파서는 LLM에서 생성된 텍스트를 가져와 필요한 구조와 일치하도록 형식을 지정합니다.

사용 가능한 노드:

* [자동 수정 출력 파서](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.outputparserautofixing.md)
* [항목 목록 출력 파서](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.outputparseritemlist.md)
* [구조화된 출력 파서](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.outputparserstructured/index.md)

[LangChain의 출력 파서](https://js.langchain.com/docs/concepts/output_parsers/){:target=_blank .external-link}에 대해 자세히 알아보세요.

#### 리트리버


* [문맥 압축 리트리버](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.retrievercontextualcompression.md)
* [다중 쿼리 리트리버](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.retrievermultiquery.md)
* [벡터 저장소 리트리버](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.retrievervectorstore.md)
* [워크플로우 리트리버](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.retrieverworkflow.md)


#### 텍스트 분할기

텍스트 분할기는 데이터(문서)를 분해하여 LLM이 정보를 더 쉽게 처리하고 정확한 결과를 반환하도록 합니다.

사용 가능한 노드:

* [문자 텍스트 분할기](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.textsplittercharactertextsplitter.md)
* [재귀 문자 텍스트 분할기](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.textsplitterrecursivecharactertextsplitter.md)
* [토큰 분할기](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.textsplittertokensplitter.md)

n8n의 텍스트 분할기 노드는 [LangChain의 text_splitter API](https://js.langchain.com/docs/concepts/text_splitters/){:target=_blank .external-link}의 일부를 구현합니다.

#### 도구

유틸리티 [도구](/glossary.md#ai-tool).

* [계산기](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.toolcalculator.md)
* [코드 도구](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.toolcode.md)
* [SerpAPI](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.toolserpapi.md)
* [생각 도구](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.toolthink.md)
* [벡터 저장소 도구](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.toolvectorstore.md)
* [Wikipedia](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.toolwikipedia.md)
* [Wolfram|Alpha](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.toolwolframalpha.md)
* [워크플로우 도구](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.toolworkflow.md)

#### 임베딩

> [임베딩](/glossary.md#ai-embedding)은 텍스트, 이미지, 비디오 또는 기타 유형의 정보의 "관련성"을 포착합니다. ([출처](https://supabase.com/docs/guides/ai/concepts){:target=_blank .external-link})

사용 가능한 노드:


* [임베딩 AWS Bedrock](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.embeddingsawsbedrock.md)
* [임베딩 Cohere](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.embeddingscohere.md)
* [임베딩 Google PaLM](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.embeddingsgooglepalm.md)
* [임베딩 Hugging Face 추론](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.embeddingshuggingfaceinference.md)
* [임베딩 Mistral 클라우드](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.embeddingsmistralcloud.md)
* [임베딩 Ollama](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.embeddingsollama.md)
* [임베딩 OpenAI](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.embeddingsopenai.md)

[LangChain의 텍스트 임베딩](https://js.langchain.com/docs/concepts/embedding_models/){:target=_blank .external-link}에 대해 자세히 알아보세요.


#### 기타

* [채팅 메모리 관리자](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.memorymanager.md)
