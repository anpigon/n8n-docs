#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
description: 사용자 관리를 위한 자체 호스팅 n8n 구성
contentType: howto
---

# 사용자 관리를 위한 자체 호스팅 n8n 구성

n8n의 사용자 관리를 통해 n8n 인스턴스에서 작업할 사람들을 초대할 수 있습니다.

이 문서에서는 사용자 관리를 지원하도록 n8n 인스턴스를 구성하는 방법과 사용자 초대를 시작하는 단계를 설명합니다.

다음을 포함한 사용에 대한 자세한 내용은 기본 [사용자 관리](/user-management/index.md) 가이드를 참조하십시오.

* [사용자 관리](/user-management/manage-users.md)
* [계정 유형](/user-management/account-types.md)
* [모범 사례](/user-management/best-practices.md)

LDAP 설정 정보는 [LDAP](/user-management/ldap.md)를 참조하십시오.

SAML 설정 정보는 [SAML](/user-management/saml/index.md)을 참조하십시오.

/// note | 기본 인증 및 JWT 제거됨
n8n은 버전 1.0에서 기본 인증 및 JWT에 대한 지원을 제거했습니다.
///
## 설정

n8n에서 사용자 관리를 설정하는 데는 세 단계가 있습니다.

1. SMTP 서버를 사용하도록 n8n 인스턴스를 구성합니다.
2. n8n을 시작하고 앱의 설정 단계를 따릅니다.
3. 사용자를 초대합니다.

### 1단계: SMTP

n8n은 사용자 초대 및 암호 재설정을 위해 SMTP 서버를 설정하는 것을 권장합니다.

/// note | 0.210.1부터 선택 사항
버전 0.210.1부터 이 단계는 선택 사항입니다. SMTP를 설정하는 대신 초대 링크를 수동으로 복사하여 보낼 수 있습니다. 이 단계를 건너뛰면 사용자는 암호를 재설정할 수 없습니다.
///
SMTP 공급자로부터 다음 정보를 얻으십시오.

* 서버 이름
* SMTP 사용자 이름
* SMTP 암호
* SMTP 보낸 사람 이름

n8n으로 SMTP를 설정하려면 n8n 인스턴스에 대한 SMTP 환경 변수를 구성하십시오. 환경 변수 설정 방법에 대한 정보는 [구성](/hosting/configuration/configuration-methods.md)을 참조하십시오.
<!-- vale off -->
| 변수 | 유형 | 설명 | 필수? |
| -------- | ---- | ----------- | --------- |
| `N8N_EMAIL_MODE` | 문자열 | `smtp` | 필수 |
| `N8N_SMTP_HOST` | 문자열 | _your_SMTP_server_name_ | 필수 |
| `N8N_SMTP_PORT` | 숫자 | _your_SMTP_server_port_ 기본값은 `465`입니다.| 선택 사항 |
| `N8N_SMTP_USER` | 문자열 | _your_SMTP_username_ | 선택 사항 |
| `N8N_SMTP_PASS` | 문자열 | _your_SMTP_password_ | 선택 사항 |
| `N8N_SMTP_OAUTH_SERVICE_CLIENT` | 문자열 | _your_OAuth_service_client_ | 선택 사항 |
| `N8N_SMTP_OAUTH_PRIVATE_KEY` | 문자열 | _your_OAuth_private_key_ | 선택 사항 |
| `N8N_SMTP_SENDER` | 문자열 | 보낸 사람 이메일 주소입니다. 선택적으로 보낸 사람 이름을 포함할 수 있습니다. 이름 예: _N8N `<contact@n8n.com>`_ | 필수 |
| `N8N_SMTP_SSL` | 부울 | SMTP에 SSL을 사용할지(true) 여부(false)입니다. 기본값은 `true`입니다. | 선택 사항 | 
| `N8N_UM_EMAIL_TEMPLATES_INVITE` | 문자열 | HTML 이메일 템플릿의 전체 경로입니다. 초대 이메일의 기본 템플릿을 재정의합니다. | 선택 사항 |
| `N8N_UM_EMAIL_TEMPLATES_PWRESET` | 문자열 | HTML 이메일 템플릿의 전체 경로입니다. 암호 재설정 이메일의 기본 템플릿을 재정의합니다. | 선택 사항 |
| `N8N_UM_EMAIL_TEMPLATES_WORKFLOW_SHARED` | 문자열 | 자격 증명이 공유되었음을 사용자에게 알리는 기본 HTML 템플릿을 재정의합니다. 템플릿의 전체 경로를 제공하십시오. | 선택 사항 |
| `N8N_UM_EMAIL_TEMPLATES_CREDENTIALS_SHARED` | 문자열 | 자격 증명이 공유되었음을 사용자에게 알리는 기본 HTML 템플릿을 재정의합니다. 템플릿의 전체 경로를 제공하십시오. | 선택 사항 |

<!-- vale on-->
이미 n8n 인스턴스가 실행 중인 경우 새 SMTP 설정을 활성화하려면 다시 시작해야 합니다.

/// note | 더 많은 구성 옵션
환경 변수로 사용할 수 있는 더 많은 구성 옵션이 있습니다. 목록은 [환경 변수](/hosting/configuration/environment-variables/index.md)를 참조하십시오. 여기에는 사용자가 보지 않으려는 경우 태그, 워크플로우 템플릿 및 개인화 설문 조사를 비활성화하는 옵션이 포함됩니다.
///

/// note | SMTP를 처음 사용하십니까?
SMTP에 익숙하지 않은 경우 SendGrid의 [이 블로그 게시물](https://sendgrid.com/blog/what-is-an-smtp-server/)은 간단한 소개를 제공하고 Wikipedia의 [Simple Mail Transfer Protocol 문서](https://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol)는 더 자세한 기술적 배경을 제공합니다.
///

### 2단계: 인앱 설정

--8<-- "_snippets/user-management/in-app-setup.md"

### 3단계: 사용자 초대

--8<-- "_snippets/user-management/invite-users.md"