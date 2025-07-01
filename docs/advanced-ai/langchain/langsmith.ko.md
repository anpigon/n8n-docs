---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
contentType: howto
title: n8n에서 LangSmith 사용하기
description: 자체 호스팅 n8n 인스턴스에 대해 LangSmith를 활성화하는 방법.
---

# n8n에서 LangSmith 사용하기

[LangSmith](https://www.langchain.com/langsmith){:target=_blank .external-link}는 LangChain 팀에서 만든 개발자 플랫폼입니다. n8n 인스턴스를 LangSmith에 연결하여 LangChain 애플리케이션에서와 마찬가지로 n8n에서 실행을 기록하고 모니터링할 수 있습니다.

/// info | 기능 가용성
자체 호스팅 n8n만 해당.
///

## n8n 인스턴스를 LangSmith에 연결하기

1. [LangSmith에 로그인](https://smith.langchain.com/settings){:target=_blank .external-link}하고 API 키를 받으세요.
1. LangSmith 환경 변수를 설정합니다.

	| 변수 | 값 |
	| -------- | ----- |
	| LANGCHAIN_ENDPOINT | `"https://api.smith.langchain.com"` |
	| LANGCHAIN_TRACING_V2 | `true` |
	| LANGCHAIN_API_KEY | API 키로 설정하세요 |

	n8n 인스턴스를 호스팅하는 환경에서 전역적으로 사용할 수 있도록 변수를 설정하세요. 나머지 일반 구성과 동일한 방식으로 이 작업을 수행할 수 있습니다. 이것은 n8n 환경 변수가 아니므로 [n8n 구성 파일](/hosting/configuration/configuration-methods.md#set-environment-variables-using-a-file)을 사용하여 설정하려고 하지 마세요.

1. n8n을 다시 시작합니다.

LangSmith 사용에 대한 정보는 [LangSmith의 설명서](https://docs.smith.langchain.com/){:target=_blank .external-link}를 참조하세요.
