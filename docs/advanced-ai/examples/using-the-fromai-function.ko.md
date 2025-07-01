---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: AI가 도구 매개변수를 지정하도록 허용
description: n8n의 `$fromAI()` 함수가 작동하는 방식과 이를 사용하여 AI 앱 도구의 매개변수를 동적으로 채우거나 내장된 자동화를 사용하여 대신 완료하는 방법을 이해합니다.
contentType: explanation
tags:
  - $fromAI
  - $fromAI()
  - fromAI
  - fromAI()
hide:
  - tags
---

# AI가 도구 매개변수를 지정하도록 허용

도구 에이전트에 연결된 [도구](/glossary.md#ai-tool)를 구성할 때 많은 매개변수를 AI 모델 자체가 채울 수 있습니다. AI 모델은 작업의 컨텍스트와 연결된 다른 도구의 정보를 사용하여 적절한 세부 정보를 채웁니다.

이를 수행하는 방법에는 두 가지가 있으며, 이들 사이를 전환할 수 있습니다.

## 모델이 매개변수를 채우도록 허용

도구의 편집 대화 상자에 있는 각 적절한 매개변수 필드 끝에는 추가 버튼이 있습니다.

![매개변수 필드 오른쪽에 별 아이콘을 보여주는 이미지](/_images/advanced-ai/ai-stars.png)

이 버튼을 활성화하면 [AI 에이전트](/glossary.md#ai-agent)가 추가 사용자 입력 없이 자동으로 표현식을 채웁니다.
필드 자체는 매개변수가 모델에 의해 자동으로 정의되었음을 나타내는 메시지로 채워집니다.

매개변수를 직접 정의하려면 이 상자의 'X'를 클릭하여 사용자 정의 값으로 되돌립니다. '표현식' 필드에는 이제 이 기능으로 생성된 표현식이 포함되지만, 다음 섹션에 설명된 대로 추가 세부 정보를 추가하기 위해 편집할 수 있습니다.

/// warning 
이 기능을 활성화하면 이미 추가한 수동 정의를 덮어씁니다.
///

## `$fromAI()` 함수 사용

`$fromAI()` 함수는 AI를 사용하여 [도구 AI 에이전트](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.agent/tools-agent.md)에 연결된 도구의 매개변수를 동적으로 채웁니다.

/// note | 도구 전용
`$fromAI()` 함수는 AI 에이전트 노드에 연결된 도구에서만 사용할 수 있습니다. `$fromAI()` 함수는 [코드](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.toolcode.md) 도구나 [다른 비도구 클러스터 하위 노드](/integrations/builtin/cluster-nodes/sub-nodes/index.md)와 함께 작동하지 않습니다.
///

`$fromAI()` 함수를 사용하려면 필요한 `key` 매개변수와 함께 호출합니다.

```javascript
{{ $fromAI('email') }}
```

`$fromAI()` 함수에 대한 `key` 매개변수 및 기타 인수는 기존 값에 대한 참조가 아닙니다. 대신 이러한 인수를 AI 모델이 올바른 데이터를 채우는 데 사용할 힌트로 생각하세요.

예를 들어 `email`이라는 키를 선택하면 AI 모델은 컨텍스트, 다른 도구 및 입력 데이터에서 이메일 주소를 찾습니다. 채팅 워크플로우에서는 다른 곳에서 이메일 주소를 찾을 수 없는 경우 사용자에게 이메일 주소를 요청할 수 있습니다. 선택적으로 `description`과 같은 다른 매개변수를 전달하여 AI 모델에 추가 컨텍스트를 제공할 수 있습니다.

### 매개변수

`$fromAI()` 함수는 다음 매개변수를 허용합니다.

<!-- vale off -->

| 매개변수 | 유형 | 필수? | 설명 |
| --------- | ---- | --------- | ----------- |
| `key` | 문자열 | :white_check_mark: | 인수의 키 또는 이름을 나타내는 문자열입니다. 길이는 1~64자여야 하며 소문자, 대문자, 숫자, 밑줄, 하이픈만 포함할 수 있습니다. |
| `description` | 문자열 | :x: | 인수를 설명하는 문자열입니다. |
| `type` | 문자열 | :x: | 데이터 유형을 지정하는 문자열입니다. 문자열, 숫자, 부울 또는 json일 수 있습니다(기본값은 문자열). |
| `defaultValue` | any | :x: | 인수에 사용할 기본값입니다. |

<!-- vale on -->

### 예시

예를 들어 다음 `$fromAI()` 표현식을 사용하여 필드를 이름으로 동적으로 채울 수 있습니다.

```javascript
$fromAI("name", "주석 작성자의 이름", "string", "Jane Doe")
```

선택적 매개변수가 필요하지 않은 경우 다음과 같이 단순화할 수 있습니다.

```javascript
$fromAI("name")
```

재고가 있는 품목 수를 동적으로 채우려면 다음과 같은 `$fromAI()` 표현식을 사용할 수 있습니다.

```javascript
$fromAI("numItemsInStock", "재고 품목 수", "number", 5)
```

모델의 동적 값으로 필드의 일부만 채우려면 일반 표현식에서도 사용할 수 있습니다. 예를 들어 모델이 이메일의 `subject` 매개변수를 채우도록 하되 생성된 값 앞에 항상 'AI가 생성함:' 문자열을 붙이려면 다음 표현식을 사용할 수 있습니다.

```javascript
AI가 생성함: {{ $fromAI("subject") }}
```

### 템플릿

다음 [템플릿](/glossary.md#template-n8n)에서 `$fromAI()` 함수가 작동하는 것을 볼 수 있습니다.

* [Angie, 텔레그램 음성 및 텍스트를 사용하는 개인 AI 비서](https://n8n.io/workflows/2462-angie-personal-ai-assistant-with-telegram-voice-and-text/)
* [AI 텍스트 분류기를 사용하여 고객 지원 문제 해결 자동화](https://n8n.io/workflows/2468-automate-customer-support-issue-resolution-using-ai-text-classifier/)
* [피치 덱 AI 비전, 챗봇 및 QDrant 벡터 저장소로 거래 흐름 확장](https://n8n.io/workflows/2464-scale-deal-flow-with-a-pitch-deck-ai-vision-chatbot-and-qdrant-vector-store/)
