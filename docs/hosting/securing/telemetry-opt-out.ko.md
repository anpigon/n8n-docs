---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 데이터 수집 옵트아웃
description: "n8n 인스턴스에서 데이터 원격 측정 수집을 옵트아웃합니다."
contentType: howto
---

# 데이터 수집

n8n은 자체 호스팅 n8n 설치에서 일부 익명 데이터를 수집합니다. 데이터 원격 측정 수집을 옵트아웃하려면 아래 지침을 사용하십시오.

## 수집된 데이터

n8n이 수집하는 데이터에 대한 자세한 내용은 [개인정보 보호 | 자체 호스팅 n8n의 데이터 수집](/privacy-security/privacy.md#data-collection-in-self-hosted-n8n)을 참조하십시오.

## 수집 작동 방식

n8n 인스턴스는 이벤트가 발생할 때 대부분의 데이터를 n8n으로 보냅니다. 워크플로우 실행 횟수 및 인스턴스 펄스는 주기적으로(6시간마다) 전송됩니다. 이러한 데이터 유형은 대부분 n8n 원격 측정 수집에 해당합니다.

## 데이터 수집 옵트아웃

n8n은 기본적으로 원격 측정 수집을 활성화합니다. 비활성화하려면 다음 환경 변수를 구성하십시오.

### 원격 측정 이벤트 옵트아웃

원격 측정 이벤트를 옵트아웃하려면 `N8N_DIAGNOSTICS_ENABLED` 환경 변수를 false로 설정하십시오. 예를 들면 다음과 같습니다.

```bash
export N8N_DIAGNOSTICS_ENABLED=false
```

### n8n의 새 버전 확인 옵트아웃

n8n의 새 버전 확인을 옵트아웃하려면 `N8N_VERSION_NOTIFICATIONS_ENABLED` 환경 변수를 false로 설정하십시오. 예를 들면 다음과 같습니다.

```bash
export N8N_VERSION_NOTIFICATIONS_ENABLED=false
```

## n8n 서버에 대한 모든 연결 비활성화

n8n 서버와의 모든 통신을 완전히 방지하려면 [n8n 격리](/hosting/configuration/configuration-examples/isolation.md)를 참조하십시오.

## 관련 리소스

이러한 환경 변수에 대한 자세한 내용은 [배포 환경 변수](/hosting/configuration/environment-variables/deployment.md)를 참조하십시오.

환경 변수 설정에 대한 자세한 내용은 [구성](/hosting/configuration/configuration-methods.md)을 참조하십시오.
