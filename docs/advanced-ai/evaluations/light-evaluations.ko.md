---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 라이트 평가
description: 개발 중 라이트 평가를 사용하여 알려진 테스트 케이스의 성능을 측정하여 신뢰할 수 있는 LLM 기반 워크플로우를 구축합니다.
description: 개발 중 라이트 평가를 사용하여 알려진 테스트 케이스에 대한 실행 결과를 확인하여 신뢰할 수 있는 LLM 기반 워크플로우를 구축합니다.
contentType: howto
---

# 라이트 평가
<!-- vale from-microsoft.HeadingPunctuation = NO -->

/// note | 등록된 커뮤니티 및 유료 플랜에서 사용 가능
라이트 평가는 등록된 커뮤니티 사용자와 모든 유료 플랜에서 사용할 수 있습니다.
///

## 라이트 평가란 무엇인가요?

워크플로우를 구축할 때 몇 가지 예제로 테스트하여 성능을 파악하고 개선하는 경우가 많습니다. 워크플로우 개발의 이 단계에서는 각 예제에 대한 워크플로우 출력을 살펴보는 것만으로도 충분한 경우가 많습니다. 보다 [공식적인 점수 또는 메트릭](/advanced-ai/evaluations/metric-based-evaluations.md)을 설정하는 이점은 아직 그 노력을 정당화하지 못합니다.

라이트 평가를 사용하면 테스트 데이터 세트의 예제를 워크플로우를 통해 하나씩 실행하고 출력을 데이터 세트에 다시 쓸 수 있습니다. 그런 다음 해당 출력을 나란히 검토하고 예상 출력(있는 경우)과 시각적으로 비교할 수 있습니다.

## 작동 방식

/// note | Google Sheets 필요
평가는 Google Sheets를 사용하여 테스트 데이터 세트를 저장합니다. 평가를 사용하려면 [Google Sheets 자격 증명](/integrations/builtin/credentials/google/index.md)을 구성해야 합니다.
///

라이트 평가는 워크플로우의 '편집기' 탭에서 이루어지지만 '평가' 탭에서 설정 방법에 대한 지침을 찾을 수 있습니다.

단계:

1. 데이터 세트 생성
2. 데이터 세트를 워크플로우에 연결
3. 워크플로우 출력을 데이터 세트에 다시 쓰기
4. 평가 실행

다음 설명에서는 들어오는 지원 티켓에 범주와 우선순위를 할당하는 샘플 워크플로우를 사용합니다.

![예제 AI 워크플로우 ](/_images/advanced-ai/evaluations/example-ai-workflow.png)

### 1. 데이터 세트 생성

워크플로우에 대한 몇 가지 예제가 포함된 Google Sheet를 만듭니다. 시트에는 다음 열이 포함되어야 합니다.

- 워크플로우 입력
- (선택 사항) 예상 또는 올바른 워크플로우 출력
- 실제 출력

평가 중에 채울 것이므로 실제 출력 열은 비워 둡니다.

<figure markdown="span">
![지원 티켓 분류 워크플로우용 샘플 데이터 세트](/_images/advanced-ai/evaluations/sample-dataset.png)
<figcaption>지원 티켓 분류 워크플로우용 <a href="https://docs.google.com/spreadsheets/d/1uuPS5cHtSNZ6HNLOi75A2m8nVWZrdBZ_Ivf58osDAS8/edit?gid=294497137#gid=294497137">샘플 데이터 세트</a>입니다.</figcaption>
</figure>

### 2. 데이터 세트를 워크플로우에 연결

#### 데이터 세트를 가져오기 위한 평가 트리거 삽입

[평가 트리거](/integrations/builtin/core-nodes/n8n-nodes-base.evaluationtrigger.md)가 실행될 때마다 데이터 세트의 한 행을 나타내는 단일 항목이 출력됩니다.

평가 트리거 왼쪽에 있는 '모두 평가' 버튼을 클릭하면 데이터 세트의 각 행에 대해 한 번씩 워크플로우가 순서대로 여러 번 실행됩니다. 이것은 평가 트리거의 특별한 동작입니다.

트리거를 연결하는 동안 한 번만 실행하고 싶은 경우가 많습니다. 다음 중 하나를 수행하여 이 작업을 수행할 수 있습니다.

- 트리거의 '처리할 최대 행'을 1로 설정
- 트리거의 '노드 실행' 버튼 클릭('모두 평가' 버튼 대신)

#### 트리거를 워크플로우에 연결

이제 평가 트리거를 나머지 워크플로우에 연결하고 출력하는 데이터를 참조할 수 있습니다. 최소한 나중에 워크플로우에서 데이터 세트의 입력 열을 사용해야 합니다.

워크플로우에 여러 트리거가 있는 경우 [해당 분기를 함께 병합](/advanced-ai/evaluations/tips-and-common-issues.md#combining-multiple-triggers)해야 합니다.

<figure markdown="span">
![평가 트리거 연결](/_images/advanced-ai/evaluations/connecting-evaluation-trigger.png)
<figcaption>평가 트리거가 추가되고 연결된 지원 티켓 분류 워크플로우입니다.</figcaption>
</figure>

### 3. 워크플로우 출력을 데이터 세트에 다시 쓰기

평가가 실행될 때 데이터 세트의 출력 열을 채우려면 다음을 수행합니다.

- [평가 노드](/integrations/builtin/core-nodes/n8n-nodes-base.evaluation.md)의 '출력 설정' 작업을 삽입합니다.
- 평가 중인 출력을 생성한 후 워크플로우에 연결합니다.
- 노드의 매개변수에서 워크플로우 출력을 올바른 데이터 세트 열에 매핑합니다.

<figure markdown="span">
![출력 설정 노드 연결](/_images/advanced-ai/evaluations/connecting-set-outputs-node.png)
<figcaption>'출력 설정' 노드가 추가되고 연결된 지원 티켓 분류 워크플로우입니다.</figcaption>
</figure>

### 4. 평가 실행

평가 트리거 왼쪽에 있는 **워크플로우 실행** 버튼을 클릭합니다. 워크플로우는 데이터 세트의 각 행에 대해 한 번씩 여러 번 실행됩니다.

![워크플로우 실행 버튼](/_images/advanced-ai/evaluations/execute-workflow-button.png)

Google Sheet에서 각 실행의 출력을 검토하고 필요한 경우 워크플로우의 '실행' 탭을 사용하여 실행 세부 정보를 검토합니다.

데이터 세트가 몇 가지 예제를 넘어 커지면 성능에 대한 수치적 보기를 얻기 위해 [메트릭 기반 평가](/advanced-ai/evaluations/metric-based-evaluations.md)를 고려하십시오. 또한 [팁 및 일반적인 문제](/advanced-ai/evaluations/tips-and-common-issues.md)를 참조하십시오.
