---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: n8n 보안
contentType: overview
---

# n8n 보안

n8n 인스턴스를 보호하는 방법에는 여러 가지가 있습니다.

상위 수준에서 다음을 수행할 수 있습니다.

* [보안 감사](/hosting/securing/security-audit.md)를 수행하여 보안 위험을 식별합니다.
* [SSL 설정](/hosting/securing/set-up-ssl.md)을 통해 보안 연결을 강제합니다.
* 사용자 계정 관리를 위해 [단일 로그온 설정](/hosting/securing/set-up-sso.md)을 합니다.
* 사용자를 위해 [2단계 인증(2FA)](/user-management/two-factor-auth.md)을 사용합니다.

보다 세부적으로는 원하지 않는 기능이나 데이터 수집을 차단하거나 옵트아웃하는 것을 고려하십시오.

* 사용하지 않는 경우 [공개 API 비활성화](/hosting/securing/disable-public-api.md)합니다.
* n8n이 자동으로 수집하는 익명 데이터의 [데이터 수집 옵트아웃](/hosting/securing/telemetry-opt-out.md)합니다.
* 사용자가 사용할 수 없도록 [특정 노드 차단](/hosting/securing/blocking-nodes.md)합니다.
