---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
description: n8n을 사용해 보는 빠른 예제입니다.
contentType: tutorial
---

# 매우 빠른 퀵스타트

이 퀵스타트는 가능한 한 빨리 n8n을 시작하는 데 도움이 됩니다. UI를 사용해 보고 [워크플로우 템플릿](/glossary.md#template-n8n) 및 [표현식](/glossary.md#expression-n8n)이라는 두 가지 주요 기능을 소개합니다. 자세한 설명이나 개념에 대한 심층적인 탐구는 포함하지 않습니다.

이 튜토리얼에서는 다음을 수행합니다.

* 워크플로우 템플릿 라이브러리에서 [워크플로우](/glossary.md#workflow-n8n) 로드
* 노드를 추가하고 표현식을 사용하여 구성
* 첫 번째 워크플로우 실행

## 1단계: n8n에 가입

이 퀵스타트는 [n8n Cloud](/manage-cloud/overview.md)를 사용합니다. 신규 사용자는 무료 평가판을 사용할 수 있습니다. 아직 가입하지 않았다면 지금 [가입](https://app.n8n.cloud/register)하여 계정을 만드세요.

## 2단계: 워크플로우 템플릿 열기

n8n은 교육 노드를 사용하는 퀵스타트 템플릿을 제공합니다. 이를 사용하여 가짜 데이터로 작업하고 [자격 증명](/glossary.md#credential-n8n) 설정을 피할 수 있습니다.

1. [템플릿 | 매우 빠른 퀵스타트](https://n8n.io/workflows/1700-very-quick-quickstart/)로 이동합니다.
2. **워크플로우 사용**을 선택하여 템플릿 사용 옵션을 봅니다.
3. **<name> 클라우드 작업 공간으로 템플릿 가져오기**를 선택하여 템플릿을 클라우드 인스턴스로 로드합니다.

이 워크플로우는 다음을 수행합니다.

1. [고객 데이터 저장소](/integrations/builtin/app-nodes/n8n-nodes-base.n8ntrainingcustomerdatastore.md) 노드에서 예제 데이터를 가져옵니다.
2. [필드 편집](/integrations/builtin/core-nodes/n8n-nodes-base.set.md) 노드를 사용하여 원하는 데이터만 추출하고 해당 데이터를 변수에 할당합니다. 이 예에서는 고객 이름, ID 및 설명을 매핑합니다.

n8n 워크플로우의 개별 부분을 [노드](/glossary.md#node-n8n)라고 합니다. 노드를 두 번 클릭하여 설정을 탐색하고 데이터를 처리하는 방법을 확인합니다.

## 3단계: 워크플로우 실행

**워크플로우 테스트**를 선택합니다. 그러면 워크플로우가 실행되어 고객 데이터 저장소 노드에서 데이터를 로드한 다음 필드 편집으로 변환합니다. 다음 단계에서 작업할 수 있도록 워크플로우에서 이 데이터를 사용할 수 있어야 합니다.

## 4단계: 노드 추가

세 번째 노드를 추가하여 각 고객에게 메시지를 보내고 설명을 알려줍니다. 고객 메신저 노드를 사용하여 가짜 수신자에게 메시지를 보냅니다.

1. 필드 편집 노드에서 **노드 추가** <span class="inline-image">![노드 추가 아이콘](/_images/try-it-out/add-node-small.png){.off-glb}</span> 커넥터를 선택합니다.
2. **고객 메신저**를 검색합니다. n8n은 검색과 일치하는 노드 목록을 표시합니다.
3. **고객 메신저(n8n 교육)**를 선택하여 노드를 [캔버스](/glossary.md#canvas-n8n)에 추가합니다. n8n이 노드를 자동으로 엽니다.
4. [표현식](/code/expressions.md)을 사용하여 **고객 ID**를 매핑하고 **메시지**를 만듭니다.
	1. **입력** 패널에서 **스키마** 탭을 선택합니다.
	2. **필드 편집1** > **customer_id**를 노드 설정의 **고객 ID** 필드로 드래그합니다.
    2. **메시지** 위로 마우스를 가져갑니다. **표현식** 탭을 선택한 다음 확장 버튼 <span class="inline-image">![노드 추가 아이콘](/_images/common-icons/open-expression-editor.png){.off-glb}</span>을 선택하여 전체 표현식 편집기를 엽니다.
    3. 이 표현식을 편집기에 복사합니다.
        ```
        안녕하세요 {{ $json.customer_name }}. 귀하의 설명은 다음과 같습니다: {{ $json.customer_description }}
        ```
5. 표현식 편집기를 닫은 다음 노드 외부를 클릭하거나 **캔버스로 돌아가기**를 선택하여 **고객 메신저** 노드를 닫습니다.
6. **워크플로우 테스트**를 선택합니다. n8n이 워크플로우를 실행합니다.

완성된 워크플로우는 다음과 같아야 합니다.

[[ workflowDemo("file:///try-it-out/quickstart/very-quick-quickstart-workflow.json") ]]


## 다음 단계

* 더 복잡한 워크플로우와 더 많은 기능 및 n8n 개념에 대한 소개는 n8n의 [더 긴 직접 해보기 튜토리얼](/try-it-out/tutorial-first-workflow.md)을 읽어보세요.
* [텍스트 과정](/courses/index.md) 또는 [비디오 과정](/video-courses.md)을 수강하세요.
