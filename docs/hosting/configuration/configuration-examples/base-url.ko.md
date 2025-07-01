---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: n8n의 프런트엔드 액세스를 위한 기본 URL 구성
description: n8n의 백엔드 REST API에 대한 프런트엔드의 액세스 경로를 정의하기 위해 기본 URL 환경 변수를 구성합니다.
contentType: howto
---

# n8n의 프런트엔드 액세스를 위한 기본 URL 구성

/// warning | 수동 UI 빌드 필요
이 사용 사례는 `VUE_APP_URL_BASE_API` 환경 변수를 구성해야 하며, 이는 `n8n-editor-ui` 패키지의 수동 빌드가 필요합니다. 이 변수의 기본 설정이 `/`인 기본 n8n Docker 이미지에서는 사용할 수 없습니다. 즉, 루트 도메인을 사용합니다.
///

프런트엔드가 백엔드의 REST API에 연결하는 데 사용하는 기본 URL을 구성할 수 있습니다. 이는 n8n의 프런트엔드와 백엔드를 별도로 호스팅하려는 경우에 관련이 있습니다.

```bash
export VUE_APP_URL_BASE_API=https://n8n.example.com/
```
이 변수에 대한 자세한 내용은 [환경 변수 참조](/hosting/configuration/environment-variables/deployment.md)를 참조하십시오.
