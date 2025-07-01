---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 자격 증명 환경 변수
description: 자체 호스팅 n8n 인스턴스에 대한 환경 변수를 통해 기본 자격 증명을 관리하고 재정의합니다.
contentType: reference
tags:
  - 환경 변수
hide:
  - toc
  - tags
---

# 자격 증명 환경 변수

--8<-- "_snippets/self-hosting/file-based-configuration.md"

다음 환경 변수를 사용하여 자격 증명 재정의를 활성화합니다. 자세한 내용은 [자격 증명 재정의](/embed/configuration.md#credential-overwrites)를 참조하십시오.

| 변수 | 유형 | 기본값 | 설명 |
| :------- | :---- | :------- | :---------- |
| `CREDENTIALS_OVERWRITE_DATA`<br>/`_FILE` | * | - | 자격 증명 재정의. |
| `CREDENTIALS_OVERWRITE_ENDPOINT` | 문자열 | - | 자격 증명을 가져올 API 엔드포인트. |
| `CREDENTIALS_DEFAULT_NAME` | 문자열 | `내 자격 증명` | 자격 증명의 기본 이름. |
