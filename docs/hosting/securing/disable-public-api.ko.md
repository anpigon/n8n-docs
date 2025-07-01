---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 공개 REST API 비활성화
description: "다른 사람이 사용하지 못하도록 n8n 공개 REST API를 비활성화합니다."
contentType: howto
---

# 공개 REST API 비활성화

[n8n 공개 REST API](/api/index.md)를 사용하면 n8n GUI에서와 동일한 많은 작업을 프로그래밍 방식으로 수행할 수 있습니다.

이 API를 사용할 계획이 없다면 n8n 설치의 보안을 향상시키기 위해 비활성화하는 것이 좋습니다.

[공개 REST API](/api/index.md)를 비활성화하려면 `N8N_PUBLIC_API_DISABLED` 환경 변수를 `true`로 설정하십시오. 예를 들면 다음과 같습니다.

```bash
export N8N_PUBLIC_API_DISABLED=true
```

## API 플레이그라운드 비활성화

[API 플레이그라운드](/api/using-api-playground.md)를 비활성화하려면 `N8N_PUBLIC_API_SWAGGERUI_DISABLED` 환경 변수를 `true`로 설정하십시오. 예를 들면 다음과 같습니다.

```bash
export N8N_PUBLIC_API_SWAGGERUI_DISABLED=true
```

## 관련 리소스

이러한 환경 변수에 대한 자세한 내용은 [배포 환경 변수](/hosting/configuration/environment-variables/deployment.md)를 참조하십시오.

환경 변수 설정에 대한 자세한 내용은 [구성](/hosting/configuration/configuration-methods.md)을 참조하십시오.
