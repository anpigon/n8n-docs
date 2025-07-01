#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 사용자 관리 SMTP 및 2단계 인증 환경 변수
description: 사용자 관리 및 이메일을 설정하는 환경 변수입니다.
contentType: reference
tags:
  - 환경 변수
hide:
  - toc
  - tags
---

# 사용자 관리 SMTP 및 2단계 인증 환경 변수

--8<-- "_snippets/self-hosting/file-based-configuration.md"

사용자 관리 및 이메일 설정에 대한 자세한 내용은 [사용자 관리](/hosting/configuration/user-management-self-hosted.md)를 참조하십시오.
<!-- vale off -->
| 변수 | 유형 | 기본값 | 설명 |
| :------- | :--- | :------ | :---------- |
| `N8N_EMAIL_MODE` | 문자열 | `smtp` | 이메일을 활성화합니다. |
| `N8N_SMTP_HOST` | 문자열 | - | _your_SMTP_server_name_ |
| `N8N_SMTP_PORT` | 숫자 | - | _your_SMTP_server_port_ |
| `N8N_SMTP_USER` | 문자열 | - | _your_SMTP_username_ |
| `N8N_SMTP_PASS` | 문자열 | - | _your_SMTP_password_ |
| `N8N_SMTP_OAUTH_SERVICE_CLIENT` | 문자열 | - | 서비스 계정으로 2LO를 사용하는 경우 클라이언트 ID입니다. |
| `N8N_SMTP_OAUTH_PRIVATE_KEY` | 문자열 | - | 서비스 계정으로 2LO를 사용하는 경우 개인 키입니다. |
| `N8N_SMTP_SENDER` | 문자열 | - | 보낸 사람 이메일 주소입니다. 선택적으로 보낸 사람 이름을 포함할 수 있습니다. 이름 예: _N8N `<contact@n8n.com>`_ |
| `N8N_SMTP_SSL` | 부울 | `true` | SMTP에 SSL을 사용할지(true) 여부(false)입니다. |
| `N8N_SMTP_STARTTLS` | 부울 | `true` | SMTP에 STARTTLS를 사용할지(true) 여부(false)입니다. |
| `N8N_UM_EMAIL_TEMPLATES_INVITE` | 문자열 | - | HTML 이메일 템플릿의 전체 경로입니다. 초대 이메일의 기본 템플릿을 재정의합니다. |
| `N8N_UM_EMAIL_TEMPLATES_PWRESET` | 문자열 | - | HTML 이메일 템플릿의 전체 경로입니다. 암호 재설정 이메일의 기본 템플릿을 재정의합니다. |
| `N8N_UM_EMAIL_TEMPLATES_WORKFLOW_SHARED` | 문자열 | - | 워크플로우가 공유되었음을 사용자에게 알리는 기본 HTML 템플릿을 재정의합니다. 템플릿의 전체 경로를 제공하십시오. |
| `N8N_UM_EMAIL_TEMPLATES_CREDENTIALS_SHARED` | 문자열 | - | 자격 증명이 공유되었음을 사용자에게 알리는 기본 HTML 템플릿을 재정의합니다. 템플릿의 전체 경로를 제공하십시오. | |
| `N8N_USER_MANAGEMENT_JWT_SECRET` | 문자열 | - | 특정 JWT 비밀을 설정합니다. 기본적으로 n8n은 시작 시 하나를 생성합니다. |
| `N8N_USER_MANAGEMENT_JWT_DURATION_HOURS` | 숫자 | 168 | JWT의 만료 날짜를 시간 단위로 설정합니다. |
| `N8N_USER_MANAGEMENT_JWT_REFRESH_TIMEOUT_HOURS` | 숫자 | 0 | JWT가 만료되기 몇 시간 전에 자동으로 새로 고칠지입니다. 0은 `N8N_USER_MANAGEMENT_JWT_DURATION_HOURS`의 25%를 의미합니다. -1은 절대 새로 고치지 않음을 의미하며, 이 경우 사용자는 `N8N_USER_MANAGEMENT_JWT_DURATION_HOURS`에 정의된 기간 후에 다시 로그인해야 합니다. |
| `N8N_MFA_ENABLED` | 부울 | `true` | 2단계 인증을 활성화할지(true) 여부(false)입니다. 기존 사용자가 2FA를 활성화한 경우 n8n은 이를 무시합니다. |
<!-- vale on -->