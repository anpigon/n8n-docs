#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 배포 환경 변수
description: 자체 호스팅 n8n 인스턴스에 대한 환경 변수로 배포 옵션 및 애플리케이션 접근성을 구성합니다.
contentType: reference
tags:
  - 환경 변수
hide:
  - toc
  - tags
---

# 배포 환경 변수

--8<-- "_snippets/self-hosting/file-based-configuration.md"

이 페이지에는 자체 호스팅 n8n 인스턴스에 대한 배포 구성 옵션이 나열되어 있으며, 여기에는 액세스 URL 설정, 템플릿 활성화, 암호화 사용자 지정 및 서버 세부 정보 구성이 포함됩니다.

| 변수 | 유형 | 기본값 | 설명 |
| :------- | :---- | :------- | :---------- |
| `N8N_EDITOR_BASE_URL` | 문자열 | - | 사용자가 편집기에 액세스할 수 있는 공개 URL입니다. n8n에서 보낸 이메일 및 SAML 기반 인증의 리디렉션 URL에도 사용됩니다. |
| `N8N_CONFIG_FILES` | 문자열 | - | JSON [구성 파일](/hosting/configuration/configuration-methods.md)의 경로를 제공하는 데 사용합니다. |
| `N8N_DISABLE_UI` | 부울 | `false` | UI를 비활성화하려면 `true`로 설정합니다. |
| `N8N_PREVIEW_MODE` | 부울 | `false` | 미리보기 모드에서 실행하려면 `true`로 설정합니다. |
| `N8N_TEMPLATES_ENABLED` | 부울 | `false` | [워크플로우 템플릿](/glossary.md#template-n8n)을 활성화(true)하거나 비활성화(false)합니다. |
| `N8N_TEMPLATES_HOST` | 문자열 | `https://api.n8n.io` | 자체 워크플로우 템플릿 라이브러리를 만드는 경우 이 값을 변경합니다. 자체 워크플로우 템플릿 라이브러리를 사용하려면 API가 n8n과 동일한 엔드포인트 및 응답 구조를 제공해야 합니다. 자세한 내용은 [워크플로우 템플릿](/workflows/templates.md)을 참조하십시오. |
| `N8N_ENCRYPTION_KEY` | 문자열 | n8n에서 생성된 임의 키 | n8n 데이터베이스에서 자격 증명을 암호화하는 데 사용되는 사용자 지정 키를 제공합니다. 기본적으로 n8n은 첫 실행 시 임의 키를 생성합니다. |
| `N8N_USER_FOLDER` | 문자열 | `user-folder` | n8n이 `.n8n` 폴더를 만들 경로를 제공합니다. 이 디렉토리는 데이터베이스 파일 및 암호화 키와 같은 사용자별 데이터를 저장합니다. |
| `N8N_PATH` | 문자열 | `/` | n8n이 배포되는 경로입니다. |
| `N8N_HOST` | 문자열 | `localhost` | n8n이 실행되는 호스트 이름입니다. |
| `N8N_PORT` | 숫자 | `5678` | n8n이 실행되는 HTTP 포트입니다. |
| `N8N_LISTEN_ADDRESS` | 문자열 | `0.0.0.0` | n8n이 수신해야 하는 IP 주소입니다. |
| `N8N_PROTOCOL` | 열거형 문자열: `http`, `https` | `http` | n8n에 도달하는 데 사용되는 프로토콜입니다. |
| `N8N_SSL_KEY` | 문자열 | - | HTTPS 프로토콜의 SSL 키입니다. |
| `N8N_SSL_CERT` | 문자열 | - | HTTPS 프로토콜의 SSL 인증서입니다. |
| `N8N_PERSONALIZATION_ENABLED` | 부울 | `true` | 사용자에게 개인화 질문을 하고 그에 따라 n8n을 사용자 지정할지 여부입니다. |
| `N8N_VERSION_NOTIFICATIONS_ENABLED` | 부울 | `true` | 활성화되면 n8n은 새 버전 및 보안 업데이트 알림을 보냅니다. |
| `N8N_VERSION_NOTIFICATIONS_ENDPOINT` | 문자열 | `https://api.n8n.io/versions/` | 버전 정보를 검색하는 엔드포인트입니다. |
| `N8N_VERSION_NOTIFICATIONS_INFO_URL` | 문자열 | `https://docs.n8n.io/getting-started/installation/updating.html` | 자세한 내용은 새 버전 패널에 표시되는 URL입니다. |
| `N8N_DIAGNOSTICS_ENABLED` | 부울 | `true` | 선택한 익명의 [원격 측정](/privacy-security/privacy.md)을 n8n과 공유할지 여부입니다. 이 값을 `false`로 설정하면 코드 노드에서 Ask AI를 활성화할 수 없습니다. |
| `N8N_DIAGNOSTICS_CONFIG_FRONTEND` | 문자열 | `1zPn9bgWPzlQc0p8Gj1uiK6DOTn;https://telemetry.n8n.io` | 프런트엔드의 원격 측정 구성입니다. |
| `N8N_DIAGNOSTICS_CONFIG_BACKEND` | 문자열 | `1zPn7YoGC3ZXE9zLeTKLuQCB4F6;https://telemetry.n8n.io/v1/batch` | 백엔드의 원격 측정 구성입니다. |
| `N8N_PUSH_BACKEND` | 문자열 | `websocket` | n8n 백엔드가 서버 전송 이벤트(`sse`) 또는 웹소켓(`websocket`)을 사용하여 UI에 변경 사항을 보낼지 여부를 선택합니다. |
| `VUE_APP_URL_BASE_API` | 문자열 | `http://localhost:5678/` | `n8n-editor-ui` 패키지를 수동으로 빌드할 때 프런트엔드가 백엔드 API에 도달하는 방법을 설정하는 데 사용됩니다. [기본 URL 구성](/hosting/configuration/configuration-examples/base-url.md)을 참조하십시오. |
| `N8N_HIRING_BANNER_ENABLED` | 부울 | `true` | 콘솔에 n8n 채용 배너를 표시할지(true) 여부(false)입니다. |
| `N8N_PUBLIC_API_SWAGGERUI_DISABLED` | 부울 | `false` | Swagger UI(API 플레이그라운드)를 비활성화할지(true) 여부(false)입니다. |
| `N8N_PUBLIC_API_DISABLED` | 부울 | `false` | 공개 API를 비활성화할지(true) 여부(false)입니다. |
| `N8N_PUBLIC_API_ENDPOINT` | 문자열 | `api` | 공개 API 엔드포인트의 경로입니다. |
| `N8N_GRACEFUL_SHUTDOWN_TIMEOUT` | 숫자 | `30` | n8n 프로세스가 프로세스를 종료하기 전에 구성 요소가 종료될 때까지 기다려야 하는 시간(초)입니다. |
| `N8N_DEV_RELOAD` | 부울 | `false` | n8n 소스 코드에서 작업할 때 소스 코드 파일에 변경 사항이 발생하면 애플리케이션을 자동으로 다시 로드하거나 다시 시작하려면 이 값을 `true`로 설정합니다. |
| `N8N_REINSTALL_MISSING_PACKAGES` | 부울 | `false` | `true`로 설정하면 n8n이 누락된 패키지를 자동으로 다시 설치하려고 시도합니다. |
| `N8N_TUNNEL_SUBDOMAIN` | 문자열 | - | n8n 터널의 하위 도메인을 지정합니다. 설정하지 않으면 n8n이 임의의 하위 도메인을 생성합니다.|
| `N8N_PROXY_HOPS` | 숫자 | 0 | n8n이 실행 중인 리버스 프록시 수입니다. |