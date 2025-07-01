---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 커뮤니티 에디션 기능
description: 커뮤니티 에디션과 다른 유료 플랜 간의 사용 가능한 기능 차이.
contentType: explanation
tags:
  - 커뮤니티 에디션
  - 엔터프라이즈 에디션
hide:
  - tags
---

# 커뮤니티 에디션 기능

커뮤니티 에디션에는 여기에 나열된 기능을 제외하고 거의 모든 n8n 기능 세트가 포함되어 있습니다.

커뮤니티 에디션에는 다음 기능이 포함되어 있지 않습니다.

- [사용자 지정 변수](/code/variables.md)
- [환경](/source-control-environments/index.md)
- [외부 비밀](/external-secrets.md)
- [바이너리 데이터용 외부 저장소](/hosting/scaling/external-storage.md)
- [로그 스트리밍](/log-streaming.md) ([로깅](/hosting/logging-monitoring/logging.md)은 포함됨)
- [다중 메인 모드](/hosting/scaling/queue-mode.md#multi-main-setup) ([큐 모드](/hosting/scaling/queue-mode.md)는 포함됨)
- [프로젝트](/user-management/rbac/projects.md)
- SSO ([SAML](/hosting/securing/set-up-sso.md), [LDAP](/user-management/ldap.md))
- 공유 ([워크플로우](/workflows/sharing.md), [자격 증명](/credentials/credential-sharing.md)) (인스턴스 소유자와 생성한 사용자만 워크플로우 및 자격 증명에 액세스할 수 있음)
- [Git을 사용한 버전 관리](/source-control-environments/index.md)
- [워크플로우 기록](/workflows/history.md) (커뮤니티 에디션으로 [등록](#registered-community-edition)하면 하루 분량의 워크플로우 기록을 얻을 수 있음)

이러한 기능은 자체 호스팅 엔터프라이즈 에디션을 포함한 엔터프라이즈 클라우드 플랜에서 사용할 수 있습니다. 이러한 기능 중 일부는 스타터 및 프로 클라우드 플랜에서 사용할 수 있습니다.

참고로 [가격 책정](https://n8n.io/pricing/){:target=_blank .external-link}을 참조하십시오.

## 등록된 커뮤니티 에디션

n8n 커뮤니티 에디션을 등록하여 추가 기능을 잠금 해제할 수 있습니다. 이메일로 등록하고 라이선스 키를 받습니다.

등록하면 커뮤니티 에디션에 대해 다음 기능이 잠금 해제됩니다.

* [폴더](/release-notes.md#folders): 워크플로우를 깔끔한 폴더로 정리
* [편집기에서 디버그](/workflows/executions/debug.md): 워크플로우 작업 시 실행 데이터 복사 및 [고정](/glossary.md#data-pinning-n8n)
* 하루 분량의 [워크플로우 기록](/workflows/history.md): 이전 워크플로우 버전으로 되돌릴 수 있는 24시간의 워크플로우 기록
* [사용자 지정 실행 데이터](/workflows/executions/custom-executions-data.md): 실행 메타데이터 저장, 찾기 및 주석 달기

새 커뮤니티 에디션 인스턴스를 등록하려면 초기 계정 생성 중에 옵션을 선택하십시오.

기존 커뮤니티 에디션 인스턴스를 등록하려면:

1. 왼쪽 하단 모서리에 있는 **세 점 아이콘** <span class="inline-image">![세 점 아이콘](/_images/common-icons/three-dots-horizontal.png){.off-glb}</span>을 선택합니다.
2. **설정**을 선택한 다음 **사용량 및 플랜**을 선택합니다.
3. **잠금 해제**를 선택하여 이메일을 입력한 다음 **무료 라이선스 키 보내기**를 선택합니다.
4. 입력한 계정의 이메일을 확인합니다.

라이선스 키가 있으면 라이선스 이메일의 버튼을 클릭하거나 **옵션 > 설정 > 사용량 및 플랜**을 방문하여 **활성화 키 입력**을 선택하여 활성화합니다.

활성화되면 라이선스는 만료되지 않습니다. 향후 잠금 해제된 기능을 변경할 수 있습니다. 이는 이전에 잠금 해제된 기능에 영향을 미치지 않습니다.
