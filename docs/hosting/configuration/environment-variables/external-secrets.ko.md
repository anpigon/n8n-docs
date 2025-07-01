---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 외부 비밀 환경 변수
description: 자체 호스팅 n8n 인스턴스에서 외부 비밀 업데이트 확인 간격을 구성합니다.
contentType: reference
tags:
  - 환경 변수
hide:
  - toc
  - tags
---

# 외부 비밀 환경 변수

--8<-- "_snippets/self-hosting/file-based-configuration.md"

외부 비밀 저장소를 사용하여 n8n의 자격 증명을 관리할 수 있습니다. 자세한 내용은 [외부 비밀](/external-secrets.md)을 참조하십시오.

| 변수 | 유형 | 기본값 | 설명 |
| :------- | :---- | :------- | :---------- |
| `N8N_EXTERNAL_SECRETS_UPDATE_INTERVAL` | 숫자 | `300` (5분) | 비밀 업데이트를 확인하는 빈도(초)입니다. |
