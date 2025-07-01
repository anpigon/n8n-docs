---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
contentType: howto
title: 웹사이트에서 Pinecone 벡터 데이터베이스 채우기
description: 웹사이트를 스크랩하고 데이터를 Pinecone에 로드한 다음 채팅 워크플로우를 사용하여 쿼리합니다.
---

# 웹사이트에서 Pinecone 벡터 데이터베이스 채우기

n8n을 사용하여 웹사이트를 스크랩하고 데이터를 Pinecone에 로드한 다음 채팅 워크플로우를 사용하여 쿼리합니다. 이 워크플로우는 [HTTP 노드](/integrations/builtin/core-nodes/n8n-nodes-base.httprequest/index.md)를 사용하여 웹사이트 데이터를 가져오고 [HTML 노드](/integrations/builtin/core-nodes/n8n-nodes-base.html.md)를 사용하여 관련 콘텐츠를 추출한 다음 [Pinecone 벡터 저장소 노드](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.vectorstorepinecone.md)를 사용하여 Pinecone으로 보냅니다.

[[ workflowDemo("file:///advanced-ai/examples/populate_a_pinecone_vector_database_from_a_website.json") ]]

## 주요 기능

이 워크플로우는 다음을 사용합니다.

* [HTTP 노드](/integrations/builtin/core-nodes/n8n-nodes-base.httprequest/index.md): 웹사이트 데이터를 가져옵니다.
* [HTML 노드](/integrations/builtin/core-nodes/n8n-nodes-base.html.md): 페이지에서 기본 콘텐츠를 추출하여 데이터를 단순화합니다.
* [Pinecone 벡터 저장소 노드](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.vectorstorepinecone.md) 및 [Embeddings OpenAI](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.embeddingsopenai.md): 데이터를 벡터로 변환하여 Pinecone에 저장합니다.
* [채팅 트리거](/integrations/builtin/core-nodes/n8n-nodes-langchain.chattrigger/index.md) 및 [질의응답 체인](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.chainretrievalqa/index.md)을 사용하여 벡터 데이터베이스를 쿼리합니다.


## 예제 사용

--8<-- "_snippets/examples-color-key.md"
