#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 보안 환경 변수
description: 자체 호스팅 n8n 인스턴스에서 인증 및 환경 변수 액세스를 구성합니다.
contentType: reference
tags:
  - 환경 변수
hide:
  - toc
  - tags
---

# 보안 환경 변수

--8<-- "_snippets/self-hosting/file-based-configuration.md"

| 변수 | 유형 | 기본값 | 설명 |
| :------- | :---- | :------- | :---------- |
| `N8N_BLOCK_ENV_ACCESS_IN_NODE` | 부울 | `false` | 사용자가 표현식 및 코드 노드에서 환경 변수에 액세스하도록 허용할지(false) 여부(true)입니다. |
| `N8N_BLOCK_FILE_ACCESS_TO_N8N_FILES` | 부울 | `true` | `.n8n` 디렉토리 및 사용자 정의 구성 파일의 모든 파일에 대한 액세스를 차단하려면 `true`로 설정합니다. |
| `N8N_ENFORCE_SETTINGS_FILE_PERMISSIONS` | 부울 | `false` | 설정 파일에 대해 0600 권한을 설정하여 소유자에게만 읽기 및 쓰기 액세스 권한을 부여하려면 `true`로 설정합니다. |
| `N8N_RESTRICT_FILE_ACCESS_TO` | 문자열 | | 이러한 디렉토리의 파일에 대한 액세스를 제한합니다. 여러 파일을 콜론으로 구분된 목록("`:`")으로 제공하십시오. |
| `N8N_SECURITY_AUDIT_DAYS_ABANDONED_WORKFLOW` | 숫자 | 90 | 워크플로우가 실행되지 않은 경우 포기된 것으로 간주할 일수입니다. |
| `N8N_SECURE_COOKIE` | 부울 | `true` | 쿠키가 HTTPS를 통해서만 전송되도록 하여 보안을 강화합니다.|
| `N8N_SAMESITE_COOKIE` | 열거형 문자열: `strict`, `lax`, `none` | `lax` | 사이트 간 쿠키 동작을 제어합니다([자세히 알아보기](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Set-Cookie/SameSite)):<ul><li>`strict`: 자사 요청에 대해서만 전송됩니다.</li><li>`lax` (기본값): 최상위 탐색 요청과 함께 전송됩니다.</li><li>`none`: 모든 컨텍스트에서 전송됩니다(HTTPS 필요).</li></ul> |