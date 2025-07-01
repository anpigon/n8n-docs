#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: n8n 격리
description: n8n 인스턴스가 n8n 서버와 연결되지 않도록 방지합니다.
contentType: howto
---

# n8n 격리

기본적으로 자체 호스팅 n8n 인스턴스는 n8n 서버로 데이터를 보냅니다. 사용 가능한 업데이트, 워크플로우 템플릿 및 진단에 대해 사용자에게 알립니다.

n8n 인스턴스가 n8n 서버에 연결되지 않도록 하려면 이러한 환경 변수를 false로 설정하십시오.

```
N8N_DIAGNOSTICS_ENABLED=false
N8N_VERSION_NOTIFICATIONS_ENABLED=false
N8N_TEMPLATES_ENABLED=false
```

n8n의 진단 구성 설정 해제:

```
EXTERNAL_FRONTEND_HOOKS_URLS=
N8N_DIAGNOSTICS_CONFIG_FRONTEND=
N8N_DIAGNOSTICS_CONFIG_BACKEND=
```

이러한 변수에 대한 자세한 내용은 [환경 변수 참조](/hosting/configuration/environment-variables/deployment.md)를 참조하십시오.