#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 리버스 프록시로 웹훅 URL 구성
description: 리버스 프록시 설정과 호환되도록 n8n 웹훅 URL을 사용자 지정합니다.
contentType: howto
---

# 리버스 프록시로 n8n 웹훅 구성

n8n은 `N8N_PROTOCOL`, `N8N_HOST` 및 `N8N_PORT`를 결합하여 웹훅 URL을 만듭니다. n8n이 리버스 프록시 뒤에서 실행되는 경우 이는 작동하지 않습니다. 이는 n8n이 내부적으로 포트 5678에서 실행되지만 리버스 프록시는 포트 443에서 웹에 노출하기 때문입니다. 이 경우 n8n이 편집기 UI에 표시하고 외부 서비스에 올바른 웹훅 URL을 등록할 수 있도록 웹훅 URL을 수동으로 설정하는 것이 중요합니다.

```bash
export WEBHOOK_URL=https://n8n.example.com/
```
이 변수에 대한 자세한 내용은 [환경 변수 참조](/hosting/configuration/environment-variables/endpoints.md)를 참조하십시오.