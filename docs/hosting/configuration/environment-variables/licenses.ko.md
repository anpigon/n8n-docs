#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 라이선스 환경 변수
description: 사용 페이지 숨기기, 라이선스 활성화 및 자동 갱신 설정 관리, 라이선스 검색을 위한 서버 URL 지정을 포함하여 n8n의 라이선스 설정을 구성하는 환경 변수입니다.
contentType: reference
tags:
  - 환경 변수
hide:
  - toc
  - tags
---

# 라이선스 환경 변수

--8<-- "_snippets/self-hosting/file-based-configuration.md"

특정 라이선스 기능을 활성화하려면 먼저 라이선스를 활성화해야 합니다. UI를 통해 또는 환경 변수를 설정하여 이 작업을 수행할 수 있습니다. 자세한 내용은 [라이선스 키](/license-key.md)를 참조하십시오.

| 변수 | 유형 | 기본값 | 설명 |
| :------- | :---- | :------- | :---------- |
| `N8N_HIDE_USAGE_PAGE` | 부울 | `false` | 앱에서 사용량 및 요금제 페이지를 숨깁니다. |
| `N8N_LICENSE_ACTIVATION_KEY` | 문자열 | `''` | 라이선스를 초기화하는 활성화 키입니다. n8n 인스턴스가 이미 활성화된 경우에는 적용되지 않습니다. |
| `N8N_LICENSE_AUTO_RENEW_ENABLED` | 부울 | `true` | 라이선스 자동 갱신을 활성화(true) 또는 비활성화(false)합니다. <br>비활성화된 경우 **설정** > **사용량 및 요금제**로 이동하여 `F5`를 눌러 10일마다 라이선스를 수동으로 갱신해야 합니다. 라이선스를 갱신하지 않으면 모든 라이선스 기능이 비활성화됩니다. |
| `N8N_LICENSE_DETACH_FLOATING_ON_SHUTDOWN` | 부울 | `true` | 인스턴스가 종료 시 [부동 자격](/glossary.md#entitlement-n8n)을 풀로 다시 해제할지 여부를 제어합니다. 다른 인스턴스가 자격을 재사용하도록 허용하려면 `true`로 설정하고 유지하려면 `false`로 설정합니다. <br> 항상 라이선스 기능을 유지해야 하는 프로덕션 인스턴스의 경우 이 값을 `false`로 설정하십시오. |
| `N8N_LICENSE_SERVER_URL` | 문자열 | `https://license.n8n.io/v1` | 라이선스를 검색할 서버 URL입니다. |
| `N8N_LICENSE_TENANT_ID` | 숫자 | `1` | 라이선스와 연결된 테넌트 ID입니다. n8n에서 명시적으로 지시한 경우에만 이 변수를 설정하십시오. |
| `https_proxy_license_server` | 문자열 | `https://user:pass@proxy:port` | 라이선스를 검색하기 위한 HTTPS 요청에 대한 프록시 서버 URL입니다. 이 변수 이름은 소문자여야 합니다. |