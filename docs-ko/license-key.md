---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 라이선스 키
description: 라이선스 키를 활성화하는 방법입니다.
contentType: howto
---

# 라이선스 키

특정 라이선스 기능을 활성화하려면 먼저 라이선스를 활성화해야 합니다. 이는 UI를 통해 또는 환경 변수를 설정하여 수행할 수 있습니다.

## UI를 사용하여 라이선스 키 추가

n8n 인스턴스에서:

1. **관리자** 또는 **소유자**로 로그인합니다.
1. **설정** > **사용량 및 요금제**를 선택합니다.
1. **활성화 키 입력**을 선택합니다.
1. 라이선스 키를 붙여넣습니다.
1. **활성화**를 선택합니다.

## 환경 변수를 사용하여 라이선스 키 추가

n8n 구성에서 `N8N_LICENSE_ACTIVATION_KEY`를 라이선스 키로 설정합니다. 인스턴스에 이미 활성화된 라이선스가 있는 경우 이 변수는 영향을 미치지 않습니다.

n8n 구성에 대한 자세한 내용은 [환경 변수](/hosting/configuration/configuration-methods.md)를 참조하십시오.

## 라이선스 서버 IP 주소 허용 목록에 추가

n8n은 Cloudflare를 사용하여 라이선스 서버를 호스팅합니다. 특정 IP 주소는 변경될 수 있으므로 n8n이 항상 라이선스 서버에 접근할 수 있도록 [Cloudflare IP 주소의 전체 범위](https://www.cloudflare.com/ips/){:target=_blank .external-link}를 허용 목록에 추가해야 합니다.