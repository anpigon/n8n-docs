---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: SSL 설정
description: "자체 호스팅 n8n 인스턴스에 대한 SSL을 설정합니다."
contentType: howto
---

# SSL 설정

n8n에서 TLS/SSL을 지원하는 방법에는 두 가지가 있습니다.

## 리버스 프록시 사용(권장)

n8n 인스턴스 앞에 [Traefik](https://doc.traefik.io/traefik/){:target=_blank .external-link} 또는 NLB(네트워크 로드 밸런서)와 같은 리버스 프록시를 사용합니다. 이렇게 하면 인증서 갱신도 처리됩니다.

자세한 내용은 [보안 | 데이터 암호화](https://n8n.io/legal/#security){:target=_blank .external-link}를 참조하십시오.

## 인증서를 n8n에 직접 전달

인증서를 n8n에 직접 전달하도록 선택할 수도 있습니다. 이렇게 하려면 `N8N_SSL_CERT` 및 `N8N_SSL_KEY` 환경 변수를 생성된 인증서 및 키 파일을 가리키도록 설정합니다.

인증서가 갱신되고 최신 상태로 유지되도록 해야 합니다.

이러한 변수에 대한 자세한 내용은 [배포 환경 변수](/hosting/configuration/environment-variables/deployment.md)를 참조하고 환경 변수 설정에 대한 자세한 내용은 [구성](/hosting/configuration/configuration-methods.md)을 참조하십시오.
