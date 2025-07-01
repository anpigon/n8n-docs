---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 릴리스 노트
description: n8n의 새로운 기능과 버그 수정을 상세히 설명하는 릴리스 노트입니다.
tags:
  - 릴리스
  - 릴리스 노트
  - 변경 로그
hide:
  - 태그
contentType: reference
---
<!-- vale off -->
# 릴리스 노트

n8n의 새로운 기능과 버그 수정 사항입니다.

GitHub 리포지토리에서 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 확인할 수도 있습니다.

--8<-- "_snippets/self-hosting/installation/latest-next-version.md"

--8<-- "_snippets/update-n8n.md"

## n8n의 시맨틱 버전 관리

n8n은 [시맨틱 버전 관리](https://semver.org/){:target=_blank .external-link}를 사용합니다. 모든 버전 번호는 `MAJOR.MINOR.PATCH` 형식입니다. 버전 번호는 다음과 같이 증가합니다.

* 사용자 조치가 필요할 수 있는 호환되지 않는 변경 시 MAJOR 버전.
* 하위 호환되는 방식으로 기능을 추가할 때 MINOR 버전.
* 하위 호환되는 버그 수정 시 PATCH 버전.

/// note | 이전 버전
n8n의 이전 버전 릴리스 노트는 [여기](/release-notes/0-x.md)에서 찾을 수 있습니다.
///



## n8n@1.100.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.100.0...n8n@1.100.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-06-25

/// note | 다음 버전
이것은 `next` 버전입니다. n8n은 `latest` 버전을 사용하는 것을 권장합니다. `next` 버전은 불안정할 수 있습니다. 문제를 보고하려면 [포럼](https://community.n8n.io/c/questions/12){:target=_blank .external-link}을 사용하십시오.
///

이 릴리스에는 버그 수정이 포함되어 있습니다.


전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.



## n8n@1.100.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.99.0...n8n@1.100.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-06-23



이 릴리스에는 핵심 업데이트, 편집기 개선, 새 노드, 노드 업데이트 및 버그 수정이 포함되어 있습니다.

### OIDC(OpenID Connect) 인증 지원

이제 단일 로그온(SSO)을 위한 인증 방법으로 OIDC(OpenID Connect)를 사용할 수 있습니다.

이를 통해 엔터프라이즈 팀은 널리 채택되고 관리하기 쉬운 표준을 사용하여 n8n을 기존 ID 공급자와 통합할 수 있는 유연성을 확보할 수 있습니다. OIDC는 이제 SAML과 함께 사용할 수 있으므로 기업은 내부 요구 사항에 가장 적합한 것을 선택할 수 있습니다.

### 프로젝트 관리자는 이제 환경 내에서 Git에 커밋할 수 있습니다.

프로젝트 관리자는 이제 환경 기능을 통해 워크플로우 및 자격 증명 변경 사항을 Git에 직접 커밋할 수 있습니다. 이 업데이트는 프로젝트 수준 관리자에게 변경 사항 커밋에 대한 직접적인 제어 권한을 부여하여 워크플로우 배포 프로세스를 간소화합니다. 또한 워크플로우를 가장 잘 아는 사람들이 인스턴스 수준 관리자를 참여시킬 필요 없이 직접 업데이트를 검토하고 커밋할 수 있도록 합니다.

[소스 제어 환경에 대해 자세히 알아보기](/source-control-environments/index.md)


### 기여자

[aliou](https://github.com/aliou){:target=_blank .external-link}  

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.



## n8n@1.99.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.99.0...n8n@1.99.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-06-19

/// note | 최신 버전
이것은 `latest` 버전입니다. n8n은 `latest` 버전을 사용하는 것을 권장합니다. `next` 버전은 불안정할 수 있습니다. 문제를 보고하려면 [포럼](https://community.n8n.io/c/questions/12){:target=_blank .external-link}을 사용하십시오.
///





이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.


## n8n@1.98.2

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.98.1...n8n@1.98.2){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-06-18



이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.


## n8n@1.99.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.98.0...n8n@1.99.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-06-16

이 릴리스에는 성능 개선, 핵심 업데이트, 편집기 변경, 노드 업데이트 및 버그 수정이 포함되어 있습니다.

### 노드 자동 이름 지정

기본 노드 이름은 이제 선택한 리소스 및 작업에 따라 자동으로 업데이트되므로 노드가 수행하는 작업을 한 눈에 항상 알 수 있습니다.

이렇게 하면 캔버스가 더 명확해지고 노드 이름을 수동으로 바꾸는 시간을 절약할 수 있습니다.

걱정하지 마십시오. 자동 이름 지정은 참조를 깨뜨리지 않습니다. 그리고 노드 이름을 직접 바꾼 경우 그대로 둡니다.

<br>
<video src="/_video/release-notes/automatic_node_naming.mp4" controls width="100%"></video>
<br>

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.98.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.98.0...n8n@1.98.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-06-12



이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.



## n8n@1.98.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.97.0...n8n@1.98.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-06-11



이 릴리스에는 성능 개선, 핵심 업데이트, 편집기 변경, 노드 업데이트, 새 노드 및 버그 수정이 포함되어 있습니다.

### 기여자

[luka-mimi](https://github.com/luka-mimi){:target=_blank .external-link}  
[Alexandero89](https://github.com/Alexandero89){:target=_blank .external-link}  
[khoazero123](https://github.com/khoazero123){:target=_blank .external-link}  

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.


## n8n@1.97.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.97.0...n8n@1.97.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-06-04







이 릴리스에는 백포트가 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.95.3

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.95.2...n8n@1.95.3){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-06-03



이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.97.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.96.0...n8n@1.97.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-06-02

이 릴리스에는 새로운 기능, 성능 개선 및 버그 수정이 포함되어 있습니다.

### 하위 워크플로우로 변환

크고 단일한 워크플로우는 속도를 저하시킬 수 있습니다. 유지 관리하기가 더 어렵고 디버깅하기가 더 어려우며 확장하기가 더 어렵습니다. 하위 워크플로우를 사용하면 더 모듈화된 접근 방식을 취하여 큰 워크플로우를 재사용, 테스트, 이해 및 설명하기 쉬운 더 작고 관리하기 쉬운 부분으로 나눌 수 있습니다.

지금까지 하위 워크플로우를 만들려면 노드를 수동으로 복사하여 붙여넣고, 새 워크플로우를 처음부터 설정하고, 모든 것을 수동으로 다시 연결해야 했습니다. **하위 워크플로우로 변환**을 사용하면 이 프로세스를 단일 작업으로 단순화하여 재구성하는 데 시간을 덜 들이고 빌드하는 데 더 많은 시간을 할애할 수 있습니다.

<br>
<video src="/_video/release-notes/convert_to_sub-workflow.mp4" controls width="100%"></video>
<br>

**작동 방식**

1. 하위 워크플로우로 변환하려는 노드를 강조 표시합니다. 다음을 충족해야 합니다.
    - 완전히 연결되어 있어야 합니다. 즉, 중간에 누락된 단계가 없어야 합니다.
    - 단일 시작 노드에서 시작해야 합니다.
    - 단일 노드로 끝나야 합니다.
2. 마우스 오른쪽 버튼을 클릭하여 컨텍스트 메뉴를 열고 **하위 워크플로우로 변환**을 선택합니다.
    - 또는 바로 가기 키 `Alt + X`를 사용합니다.
3. n8n은 다음을 수행합니다.
    - 선택한 노드가 포함된 새 탭을 엽니다.
    - 모든 노드 매개변수를 그대로 유지합니다.
    - 원래 워크플로우에서 선택한 노드를 **내 하위 워크플로우 호출** 노드로 바꿉니다.

*참고*: 새 하위 워크플로우의 시작 및 반환 노드에서 필드 유형을 수동으로 조정해야 합니다.

이렇게 하면 워크플로우를 모듈식으로 유지하고 성능을 높이며 유지 관리하기가 더 쉬워집니다.

[하위 워크플로우](/flow-logic/subworkflows.md)에 대해 자세히 알아보십시오.

이 릴리스에는 성능 개선 및 버그 수정이 포함되어 있습니다.


### 기여자

[maatthc](https://github.com/maatthc){:target=_blank .external-link}  

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.96.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.95.0...n8n@1.96.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-06-02

/// warning | 빌드 실패
이 릴리스는 빌드에 실패했습니다. 대신 `1.97.0`을 사용하십시오.
///

이 릴리스에는 API 업데이트, 핵심 변경, 편집기 개선, 노드 업데이트 및 버그 수정이 포함되어 있습니다.

### 프로젝트에 사용자 할당을 위한 API 지원

이제 API를 사용하여 프로젝트 내에서 사용자를 추가하고 업데이트할 수 있습니다. 여기에는 다음이 포함됩니다.

- 기존 또는 보류 중인 사용자를 특정 역할로 프로젝트에 할당
- 프로젝트 내에서 사용자 역할 업데이트
- 하나 이상의 프로젝트에서 사용자 제거

이 업데이트를 통해 이제 API를 사용하여 인스턴스와 특정 프로젝트 모두에 사용자를 추가할 수 있으므로 UI에서 수동으로 할당할 필요가 없습니다.

### 프로젝트 구성원 할당에 보류 중인 사용자 추가

이제 초대되었지만 가입을 완료하지 않은 **보류 중인 사용자**를 프로젝트에 구성원으로 추가할 수 있습니다.

이 변경 사항을 통해 사용자가 계정 설정을 완료할 때까지 기다리지 않고도 사용자의 프로젝트 액세스를 미리 구성할 수 있습니다. 가입 후 액세스 관리의 번거로움을 없애고 사용자가 가입 즉시 올바른 프로젝트 역할을 갖도록 보장합니다.

### 기여자

[matthabermehl](https://github.com/matthabermehl){:target=_blank .external-link}  
[Stamsy](https://github.com/Stamsy){:target=_blank .external-link}  

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.95.2

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.95.1...n8n@1.95.2){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-05-29

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.95.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.95.0...n8n@1.95.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-05-27

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.94.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.94.0...n8n@1.94.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-05-27

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.95.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.94.0...n8n@1.95.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-05-26

이 릴리스에는 핵심 업데이트, 편집기 개선, 노드 업데이트 및 버그 수정이 포함되어 있습니다.

<div class="n8n-new-features" markdown> 

### AI 워크플로우 평가

AI 자동화에 대한 변경 사항을 프로덕션에 적용하기 전에 반복, 테스트 및 비교하여 예측 가능성을 높이고 더 나은 결정을 내릴 수 있도록 돕는 기능을 추가했습니다.<br><br>

AI로 빌드할 때 작은 프롬프트 조정이나 모델 교체는 일부 입력에서는 결과를 개선하지만 다른 입력에서는 조용히 성능을 저하시킬 수 있습니다. 그러나 많은 입력에 대한 성능을 평가할 방법이 없으면 변경 시 AI가 실제로 개선되고 있는지 추측할 수밖에 없습니다.  <br><br>

n8n에서 **AI 워크플로우 평가**를 구현하면 테스트 사례를 실행하고 사용자 지정 메트릭을 적용하여 결과를 추적하는 전용 경로를 워크플로우에 추가하여 다양한 입력에 대해 AI가 어떻게 수행되는지 평가할 수 있습니다. 이를 통해 실행 가능한 개념 증명을 신속하게 구축하고, 더 효과적으로 반복하고, 회귀를 조기에 포착하고, AI가 프로덕션에 있을 때 더 자신감 있는 결정을 내릴 수 있습니다.<br><br>


<iframe width="560" height="315" src="https://www.youtube.com/embed/5LlF196PKaE?si=TcwM0JyhjsRKDb3x" title="YouTube 동영상 플레이어" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

<br><br>

#### 평가 노드 및 탭

**평가 노드**에는 함께 사용될 때 종단 간 AI 평가를 가능하게 하는 여러 작업이 포함되어 있습니다.

<br> 
<figure markdown="span">
    ![평가 노드](/_images/release-notes/Evaluations_node.png)
    <figcaption>평가 노드</figcaption>
</figure>
<br>

이 노드를 사용하여 다음을 수행합니다.

- 동일한 실행에서 다양한 테스트 사례에 대해 AI 논리 실행
- 해당 테스트 사례의 출력 캡처
- 자체 메트릭 또는 LLM-as-judge 논리를 사용하여 결과 채점
- 평가하려는 노드 및 논리만 포함하도록 테스트 경로 격리 <br>

**평가 탭**을 사용하면 n8n UI에서 테스트 결과를 검토할 수 있으므로 실행을 비교하고 회귀를 발견하고 시간 경과에 따른 성능을 보는 데 적합합니다.
<br><br>

#### 🛠 평가 작동 방식

평가 경로는 일반 실행 논리와 함께 실행되며 원할 때만 활성화되므로 테스트 및 반복에 이상적입니다. <br><br>

하나 이상의 LLM 또는 에이전트 노드를 포함하는 평가하려는 AI 워크플로우를 선택하여 시작하십시오. <br> 

1. **새 평가 이벤트 시** 작업으로 **평가** 노드를 추가합니다. 이 노드는 테스트할 때만 실행할 추가 트리거 역할을 합니다. 각 행이 테스트 입력을 나타내는 Google Sheets에서 데이터 세트를 읽도록 구성합니다.<br>

    > 💡  더 나은 데이터 세트는 더 나은 평가를 의미합니다. AI가 어떻게 수행되는지에 대한 의미 있는 피드백을 얻으려면 엣지 케이스 및 일반적인 입력을 포함한 다양한 테스트 사례에서 데이터 세트를 만드십시오. [여기](/advanced-ai/evaluations/light-evaluations.md/#1-create-a-dataset)에서 자세히 알아보고 샘플 데이터 세트에 액세스하십시오.

2. 테스트 중인 워크플로우 부분(일반적으로 LLM 또는 에이전트 노드 뒤) 다음에 **출력 설정** 작업을 사용하여 두 번째 **평가** 노드를 추가합니다. 이렇게 하면 응답을 캡처하고 Google Sheets의 데이터 세트에 다시 씁니다.
3. 출력 품질을 평가하려면 출력을 생성한 후 한 지점에서 **메트릭 설정** 작업으로 세 번째 **평가** 노드를 추가합니다. 워크플로우 논리, 사용자 지정 계산을 개발하거나 LLM-as-Judge를 추가하여 출력을 채점할 수 있습니다. 이러한 메트릭을 노드의 매개변수에서 데이터 세트에 매핑합니다. <br> 

    > 💡 잘 정의된 메트릭 = 더 현명한 결정. 유사성, 정확성 또는 분류를 기반으로 출력을 채점하면 변경 사항이 실제로 성능을 향상시키는지 추적하는 데 도움이 될 수 있습니다. [여기](/advanced-ai/evaluations/metric-based-evaluations.md/#2-calculate-metrics)에서 자세히 알아보고 예제 템플릿에 대한 링크를 얻으십시오. 
    
<br>

<figure markdown="span">
    ![평가 워크플로우](/_images/release-notes/Evaluations_workflow.png)
    <figcaption>평가 워크플로우</figcaption>
</figure>
<br>

평가 트리거 노드가 실행되면 데이터 세트의 각 입력을 AI 논리를 통해 실행합니다. 모든 테스트 사례가 처리되거나 한도에 도달하거나 수동으로 실행을 중지할 때까지 계속됩니다. 평가 경로가 설정되면 프롬프트, 모델 또는 워크플로우 논리를 업데이트하고 평가 트리거 노드를 다시 실행하여 결과를 비교할 수 있습니다. 메트릭을 추가한 경우 평가 탭에 표시됩니다. <br><br>

경우에 따라 반복을 더 빠르게 하거나 다운스트림 논리 실행을 피하기 위해 테스트 경로를 격리할 수 있습니다.  이 경우 `평가 중인지 확인` 작업으로 평가 노드를 추가하여 평가를 수행할 때 예상되는 노드만 실행되도록 할 수 있습니다. <br><br>

#### 염두에 두어야 할 사항

AI 워크플로우 평가는 개발 흐름에 맞게 설계되었으며 더 많은 개선 사항이 제공될 예정입니다. 현재로서는 몇 가지 참고 사항이 있습니다.

- 테스트 데이터 세트는 현재 Google Sheets를 통해 관리됩니다. 평가를 실행하려면 Google Sheets 자격 증명이 필요합니다.
- 각 워크플로우는 한 번에 하나의 평가를 지원합니다. 여러 세그먼트를 테스트하려면 더 많은 유연성을 위해 하위 워크플로우로 분할하는 것을 고려하십시오.
- 커뮤니티 에디션은 단일 평가를 지원합니다. 프로 및 엔터프라이즈 플랜은 무제한 평가를 허용합니다.
- 현재 확장 모드의 인스턴스에서는 AI 평가가 활성화되어 있지 않습니다. <br>

[여기](https://docs.n8n.io/advanced-ai/evaluations/tips-and-common-issues/)에서 세부 정보, 팁 및 일반적인 문제 해결 정보를 찾을 수 있습니다. <br><br>

 👉 2025년 7월 2일 오후 5시(GMT+2)에 진행되는 **라이브 스트림**에서 AI 평가 전략 및 실제 구현 기술에 대해 자세히 알아보십시오. [가입](https://lu.ma/rfniiq2c). 

</div> 

### 기여자

[Phiph](https://github.com/Phiph){:target=_blank .external-link}  
[cesars-gh](https://github.com/cesars-gh){:target=_blank .external-link}  

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.94.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.93.0...n8n@1.94.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-05-19

이 릴리스에는 편집기 개선, API 업데이트, 노드 업데이트, 새 노드 및 버그 수정이 포함되어 있습니다.

<div class="n8n-new-features" markdown> 

### 클라우드에서 검증된 커뮤니티 노드

n8n 생태계를 확장하고 n8n 클라우드 사용자를 포함한 모든 사용자에게 새로운 수준의 유연성을 제공했습니다! 이제 캔버스를 떠나지 않고도 선택된 커뮤니티 노드 및 파트너 통합에 액세스할 수 있습니다. 즉, 작업 공간을 떠나지 않고도 더 넓은 범위의 통합을 설치하고 자동화할 수 있습니다. 커뮤니티의 힘이 이제 내장되었습니다.

이 업데이트는 세 가지 주요 개선 사항에 중점을 둡니다.

- **클라우드 가용성**: 커뮤니티 노드는 더 이상 자체 호스팅 사용자만을 위한 것이 아닙니다. 이제 n8n 클라우드에서 선택된 노드 세트를 사용할 수 있습니다.
- **내장 검색**: 편집기를 떠나거나 npm에서 검색하지 않고도 노드 패널에서 바로 이러한 노드를 찾고 탐색할 수 있습니다.
- **신뢰 및 검증**: 편집기에 표시되는 노드는 품질 및 보안에 대해 수동으로 검사되었습니다. 이러한 검증된 노드는 확인 표시로 표시됩니다.

가장 많이 사용되는 커뮤니티 빌드 패키지 및 파트너 지원 통합을 포함하여 약 25개의 노드를 선택하여 시작합니다. 이 단계에서는 외부 패키지 종속성을 포함하지 않는 노드에 중점을 두어 검토 프로세스를 간소화하고 원활한 출시를 보장했습니다.
<br>
<br>

이것은 시작에 불과합니다. 우리는 라이브러리를 점진적으로 확장하여 강력하고 창의적인 사용 사례와 함께 더 많은 검증된 노드를 편집기에 도입할 계획입니다. 시간이 지남에 따라 우리의 기준은 진화하여 품질과 보안을 유지하면서 더 넓은 범위의 기여에 대한 문을 열 것입니다.
<br>
<br>

이 업데이트에 대해 자세히 알아보고 [블로그](https://blog.n8n.io/community-nodes-available-on-n8n-cloud/) 게시물에서 편집기에서 이미 설치할 수 있는 노드를 확인하십시오. 

<br>

 💻 **검증된 노드 사용**

**n8n 버전 1.94.0** 이상을 사용하고 있고 인스턴스 소유자가 검증된 커뮤니티 노드를 활성화했는지 확인하십시오. 클라우드에서는 관리자 패널에서 이 작업을 수행할 수 있습니다. 자체 호스팅 인스턴스의 경우 [설명서](/hosting/configuration/environment-variables/nodes.md)를 참조하십시오. 두 경우 모두 검증된 노드는 기본적으로 활성화되어 있습니다.

- 편집기에서 **노드 패널** 열기
- 노드 검색. 검증된 노드는 방패 🛡️로 표시됩니다.
- 노드를 선택하고 **설치**를 클릭합니다.

<br>
<video src="/_video/release-notes/Community-nodes-node-panel.mp4" controls width="100%"></video>
<br>

소유자가 노드를 설치하면 인스턴스의 모든 사람이 워크플로우의 다른 노드처럼 드래그, 드롭 및 연결하여 사용을 시작할 수 있습니다.

<br>

🛠️ **노드를 빌드하고 검증받기**

노드가 검증되고 편집기에서 검색 가능하도록 하시겠습니까? 참여 방법은 다음과 같습니다.

1. [커뮤니티 노드 검증 지침](/integrations/creating-nodes/build/reference/verification-guidelines.md)을 검토합니다.
2. 새로운 것을 빌드하는 경우 [노드 생성](/integrations/creating-nodes/overview.md)에 대한 권장 사항을 따르십시오.
3. [UX 지침](/integrations/creating-nodes/build/reference/ux-guidelines.md)에 대해 디자인을 확인합니다.
4. npm에 [노드 제출](/integrations/creating-nodes/deploy/submit-community-nodes.md)합니다.
5. [이 양식](https://internal.users.n8n.cloud/form/f0ff9304-f34a-420e-99da-6103a2f8ac5b)을 작성하여 검증을 요청합니다.

<br>

**이미 노드를 빌드했습니까? 손을 드세요!**

이미 커뮤니티 노드를 게시했고 검증을 고려하고 싶다면 위에 언급된 요구 사항을 충족하는지 확인한 다음 관심 [양식](https://internal.users.n8n.cloud/form/f0ff9304-f34a-420e-99da-6103a2f8ac5b)을 제출하여 알려주십시오. 우리는 다음 배치를 적극적으로 큐레이팅하고 있으며 귀하의 작업을 포함하고 싶습니다.

</div> 


### 확장된 로그 보기

워크플로우가 복잡해지면 디버깅이... 클릭이 많아질 수 있습니다. 확장된 **로그 보기**가 필요한 이유입니다. 이제 노드 세부 정보 보기 사이를 오가지 않고도 실행을 추적하고 문제를 해결하며 전체 워크플로우의 동작을 이해할 수 있는 더 명확한 경로를 얻을 수 있습니다. 

이 업데이트는 캔버스 하단에 통합되고 항상 액세스할 수 있는 패널을 제공하여 실행되는 각 단계를 보여줍니다. 루프, 하위 워크플로우 또는 AI 에이전트로 작업하든, 실행된 모든 항목을 실행 순서대로 구조화된 보기로 볼 수 있으며 입력, 출력 및 상태 정보가 필요한 곳에 바로 표시됩니다.

더 깊이 파고들고 싶을 때 노드 세부 정보로 이동하거나 모든 단계를 통해 단일 항목을 따라갈 수 있습니다. 실시간 강조 표시는 현재 실행 중이거나 실패한 노드를 보여주며, 모든 워크플로우의 총 실행 시간과 AI 워크플로우의 토큰 사용량을 확인하여 성능을 모니터링할 수 있습니다. 여러 화면에서 디버깅하는 경우 로그를 팝아웃하여 원하는 곳으로 드래그하기만 하면 됩니다.

⚙️**기능**

- 열거나 축소할 수 있는 캔버스 하단에 **로그 보기**를 추가합니다. (워크플로우에서 사용하는 경우 채팅도 여기에 표시됩니다).
- 하위 워크플로우의 확장된 보기를 포함하여 실행된 순서대로 **계층적 노드 목록**을 표시합니다.
- **계층 구조에서 노드를 클릭**하여 입력 및 출력을 직접 미리 보거나 링크를 사용하여 전체 노드 세부 정보 보기로 이동할 수 있습니다.
- 입력 및 출력 데이터를 켜고 끄는 기능을 제공합니다.
- 각 노드를 **실행될 때 실시간으로 강조 표시**하여 시작, 완료 또는 실패 시점을 보여줍니다.
- 유사한 방식으로 과거 실행 데이터를 탐색하기 위한 **실행 기록** 보기를 포함합니다.
- 총 실행 시간 및 총 AI 토큰 사용량(AI 지원 워크플로우의 경우)과 같은 **롤업 통계**를 표시합니다.
- 로그를 부동 창으로 열기 위한 **"팝아웃"** 버튼을 포함하여 디버깅하는 동안 다른 화면으로 드래그하는 데 적합합니다.

🛠️**방법**

확장된 로그 보기에 액세스하려면 캔버스 하단의 로그 표시줄을 클릭하십시오. 이 보기는 페이지 하단의 채팅 창을 열 때도 열립니다.

### 기여자

[Stamsy](https://github.com/Stamsy){:target=_blank .external-link}  
[feelgood-interface](https://github.com/feelgood-interface){:target=_blank .external-link}  

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.93.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.92.0...n8n@1.93.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-05-12

이 릴리스에는 핵심 업데이트, 편집기 개선, 새 노드, 노드 업데이트 및 버그 수정이 포함되어 있습니다.

### 하위 워크플로우를 여는 더 빠른 방법

다중 워크플로우 자동화를 더 빠르게 탐색할 수 있는 몇 가지 새로운 방법을 추가했습니다.

하위 워크플로우 노드가 있는 모든 워크플로우에서:

🖱️ 하위 워크플로우 노드를 마우스 오른쪽 버튼으로 클릭하고 컨텍스트 메뉴에서 `하위 워크플로우 열기`를 선택합니다.

⌨️ 키보드 단축키

- **Windows:** `CTRL + SHIFT + O` 또는 `CTRL + 더블 클릭`
- **Mac:** `CMD + SHIFT + O` 또는 `CMD + 더블 클릭`

이러한 옵션은 새 탭에서 하위 워크플로우를 엽니다.

### 워크플로우 보관

실수로 워크플로우를 제거한 적이 있다면 새로운 보관 기능을 높이 평가할 것입니다. 제거 작업으로 워크플로우를 영구적으로 삭제하는 대신 이제 워크플로우가 기본적으로 보관됩니다. 이렇게 하면 필요한 경우 복구할 수 있습니다.

**방법:**

- **워크플로우 보관** - 편집기 UI 메뉴에서 **보관**을 선택합니다. **제거** 작업을 대체했습니다.
- **보관된 워크플로우 찾기** - 보관된 워크플로우는 기본적으로 숨겨져 있습니다. 보관된 워크플로우를 찾으려면 워크플로우 필터 메뉴에서 **보관된 워크플로우 표시** 옵션을 선택합니다.
- **워크플로우 영구 삭제** - 워크플로우가 보관되면 옵션 메뉴에서 **삭제**할 수 있습니다.
- **워크플로우 복구** - 옵션 메뉴에서 **보관 취소**를 선택합니다.

**참고:** 

- 워크플로우 보관에는 이전에 제거에 필요했던 것과 동일한 권한이 필요합니다.
- 보관된 워크플로우를 실행할 하위 워크플로우로 선택할 수 없습니다.
- 활성 워크플로우는 보관될 때 비활성화됩니다.
- 보관된 워크플로우는 편집할 수 없습니다.

### 기여자

[LeaDevelop](https://github.com/LeaDevelop){:target=_blank .external-link}  
[ayhandoslu](https://github.com/ayhandoslu){:target=_blank .external-link}  
[valentina98](https://github.com/valentina98){:target=_blank .external-link}  

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.92.2

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.92.1...n8n@1.92.2){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-05-08

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.91.3

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.91.2...n8n@1.91.3){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-05-08

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.92.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.92.0...n8n@1.92.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-05-06

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.92.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.91.0...n8n@1.92.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-05-05

이 릴리스에는 핵심 업데이트, 편집기 개선, 노드 업데이트 및 버그 수정이 포함되어 있습니다.

### AI 도구에 대한 부분 실행

n8n에서 AI 에이전트를 더 쉽게 빌드하고 반복할 수 있도록 만들었습니다. 이제 전체 에이전트 워크플로우를 실행하지 않고도 특정 도구를 실행하고 테스트할 수 있습니다.

부분 실행은 에이전트 논리의 일부를 구체화하거나 문제를 해결할 때 특히 유용합니다. 전체 에이전트 실행을 트리거하지 않고도 변경 사항을 점진적으로 테스트할 수 있으므로 불필요한 AI 호출, 토큰 사용량 및 다운스트림 활동을 줄일 수 있습니다. 이렇게 하면 복잡하거나 다단계 AI 워크플로우로 작업할 때 반복이 더 빠르고 비용 효율적이며 더 정확해집니다.

AI 도구에 대한 부분 실행은 이제 모든 도구에서 사용할 수 있으므로 n8n에서 AI 에이전트를 더 쉽게 빌드, 테스트 및 미세 조정할 수 있습니다.

<br>
<video src="/_video/release-notes/AI-agent-partial-execution.mp4" controls width="100%"></video>
<br>

**방법:**

이 기능을 사용하려면 다음 중 하나를 수행할 수 있습니다.

- 캔버스 보기에서 직접 실행하려는 도구의 **재생** 버튼을 클릭합니다.
- 도구의 **노드 세부 정보 보기**를 열고 **"단계 테스트"**를 선택하여 거기에서 실행합니다.

이전에 워크플로우를 실행한 경우 입력 및 출력이 마지막 실행의 데이터로 미리 채워집니다. 테스트를 실행하기 전에 매개변수를 수동으로 채울 수 있는 팝업 양식이 열립니다.

### 확장된 로그 보기

워크플로우가 복잡해지면 디버깅이... 클릭이 많아질 수 있습니다. 확장된 **로그 보기**가 필요한 이유입니다. 이제 노드 세부 정보 보기 사이를 오가지 않고도 실행을 추적하고 문제를 해결하며 전체 워크플로우의 동작을 이해할 수 있는 더 명확한 경로를 얻을 수 있습니다. 

이 업데이트는 캔버스 하단에 통합되고 항상 액세스할 수 있는 패널을 제공하여 실행되는 각 단계를 보여줍니다. 루프, 하위 워크플로우 또는 AI 에이전트로 작업하든, 실행된 모든 항목을 실행 순서대로 구조화된 보기로 볼 수 있으며 입력, 출력 및 상태 정보가 필요한 곳에 바로 표시됩니다.

더 깊이 파고들고 싶을 때 노드 세부 정보로 이동하거나 모든 단계를 통해 단일 항목을 따라갈 수 있습니다. 실시간 강조 표시는 현재 실행 중이거나 실패한 노드를 보여주며, 모든 워크플로우의 총 실행 시간과 AI 워크플로우의 토큰 사용량을 확인하여 성능을 모니터링할 수 있습니다. 여러 화면에서 디버깅하는 경우 로그를 팝아웃하여 원하는 곳으로 드래그하기만 하면 됩니다.

⚙️**기능**

- 열거나 축소할 수 있는 캔버스 하단에 **로그 보기**를 추가합니다. (워크플로우에서 사용하는 경우 채팅도 여기에 표시됩니다).
- 하위 워크플로우의 확장된 보기를 포함하여 실행된 순서대로 **계층적 노드 목록**을 표시합니다.
- **계층 구조에서 노드를 클릭**하여 입력 및 출력을 직접 미리 보거나 링크를 사용하여 전체 노드 세부 정보 보기로 이동할 수 있습니다.
- 입력 및 출력 데이터를 켜고 끄는 기능을 제공합니다.
- 각 노드를 **실행될 때 실시간으로 강조 표시**하여 시작, 완료 또는 실패 시점을 보여줍니다.
- 유사한 방식으로 과거 실행 데이터를 탐색하기 위한 **실행 기록** 보기를 포함합니다.
- 총 실행 시간 및 총 AI 토큰 사용량(AI 지원 워크플로우의 경우)과 같은 **롤업 통계**를 표시합니다.
- 로그를 부동 창으로 열기 위한 **"팝아웃"** 버튼을 포함하여 디버깅하는 동안 다른 화면으로 드래그하는 데 적합합니다.

🛠️**방법**

확장된 로그 보기에 액세스하려면 캔버스 하단의 로그 표시줄을 클릭하십시오. 이 보기는 페이지 하단의 채팅 창을 열 때도 열립니다.

### 엔터프라이즈용 인사이트 개선

[인사이트](/insights.md) 출시 2주 후, 엔터프라이즈 사용자를 위해 설계된 몇 가지 개선 사항을 출시합니다.

- **확장된 시간 범위**. 이제 지난 24시간부터 최대 1년까지 다양한 기간에 걸쳐 인사이트를 필터링할 수 있습니다. 프로 사용자는 7일 및 14일 보기로 제한됩니다.  
- **시간별 세분성**. 시간별 세분성으로 지난 24시간의 프로덕션 실행을 드릴다운하여 워크플로우를 분석하고 문제를 신속하게 식별하는 것이 더 쉬워집니다.  

이러한 업데이트는 워크플로우 기록에 대한 더 깊은 가시성을 제공하여 장기간에 걸쳐 추세를 파악하고 더 정확한 보고를 통해 문제를 더 빨리 감지하는 데 도움이 됩니다.

<br> 
<figure markdown="span">
    ![인사이트 필터링](/_images/release-notes/Insights-drill-down.png)
    <figcaption>인사이트 필터링</figcaption>
</figure>
<br>

### 기여자

[Stamsy](https://github.com/Stamsy){:target=_blank .external-link}  

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.91.2

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.91.1...n8n@1.91.2){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-05-05

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.90.3

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.90.2...n8n@1.90.3){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-05-05

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.91.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.91.0...n8n@1.91.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-05-01

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.91.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.90.0...n8n@1.91.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-04-28

이 릴리스에는 핵심 업데이트, 편집기 개선, 노드 업데이트 및 버그 수정이 포함되어 있습니다.

### 캔버스에서 이동 경로 보기

캔버스에 **이동 경로 탐색**을 직접 추가하여 워크플로우의 상위 폴더로 빠르게 이동할 수 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.90.2

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.90.1...n8n@1.90.2){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-04-25

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.90.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.90.0...n8n@1.90.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-04-22

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.90.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.89.0...n8n@1.90.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-04-22

이 릴리스에는 핵심 업데이트, 편집기 업데이트, 노드 업데이트, 성능 개선 및 버그 수정이 포함되어 있습니다.

### 확장된 HTTP 요청 도구 기능
HTTP 요청 노드의 모든 기능을 AI 워크플로우의 HTTP 요청 도구에 도입했습니다. 즉, AI 에이전트는 이제 페이지 매김, 일괄 처리, 시간 초과, 리디렉션, 프록시 지원, 심지어 cURL 가져오기와 같은 모든 고급 구성 옵션에 액세스할 수 있습니다.

<br>
<video src="/_video/release-notes/http-request-tool.mp4" controls width="100%"></video>
<br>

이 업데이트에는 프롬프트의 컨텍스트에 따라 올바른 매개변수를 동적으로 생성하는 `$fromAI` 함수에 대한 지원도 포함되어 있어 API 호출이 더 스마트하고 빠르며 유연해졌습니다.

**방법:**

- 캔버스에서 AI 에이전트 노드를 엽니다.
- **‘+’ 아이콘**을 클릭하여 새 도구 연결을 추가합니다.
- **도구 패널**에서 HTTP **요청 도구**를 선택합니다.
- 일반적인 **HTTP 요청 노드**와 마찬가지로 고급 옵션을 포함하여 구성합니다.

👉 [HTTP 요청 도구](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.toolhttprequest.md) 구성에 대해 자세히 알아보십시오.


### 범위 지정 API 키
엔터프라이즈 플랜 사용자는 이제 각 키가 액세스할 수 있는 항목을 정확하게 제어하기 위해 특정 범위의 API 키를 만들 수 있습니다.

<figure markdown="span">
    ![범위 지정 API 키](/_images/release-notes/scoped-API-keys.png)
    <figcaption>범위 지정 API 키</figcaption>
</figure>

이전에는 API 키가 모든 엔드포인트에 대해 전체 읽기/쓰기 액세스 권한을 가졌습니다. 때로는 필요하지만 이 수준의 액세스는 대부분의 사용 사례에 과도하고 너무 강력할 수 있습니다.  범위 지정 API 키를 사용하면 서비스 또는 사용자가 실제로 필요한 리소스 및 작업에만 액세스를 제한할 수 있습니다.

**새로운 기능**

새 API 키를 만들 때 이제 다음을 수행할 수 있습니다.

- 키에 읽기, 쓰기 또는 두 가지 유형의 액세스 권한이 있는지 선택합니다.  
- 키가 상호 작용할 수 있는 리소스를 지정합니다.  

지원되는 범위는 다음과 같습니다.

- 변수 — 나열, 생성, 삭제  
- 보안 감사 — 보고서 생성  
- 프로젝트 — 나열, 생성, 업데이트, 삭제  
- 실행 — 나열, 읽기, 삭제  
- 자격 증명 — 나열, 생성, 업데이트, 삭제, 이동  
- 워크플로우 — 나열, 생성, 업데이트, 삭제, 이동, 태그 추가/제거  

범위 지정 API 키는 더 많은 제어 및 보안을 제공합니다. 필요한 항목에만 액세스를 제한하여 타사와 더 안전하게 작업하고 내부 API 사용을 더 쉽게 관리할 수 있습니다.

### 폴더에서 드래그 앤 드롭

폴더가 더 친숙해졌습니다. 이 릴리스에서는 이제 **워크플로우 및 폴더를 드래그 앤 드롭**할 수 있어 정리하기가 훨씬 쉬워졌습니다.

재구성해야 합니까? 워크플로우 또는 폴더를 선택하고 다른 폴더 또는 이동 경로 위치로 드래그하기만 하면 됩니다. 증가하는 워크플로우 모음을 관리할 때 큰 차이를 만드는 작은 변경 사항입니다.

<br>
<video src="/_video/release-notes/Drag-and-drop-folders.mp4" controls width="100%"></video>
<br>

📁 폴더는 모든 [등록된](/hosting/community-edition-features.md#registered-community-edition) 사용자가 사용할 수 있습니다. 지금 바로 작업 공간을 정리하고 인스턴스를 정리할 더 많은 기능을 곧 찾아보십시오!

### 기여자

[Zordrak](https://github.com/Zordrak){:target=_blank .external-link}  

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.89.2

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.89.1...n8n@1.89.2){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-04-16

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.89.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.89.0...n8n@1.89.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-04-15

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.89.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.88.0...n8n@1.89.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-04-14

이 릴리스에는 API 업데이트, 핵심 업데이트, 편집기 업데이트, 새 노드, 노드 업데이트 및 버그 수정이 포함되어 있습니다.

<div class="n8n-new-features" markdown> 

### 인사이트 

시간이 지남에 따라 워크플로우가 어떻게 수행되는지 모니터링하는 새로운 대시보드인 [인사이트](/insights.md)를 출시합니다. 관리자(및 소유자)에게 가장 중요한 워크플로우 메트릭에 대한 더 나은 가시성을 제공하고 잠재적인 문제 및 개선 사항을 해결하는 데 도움이 되도록 설계되었습니다. <br> 
<br>

이 첫 번째 릴리스에서는 요약 배너, 인사이트 대시보드 및 실행당 절약된 시간을 소개합니다. <br> <br>

#### 1. 요약 배너
개요 페이지의 새 배너는 인스턴스 관리자 및 소유자에게 지난 7일 동안의 주요 메트릭에 대한 조감도를 제공합니다.

<figure markdown="span">
    ![요약 배너](/_images/release-notes/Insights-summary-banner.png)
    <figcaption>인사이트 요약 배너</figcaption>
</figure>

사용 가능한 메트릭:

- 총 프로덕션 실행
- 총 실패한 실행
- 실패율
- 모든 워크플로우의 평균 런타임
- 예상 절약 시간

이 개요는 한 눈에 워크플로우 활동을 파악하는 데 도움이 되도록 설계되었습니다. 모든 플랜 및 에디션에서 사용할 수 있습니다. <br> <br>

#### 2. 인사이트 대시보드
프로 및 엔터프라이즈 플랜에서는 새 대시보드가 워크플로우 성능 및 활동에 대한 더 깊은 보기를 제공합니다. 

<figure markdown="span">
    ![인사이트 대시보드](/_images/release-notes/Insights-dashboard.png)
    <figcaption>인사이트 대시보드</figcaption>
</figure>

대시보드에는 다음이 포함됩니다.

- 성공 및 실패한 실행 비교를 포함한 시간 경과에 따른 총 프로덕션 실행
- 주요 메트릭의 워크플로우별 분석
- 사용량 또는 동작의 변화를 파악하는 데 도움이 되는 이전 기간과의 비교
- 시간 경과에 따른 런타임 평균 및 실패율

#### 3. 실행당 절약된 시간
워크플로우 설정 내에서 이제 모든 워크플로우에 "실행당 절약된 시간" 값을 할당할 수 있습니다. 이를 통해 워크플로우의 영향을 추적하고 다른 팀 및 이해 관계자와 시각적으로 더 쉽게 공유할 수 있습니다.<br><br>

이것은 인사이트의 시작에 불과합니다. 다음 단계에서는 더 고급 필터링 및 비교, 사용자 지정 날짜 범위 및 추가 모니터링 기능을 도입할 것입니다. 

</div>

### 노드 업데이트
- Salesforce 노드에 대한 자격 증명 확인을 추가했습니다.
- AI 에이전트용 도구로 SearXNG를 추가했습니다.

이제 하위 폴더 내에서 검색할 수 있으므로 모든 폴더 수준에서 워크플로우를 더 쉽게 찾을 수 있습니다. 검색 창에 입력하고 이동하기만 하면 됩니다. 

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.88.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.87.0...n8n@1.88.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-04-10

이 릴리스에는 새로운 기능, 새로운 노드, 성능 개선 및 버그 수정이 포함되어 있습니다.

<div class="n8n-new-features" markdown> 


### 모델 컨텍스트 프로토콜(MCP) 노드
MCP는 Claude, ChatGPT 또는 Cursor와 같은 LLM이 도구와 상호 작용하거나 에이전트에 대한 데이터를 통합하는 방법을 표준화하는 것을 목표로 합니다. 기존 또는 신규 공급업체 모두 MCP를 에이전트 시스템을 구축하는 표준 방식으로 채택하고 있습니다. 자체 앱을 서버로 노출하여 모델에 기능을 도구로 제공하거나 자체 시스템 외부의 도구를 호출할 수 있는 클라이언트로 제공하는 쉬운 방법입니다. <br>

아직 개발 초기 단계이지만 새로운 MCP 노드에 대한 액세스 권한을 부여하고자 합니다. 이를 통해 귀하의 요구 사항을 더 잘 이해하고 더 빠른 일반 솔루션으로 수렴할 수 있습니다. <br> 

두 개의 새로운 노드를 추가하고 있습니다. 

- 모든 워크플로우에 대한 MCP [서버 트리거](/integrations/builtin/core-nodes/n8n-nodes-langchain.mcptrigger.md)  
- AI 에이전트에 대한 MCP [클라이언트 도구](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.toolmcp.md)  

MCP 서버 트리거는 n8n을 MCP 서버로 전환하여 n8n 외부에서 실행되는 모델에 n8n 도구를 제공합니다. n8n 인스턴스에서 여러 MCP 서버를 실행할 수 있습니다. MCP 클라이언트 도구는 LLM 및 기타 지능형 에이전트를 단일 인터페이스를 통해 모든 MCP 지원 서비스에 연결합니다. <br>

DevRel 팀의 Max가 시작하는 데 도움이 되는 공식 연습을 만들었습니다. 

<br>

[![스튜디오](/_images/release-notes/MCP-YouTube-thumb.jpg)](https://youtu.be/45WPU7P-1QQ?feature=shared)
<figure markdown="span">
    <figcaption>[스튜디오 업데이트 #04](https://youtu.be/45WPU7P-1QQ?feature=shared)</figcaption>
</figure>


### MCP 서버 트리거
MCP 서버 트리거는 n8n을 MCP 서버로 전환하여 n8n 외부에서 실행되는 모델에 n8n 도구를 제공합니다. 노드는 MCP 클라이언트를 위한 n8n의 진입점 역할을 합니다. MCP 클라이언트가 n8n 도구에 액세스하기 위해 상호 작용할 수 있는 URL을 노출하여 작동합니다. 즉, n8n 워크플로우 및 통합을 이제 다른 곳에서 실행되는 모델에서 사용할 수 있습니다. 아주 깔끔합니다. 

<figure markdown="span">
    ![MCP 서버 트리거](/_images/release-notes/MCP-Server-Trigger.png)
    <figcaption>MCP 서버 트리거</figcaption>
</figure>

[MCP 서버 트리거 문서 살펴보기](/integrations/builtin/core-nodes/n8n-nodes-langchain.mcptrigger.md)

### MCP 클라이언트 도구
MCP 클라이언트 도구 노드는 MCP 클라이언트이므로 외부 MCP 서버에서 노출하는 도구를 사용할 수 있습니다. MCP 클라이언트 도구 노드를 모델에 연결하여 n8n 에이전트로 외부 도구를 호출할 수 있습니다. 이 점에서 AI 에이전트와 함께 n8n 도구를 사용하는 것과 유사합니다. 한 가지 장점은 MCP 클라이언트 도구가 MCP 서버의 여러 도구에 한 번에 액세스할 수 있어 캔버스를 더 깨끗하고 이해하기 쉽게 유지할 수 있다는 것입니다. 

<figure markdown="span">
    ![MCP 클라이언트 도구](/_images/release-notes/MCP-Client-Tool.png)
    <figcaption>MCP 클라이언트 도구</figcaption>
</figure>

[MCP 클라이언트 도구 문서 살펴보기](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.toolmcp.md)

</div>

### 노드 업데이트

- Azure Cosmos DB용 노드 추가  
- Milvus 벡터 저장소용 노드 추가  
- 이메일 트리거(IMAP) 노드 업데이트  

### 기여자

[adina-hub](https://github.com/adina-hub){:target=_blank .external-link}  
[umanamente](https://github.com/umanamente){:target=_blank .external-link}  

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.87.2

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.87.1...n8n@1.87.2){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-04-09

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.86.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.86.0...n8n@1.86.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-04-09

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.87.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.87.0...n8n@1.87.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-04-08

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.87.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.86.0...n8n@1.87.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-04-07

이 릴리스에는 새 노드, 노드 업데이트, API 업데이트, 핵심 업데이트, 편집기 업데이트 및 버그 수정이 포함되어 있습니다.

### 기여자

[cesars-gh](https://github.com/cesars-gh){:target=_blank .external-link}  
[Stamsy](https://github.com/Stamsy){:target=_blank .external-link}  
[Pash10g](https://github.com/Pash10g){:target=_blank .external-link}  

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.86.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.85.0...n8n@1.86.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-03-31

이 릴리스에는 API 업데이트, 핵심 업데이트, 편집기 개선, 노드 업데이트 및 버그 수정이 포함되어 있습니다.

### 기여자

[Aijeyomah](https://github.com/Aijeyomah){:target=_blank .external-link}  
[ownerer](https://github.com/ownerer){:target=_blank .external-link}  
[ulevitsky](https://github.com/ulevitsky){:target=_blank .external-link}  

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.85.4

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.85.3...n8n@1.85.4){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-03-27

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.84.3

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.84.2...n8n@1.84.3){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-03-27

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.84.2

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.84.1...n8n@1.84.2){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-03-26

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.85.3

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.85.2...n8n@1.85.3){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-03-26

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.85.2

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.85.1...n8n@1.85.2){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-03-25

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.85.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.85.0...n8n@1.85.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-03-25

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.85.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.84.0...n8n@1.85.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-03-24

이 릴리스에는 새 노드, 새 자격 증명, 핵심 업데이트, 편집기 업데이트, 노드 업데이트 및 버그 수정이 포함되어 있습니다.

### 폴더
폴더에 대해 무엇을 말할 수 있을까요? 글쎄요, 거의 모든 것을 분류하는 데 매우 편리하며 마침내 n8n 워크플로우에서 사용할 수 있습니다. 무제한 폴더 및 중첩 폴더로 작업 공간을 정리하십시오. 폴더 내에서 워크플로우를 검색하십시오. n8n 인스턴스를 보다 효과적으로 구성하는 방법 중 하나입니다.  

**사용 방법:** 

개인 공간 또는 프로젝트 내에서 폴더를 만들고 관리합니다. 폴더 내에서 워크플로우를 만들 수도 있습니다. 폴더를 활성화하려면 인스턴스를 다시 시작해야 할 수 있습니다.

<figure markdown="span">
    ![폴더](/_images/release-notes/Folders.png
)
    <figcaption>폴더입니다.</figcaption>
</figure>
<br>

폴더는 모든 [등록된](/hosting/community-edition-features.md#registered-community-edition) 사용자가 사용할 수 있으므로 지금 바로 작업 공간을 정리하고 드래그 앤 드롭과 같은 더 많은 기능을 곧 찾아보십시오.

### 양식 트리거 노드 개선

최근 양식 트리거 노드 업데이트로 비즈니스 솔루션을 구축하는 데 더 강력한 도구가 되었습니다. 이러한 개선 사항은 더 많은 유연성과 사용자 지정을 제공하여 팀이 시각적으로 매력적이고 기능이 뛰어난 양식으로 워크플로우를 만들 수 있도록 합니다.

- **HTML 사용자 지정:** 더 풍부한 사용자 경험을 위해 포함된 이미지 및 비디오를 포함하여 양식에 사용자 지정 HTML을 추가합니다.  
- **사용자 지정 CSS 지원**: 사용자 대면 구성 요소에 사용자 지정 스타일을 적용하여 양식을 브랜드의 모양과 느낌에 맞게 조정합니다. 원활한 시각적 정체성을 위해 글꼴, 색상 및 간격을 조정합니다.
- **양식 미리보기:** 소셜 미디어 또는 메시징 앱에서 공유할 때 양식의 설명과 제목이 양식 미리보기로 가져와 더 세련된 모양을 제공합니다.  
- **숨겨진 필드:** 쿼리 매개변수를 사용하여 숨겨진 필드를 추가하여 사용자에게 노출하지 않고 추천 소스와 같은 데이터를 전달할 수 있습니다.  
- **새로운 응답 옵션:** 텍스트, HTML 또는 다운로드 가능한 파일(바이너리 형식)을 포함한 여러 가지 방법으로 사용자 제출에 응답합니다. 이를 통해 양식은 풍부한 웹 페이지를 표시하거나 동적으로 생성된 송장 또는 개인화된 인증서와 같은 디지털 자산을 제공할 수 있습니다.  

<figure markdown="span">
    ![사용자 지정 CSS가 적용된 양식](/_images/release-notes/Forms_with_custom_CSS_and_HTML.png)
    <figcaption>사용자 지정 CSS가 적용된 양식</figcaption>
</figure>
<br>

이러한 개선 사항은 양식 트리거 노드를 단순한 워크플로우 트리거를 넘어 데이터 수집 및 주문 처리에서 사용자 지정 콘텐츠 생성에 이르기까지 사용 사례를 해결하는 강력한 도구로 변환합니다.

### 기여자

[Fank](https://github.com/Fank){:target=_blank .external-link}  

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.84.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.84.0...n8n@1.84.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-03-18

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.84.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.83.0...n8n@1.84.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-03-17

이 릴리스에는 새 노드, 노드 업데이트, 편집기 업데이트 및 버그 수정이 포함되어 있습니다.

### 기여자

[Pash10g](https://github.com/Pash10g){:target=_blank .external-link}  

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.83.2

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.83.1...n8n@1.83.2){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-03-14

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.82.4

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.82.3...n8n@1.82.4){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-03-14

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.82.3

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.82.2...n8n@1.82.3){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-03-13

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.83.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.83.0...n8n@1.83.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-03-12

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.83.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.82.0...n8n@1.83.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-03-12

이 릴리스에는 버그 수정 및 편집기 업데이트가 포함되어 있습니다.

### 스키마 미리보기

스키마 미리보기를 사용하면 노드를 실행하거나 자격 증명을 추가하지 않고도 노드의 예상 출력을 보고 작업할 수 있으므로 빌드하는 동안 흐름을 유지할 수 있습니다.

- **예상 노드 출력을 즉시 확인합니다.** 100개 이상의 노드에 대한 스키마를 보고 추가 단계 없이 효율적으로 워크플로우를 설계하는 데 도움이 됩니다.  
- **먼저 워크플로우 논리를 정의하고 나중에 자격 증명을 처리합니다.** 자격 증명 설정에 방해받지 않고 종단 간 워크플로우를 빌드합니다.  
- **빌드 시 원치 않는 실행을 방지합니다.** 노드를 실행하지 않고 출력을 보고 불필요한 API 호출, 원치 않는 데이터 변경 또는 잠재적인 타사 서비스 비용을 방지합니다.  

**사용 방법:**

- 스키마 미리보기 지원이 포함된 노드를 워크플로우에 추가합니다.
- 시퀀스의 다음 노드를 엽니다. 스키마 미리보기 데이터는 일반적으로 스키마 보기에서 찾을 수 있는 노드 편집기에 나타납니다.
- 다른 스키마 데이터와 마찬가지로 스키마 미리보기 필드를 사용합니다. 필요에 따라 매개변수 및 설정으로 드래그 앤 드롭합니다.

<br>
<video src="/_video/release-notes/Schema_preview.mp4" controls width="100%"></video>
<br>

워크플로우를 프로덕션에 적용하기 전에 필요한 자격 증명을 추가하는 것을 잊지 마십시오.

### 기여자

[pemontto](https://github.com/pemontto){:target=_blank .external-link}  
[Haru922](https://github.com/Haru922){:target=_blank .external-link}  

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.82.2

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.82.1...n8n@1.82.2){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-03-12

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.82.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.82.0...n8n@1.82.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-03-04

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.82.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.81.0...n8n@1.82.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-03-03

이 릴리스에는 핵심 업데이트, 편집기 업데이트, 새 노드, 노드 업데이트, 새 자격 증명, 자격 증명 업데이트 및 버그 수정이 포함되어 있습니다.

### 정리
정리는 노드를 즉시 정렬하고, 스티커를 중앙에 배치하고, 연결을 풀고, 워크플로우에 구조를 제공합니다. 워크플로우를 공유할 준비를 하거나 가독성을 향상시키려는 경우 이 기능은 시간을 절약하고 논리를 더 쉽게 따를 수 있도록 합니다. 깨끗하고 잘 정리된 워크플로우는 보기 좋을 뿐만 아니라 이해하기도 더 빠릅니다.

**방법:** 

정리하려는 워크플로우를 연 다음 다음 옵션 중 하나를 선택합니다.

- 캔버스 왼쪽 하단 모서리에 있는 **정리** 버튼을 클릭합니다(빗자루 🧹처럼 보입니다).
- 키보드에서 **Shift + Alt + T**를 누릅니다.
- 캔버스 아무 곳이나 마우스 오른쪽 버튼으로 클릭하고 **워크플로우 정리**를 선택합니다.

워크플로우의 일부만 정리하시겠습니까? 먼저 정리하려는 특정 노드를 선택하십시오. 정리는 해당 노드와 그 뒤에 있는 스티커만 조정합니다.

<br>
<video src="/_video/release-notes/tidy_up.mp4" controls width="100%"></video>
<br>


### 다중 API 키
n8n은 이제 다중 API 키를 지원하므로 사용자는 다른 워크플로우 또는 통합에 대해 별도의 키를 생성하고 관리할 수 있습니다. 이렇게 하면 더 쉬운 키 순환 및 자격 증명 격리를 통해 보안이 향상됩니다. 향후 업데이트에서는 더 세분화된 제어 기능이 도입될 예정입니다. <br>

<figure markdown="span">
    ![다중 API 키](/_images/release-notes/Multiple-API-keys.png)
    <figcaption>다중 API 키</figcaption>
</figure>
<br>

### 기여자

[Rostammahabadi](https://github.com/Rostammahabadi){:target=_blank .external-link}  
[Lanhild](https://github.com/Lanhild){:target=_blank .external-link}  
[matthiez](https://github.com/matthiez){:target=_blank .external-link}  
[feelgood-interface](https://github.com/feelgood-interface){:target=_blank .external-link}  
[adina-hub](https://github.com/adina-hub){:target=_blank .external-link}  

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.81.4

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.81.3...n8n@1.81.4){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-03-03

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.81.3

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.81.2...n8n@1.81.3){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-03-03

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.81.2

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.81.1...n8n@1.81.2){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-28

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.80.5

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.80.4...n8n@1.80.5){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-28

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.80.4

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.80.3...n8n@1.80.4){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-27

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.81.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.81.0...n8n@1.81.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-27

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.81.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.80.0...n8n@1.81.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-24

이 릴리스에는 버그 수정, 핵심 업데이트, 편집기 개선 및 노드 업데이트가 포함되어 있습니다.

### 개선된 부분 실행
부분 실행을 위한 새로운 실행 엔진은 빌더에서 워크플로우의 일부를 테스트하는 것이 프로덕션 동작을 거의 미러링하도록 보장합니다. 이렇게 하면 특히 복잡한 워크플로우의 경우 업데이트된 실행 데이터로 반복하는 것이 더 빠르고 안정적입니다.

이전에는 사용자가 빌더에서 워크플로우의 일부를 테스트했지만 프로덕션 동작을 일관되게 반영하지 않아 개발 중에 예기치 않은 결과가 발생했습니다.

이 업데이트는 빌더의 워크플로우 실행을 프로덕션 동작과 일치시킵니다.

다음은 루프에 대한 예입니다.

이전
<br>

<video src="/_video/release-notes/Partial-execution-loop-before.mp4" controls width="100%"></video>
<br>
이후
<br>

<video src="/_video/release-notes/Partial-execution-loop-after.mp4" controls width="100%"></video>


전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.80.3

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.80.2...n8n@1.80.3){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-21

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.79.4

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.79.3...n8n@1.79.4){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-21

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.80.2

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.80.1...n8n@1.80.2){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-21

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.79.3

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.79.2...n8n@1.79.3){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-21

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.80.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.80.0...n8n@1.80.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-20

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.79.2

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.79.1...n8n@1.79.2){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-20

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.80.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.79.0...n8n@1.80.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-17

이 릴리스에는 버그 수정 및 편집기 개선 사항이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.75.3

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.75.2...n8n@1.75.3){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-17

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.74.4

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.74.3...n8n@1.74.4){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-17

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.79.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.79.0...n8n@1.79.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-15

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.78.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.78.0...n8n@1.78.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-15

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.77.4

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.77.3...n8n@1.77.4){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-15

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.76.4

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.76.3...n8n@1.76.4){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-15

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.79.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.77.0...n8n@1.78.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-12

이 릴리스에는 새로운 기능, 노드 업데이트 및 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.77.3

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.77.2...n8n@1.77.3){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-06

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.78.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.77.0...n8n@1.78.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-05

이 릴리스에는 새로운 기능, 노드 업데이트 및 버그 수정이 포함되어 있습니다.

### 기여자

[mocanew](https://github.com/mocanew){:target=_blank .external-link}  
[Timtendo12](https://github.com/Timtendo12){:target=_blank .external-link}  

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.77.2

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.77.1...n8n@1.77.2){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-04

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.76.3

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.76.2...n8n@1.76.3){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-04

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.77.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.77.0...n8n@1.77.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-03

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.76.2

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.76.1...n8n@1.76.2){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-02-03

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.77.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.76.0...n8n@1.77.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-01-29

이 릴리스에는 새로운 기능, 편집기 업데이트, 새 노드, 새 자격 증명, 노드 업데이트 및 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.76.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.76.0...n8n@1.76.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-01-23

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.76.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.75.0...n8n@1.76.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-01-22

이 릴리스에는 새로운 기능, 편집기 업데이트, 새 자격 증명, 노드 개선 및 버그 수정이 포함되어 있습니다.

### 기여자

[Stamsy](https://github.com/Stamsy){:target=_blank .external-link}  
[GKdeVries](https://github.com/GKdeVries){:target=_blank .external-link}  

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.75.2

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.75.1...n8n@1.75.2){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-01-17

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.74.3

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.74.2...n8n@1.74.3){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-01-17

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.75.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.75.0...n8n@1.75.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-01-17

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.74.2

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.74.1...n8n@1.74.2){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-01-17

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.75.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.74.0...n8n@1.75.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-01-15

이 릴리스에는 버그 수정 및 편집기 업데이트가 포함되어 있습니다.

### 환경 간 일관성 향상
스테이징 및 프로덕션 인스턴스 간의 일관성을 향상시키는 새로운 UX 및 자동 변경 개선 사항을 추가했습니다.

이전에는 사용자가 다음과 같은 문제에 직면했습니다.  

- 변경 사항을 가져올 때 필요한 자격 증명 업데이트에 대한 가시성 부족  
- 삭제와 같은 변경 사항이 환경 전체에 항상 적용되지 않는 불완전한 동기화  
- 푸시 또는 풀되는 항목이 불분명하여 혼란스러운 커밋 프로세스  

다음과 같이 해결했습니다.

- 변경 사항을 가져올 때 필요한 자격 증명 업데이트를 명확하게 표시  
- 삭제 및 기타 수정 사항이 환경 전체에 올바르게 동기화되도록 보장  
- 푸시되는 항목에 대한 가시성을 향상시키기 위해 커밋 선택 개선  
<br>
<figure markdown="span">
    ![커밋 모달](/_images/release-notes/Commit-modal.png)
    <figcaption>커밋 모달</figcaption>
</figure>
<br>
<figure markdown="span">
    ![가져오기 알림](/_images/release-notes/Pull-notification.png)
    <figcaption>가져오기 알림</figcaption>
</figure>
<br>

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.74.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.74.0...n8n@1.74.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-01-09

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.74.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.73.0...n8n@1.74.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2025-01-08

이 릴리스에는 새로운 기능, 새 노드, 노드 업데이트, 성능 개선 및 버그 수정이 포함되어 있습니다.

<div class="n8n-new-features" markdown>

### 개선된 코드 노드 편집 환경
코드 노드에 수많은 새로운 도우미를 추가하여 코드 편집을 훨씬 빠르고 편안하게 만들었습니다. 다음을 얻을 수 있습니다.

- TypeScript 자동 완성  
- TypeScript 린팅  
- TypeScript 호버 팁  
- 검색 및 바꾸기  
- VSCode 키맵 기반의 새로운 키보드 단축키  
- prettier를 사용한 자동 서식 지정(Alt+Shift+F)  
- 새로 고침 후 접힌 영역 및 기록 기억  
- 다중 커서  
- JSDoc 유형을 사용하여 코드 노드에 함수 입력  
- 모든 코드 노드 모드에 대한 드래그 앤 드롭  
- 들여쓰기 마커  

웹 워커 아키텍처를 기반으로 구축하여 입력하는 동안 성능 저하를 겪지 않아도 됩니다. <br>
<br>
전체 그림을 보려면 Max와 Elias가 새로운 편집 환경에 대해 논의하고 시연하는 스튜디오 업데이트를 확인하십시오. 👇 <br>

[![스튜디오](/_images/release-notes/The_Studio_thumbnail_Code_node.jpg)](https://youtu.be/De1E58MPaMQ?t=645)
<figure markdown="span">
    <figcaption>[스튜디오 업데이트 #04](https://youtu.be/De1E58MPaMQ?t=645)</figcaption>
</figure>

</div>

### 새 노드: Microsoft Entra ID
Microsoft Entra ID(이전의 Microsoft Azure Active Directory 또는 Azure AD)는 클라우드 기반 ID 및 액세스 관리에 사용됩니다. [새 노드](/integrations/builtin/app-nodes/n8n-nodes-base.microsoftentra.md)는 사용자 및 그룹 생성, 가져오기, 업데이트 및 삭제, 그룹에 사용자 추가 및 제거를 포함하여 광범위한 Microsoft Entra ID 기능을 지원합니다. 

### 노드 업데이트

- [AI 에이전트](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.agent/index.md): 이제 벡터 저장소를 에이전트의 도구로 직접 사용할 수 있습니다.
- [코드](/code/builtin/overview.md): 수많은 새로운 속도 및 편의 기능, 자세한 내용은 위 참조  
- [Google Vertex Chat](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.lmchatgooglevertex.md): Google API 자격 증명에 대한 GCP 지역을 지정하는 옵션 추가  
- [HighLevel](/integrations/builtin/app-nodes/n8n-nodes-base.highlevel.md): 캘린더 항목 지원 추가  


사용 가능한 이모티콘 위에 사용자 지정 [프로젝트](/user-management/rbac/projects.md) 아이콘 선택기도 추가했습니다. 예쁘네요!

### 기여자

[igatanasov](https://github.com/igatanasov){:target=_blank .external-link}  
[Stamsy](https://github.com/Stamsy){:target=_blank .external-link}  
[feelgood-interface](https://github.com/feelgood-interface){:target=_blank .external-link}  

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.73.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.73.0...n8n@1.73.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2024-12-19

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.73.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.72.0...n8n@1.73.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2024-12-19

이 릴리스에는 노드 업데이트, 성능 개선 및 버그 수정이 포함되어 있습니다.

### 노드 업데이트

- [AI 에이전트](/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.agent/index.md): 채팅 트리거 옵션에 대한 설명 업데이트
- [Facebook Graph API](/integrations/builtin/app-nodes/n8n-nodes-base.facebookgraphapi.md): API v21.0으로 업데이트
- [Gmail](/integrations/builtin/app-nodes/n8n-nodes-base.gmail/index.md): `보내고 기다리기` 작업에 대한 두 가지 새로운 옵션 추가, 자유 텍스트 및 사용자 지정 양식  
- [선형 트리거](/integrations/builtin/trigger-nodes/n8n-nodes-base.lineartrigger.md): 관리자 범위 지원 추가  
- [MailerLite](/integrations/builtin/app-nodes/n8n-nodes-base.mailerlite.md): 이제 새 API 지원  
- [Slack](/integrations/builtin/app-nodes/n8n-nodes-base.slack.md):  `보내고 기다리기` 작업에 대한 두 가지 새로운 옵션 추가, 자유 텍스트 및 사용자 지정 양식  

[SolarWinds IPAM](/integrations/builtin/credentials/solarwindsipam.md) 및 [SolarWinds Observability](/integrations/builtin/credentials/solarwindsobservability.md)에 대한 자격 증명 지원도 추가했습니다. 

마지막으로, [노드 세부 정보 보기에서 스키마 보기 성능을 90% 향상](https://github.com/n8n-io/n8n/pull/12180)하고 매개변수에 드래그 앤 드롭 재정렬을 추가했습니다. 이는 [If](/integrations/builtin/core-nodes/n8n-nodes-base.if.md) 또는 [필드 편집](/integrations/builtin/core-nodes/n8n-nodes-base.set.md) 노드에서 매우 유용합니다. 

### 기여자

[CodeShakingSheep](https://github.com/CodeShakingSheep){:target=_blank .external-link}  
[mickaelandrieu](https://github.com/mickaelandrieu){:target=_blank .external-link}  
[Stamsy](https://github.com/Stamsy){:target=_blank .external-link}  
[pbdco](https://github.com/pbdco){:target=_blank .external-link}  

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.


## n8n@1.72.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.72.0...n8n@1.72.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2024-12-12





이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.71.3

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.71.2...n8n@1.71.3){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2024-12-12



이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.72.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.71.0...n8n@1.72.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2024-12-11

이 릴리스에는 노드 업데이트, 사용성 개선 및 버그 수정이 포함되어 있습니다.

### 노드 업데이트

- [AI 변환](/integrations/builtin/core-nodes/n8n-nodes-base.aitransform.md): `최대 컨텍스트 길이` 오류는 이제 감소된 페이로드 크기로 다시 시도합니다.
- [Redis](/integrations/builtin/app-nodes/n8n-nodes-base.redis.md): `실패 시 계속` 지원 추가

### 개선된 커밋 모달 

[환경](/source-control-environments/index.md)으로 작업할 때 커밋 모달에 필터 및 텍스트 검색을 추가했습니다. 이렇게 하면 더 많은 정보와 더 나은 가시성을 제공하여 커밋이 더 쉬워집니다. 환경은 엔터프라이즈 플랜에서 사용할 수 있습니다. 

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.71.2

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.71.1...n8n@1.71.2){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2024-12-10





이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.70.4

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.70.3...n8n@1.70.4){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2024-12-10



이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.71.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.71.0...n8n@1.71.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2024-12-06

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.70.3

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.70.2...n8n@1.70.3){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2024-12-05

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.71.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.70.2...n8n@1.71.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2024-12-04

이 릴리스에는 노드 업데이트, 성능 개선 및 버그 수정이 포함되어 있습니다.

<div class="n8n-new-features" markdown>

### 공개 베타 버전의 코드 노드용 작업 실행기
새로운 작업 실행기 시스템으로 코드 노드에 상당한 성능 업그레이드를 도입합니다. 이 개선 사항은 JavaScript 코드 실행을 별도의 프로세스로 이동하여 워크플로우 실행 속도를 향상시키면서 더 나은 격리를 추가합니다.

<figure markdown="span">
    ![작업 실행기 개요](/_images/hosting/configuration/task-runner-concept.png)
    <figcaption>작업 실행기 개요</figcaption>
</figure>

벤치마크에 따르면 코드 노드를 사용하는 워크플로우 실행이 초당 약 6회에서 35회로 최대 6배 향상되었습니다. 이러한 모든 개선 사항은 내부적으로 발생하며 코드 노드 경험은 그대로 유지됩니다.

작업 실행기는 두 가지 모드로 제공됩니다.

- 내부 모드(기본값): 시작하기에 적합하며 작업 실행기를 자식 프로세스로 자동 관리합니다.  
- 외부 모드: 최대 격리 및 보안이 필요한 고급 호스팅 시나리오용

현재 이 기능은 옵트인이며 [환경 변수](/hosting/configuration/environment-variables/task-runners.md)를 사용하여 활성화할 수 있습니다. 안정화되면 코드 노드의 기본 실행 방법이 됩니다.

오늘부터 작업 실행기를 사용하려면 [문서](/hosting/configuration/task-runners.md)를 확인하십시오.

</div>

### 노드 업데이트

- [AI 변환 노드](/integrations/builtin/core-nodes/n8n-nodes-base.aitransform.md): 데이터 변환을 위한 코드 생성 프롬프트를 개선했습니다.
- [코드 노드](/integrations/builtin/core-nodes/n8n-nodes-base.code/index.md): `pairedItem`이 없거나 자동으로 매핑할 수 없는 경우 경고를 추가했습니다.  

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.


## n8n@1.70.2

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.70.1...n8n@1.70.2){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2024-12-04

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.


## n8n@1.70.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.70.0...n8n@1.70.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2024-11-29

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.70.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.69.0...n8n@1.70.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2024-11-27

이 릴리스에는 노드 업데이트, 성능 개선 및 버그 수정이 포함되어 있습니다.

### 베타 버전의 새 캔버스
새 캔버스는 이제 모든 사용자의 기본 설정입니다. 상당한 성능 향상을 가져오고 편리한 미니맵을 추가해야 합니다. 아직 베타 버전이므로 세 점 메뉴로 이전 버전으로 되돌릴 수 있습니다.  

귀하의 피드백을 기다리겠습니다. 버그가 발생하면 새 캔버스 하단에 문제를 생성하는 편리한 버튼도 찾을 수 있습니다. 

### 노드 업데이트
- HTTP 요청 노드에 [Zabbix](/integrations/builtin/credentials/zabbix.md)에 대한 자격 증명 지원을 추가했습니다.  
- [Microsoft SharePoint](/integrations/builtin/credentials/microsoft.md)에 대한 새로운 OAuth2 자격 증명을 추가했습니다.
- [Slack 노드](/integrations/builtin/app-nodes/n8n-nodes-base.slack.md#operations)는 이제 `승인 보내기 및 대기` 작업을 사용할 때 승인 메시지에 마크다운을 사용합니다.

### 기여자

[feelgood-interface](https://github.com/feelgood-interface){:target=_blank .external-link}  
[adina-hub](https://github.com/adina-hub){:target=_blank .external-link}  

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.



## n8n@1.68.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.68.0...n8n@1.68.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2024-11-26

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.69.2

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.69.1...n8n@1.69.2){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2024-11-26




이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.



## n8n@1.69.1

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.69.0...n8n@1.69.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2024-11-25



이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.



## n8n@1.69.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.68.0...n8n@1.69.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2024-11-20



이 릴리스에는 새로운 기능, 노드 개선 및 버그 수정이 포함되어 있습니다.

### 하위 워크플로우 디버깅
상위 워크플로우에서 접근성을 개선하여 하위 워크플로우를 훨씬 쉽게 디버깅할 수 있도록 했습니다. 

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.68.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.67.1...n8n@1.68.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2024-11-13


이 릴리스에는 노드 업데이트, 성능 개선 및 많은 버그 수정이 포함되어 있습니다.

<div class="n8n-new-features" markdown>

#### 새로운 AI 에이전트 캔버스 채팅

캔버스에서 AI 에이전트에 대한 채팅 경험을 개선했습니다. 노드를 숨기는 모달 대신 깔끔하게 정리된 보기입니다. 이제 워크플로우를 테스트할 때 캔버스, 채팅 및 로그를 동시에 볼 수 있습니다. 
<br /><br />

<video src="/_video/release-notes/AI-chat-on-canvas.mp4" controls width="100%"></video>
<br /><br />

</div>

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.67.1
이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.67.0...n8n@1.67.1){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2024-11-07

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.67.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.66.0...n8n@1.67.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2024-11-06

이 릴리스에는 노드 업데이트 및 버그 수정이 포함되어 있습니다.

### 노드 업데이트

- [AI 변환](/integrations/builtin/core-nodes/n8n-nodes-base.aitransform.md): 사용성 개선  
- [Anthropic 채팅 모델 노드](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.lmchatanthropic.md): Haiku 3.5 지원 추가  
- [파일로 변환](/integrations/builtin/core-nodes/n8n-nodes-base.converttofile.md): CSV에 쓰기 위한 구분 기호 옵션 추가  
- [Gmail 트리거](/integrations/builtin/trigger-nodes/n8n-nodes-base.gmailtrigger/index.md): 초안 메시지를 필터링하는 옵션 추가  
- [Intercom](/integrations/builtin/app-nodes/n8n-nodes-base.intercom.md): 이제 HTTP 요청 노드에서 자격 증명을 사용할 수 있습니다.  
- [Rapid7 InsightVM](/integrations/builtin/credentials/rapid7insightvm.md): 자격 증명 지원 추가  

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.66.0

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.65.2...n8n@1.66.0){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2024-10-31

이 릴리스에는 성능 개선, 노드 업데이트 및 버그 수정이 포함되어 있습니다.

### 노드 업데이트

- [Anthropic 채팅 모델](/integrations/builtin/cluster-nodes/sub-nodes/n8n-nodes-langchain.lmchatanthropic.md): claude-3-5-sonnet-20241022 지원 추가  

프로젝트 및 워크플로우 소유권이 표시되는 방식을 업데이트하여 더 쉽게 이해하고 탐색할 수 있도록 했습니다. 

부분 실행의 성능 논리를 더욱 개선하여 더 부드럽고 즐거운 빌드 경험을 제공합니다. 

### 새로운 n8n 캔버스 알파
새로운 캔버스의 알파 버전을 활성화했습니다. 캔버스는 n8n 편집기의 ‘그림판’이며, 전체 재작업을 진행 중입니다. 귀하의 피드백과 테스트는 개선에 도움이 될 것입니다. 
[커뮤니티 포럼에서 자세히 알아보십시오](https://community.n8n.io/t/help-us-test-the-new-n8n-canvas-alpha/60070). 


전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.65.2

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.65.1...n8n@1.65.2){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2024-10-28

이 릴리스에는 버그 수정이 포함되어 있습니다.

전체 릴리스 세부 정보는 GitHub의 [릴리스](https://github.com/n8n-io/n8n/releases){:target=_blank .external-link}를 참조하십시오.

## n8n@1.64.3

이 버전에 대한 [커밋](https://github.com/n8n-io/n8n/compare/n8n@1.64.2...n8n@1.64.3){:target=_blank .external-link} 보기.<br />
**릴리스 날짜:** 2024-10-25
