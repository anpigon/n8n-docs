#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 외부 데이터 저장소 환경 변수
description: 자체 호스팅 n8n 인스턴스에 대한 외부 데이터 저장소를 구성하는 환경 변수입니다.
contentType: reference
tags:
  - 환경 변수
  - 외부 저장소
  - 저장소
hide:
  - toc
  - tags
---

# 외부 데이터 저장소 환경 변수

--8<-- "_snippets/self-hosting/file-based-configuration.md"

바이너리 데이터에 외부 저장소를 사용하는 방법에 대한 자세한 내용은 [외부 저장소](/hosting/scaling/external-storage.md)를 참조하십시오.

| 변수 | 유형 | 기본값 | 설명 |
| :------- | :---- | :------- | :---------- |
| `N8N_EXTERNAL_STORAGE_S3_HOST` | 문자열 | - | S3 호환 외부 저장소의 n8n 버킷 호스트입니다. 예: `s3.us-east-1.amazonaws.com` |
| `N8N_EXTERNAL_STORAGE_S3_BUCKET_NAME` | 문자열 | - | S3 호환 외부 저장소의 n8n 버킷 이름입니다. |
| `N8N_EXTERNAL_STORAGE_S3_BUCKET_REGION` | 문자열 | - | S3 호환 외부 저장소의 n8n 버킷 지역입니다. 예: `us-east-1`|
| `N8N_EXTERNAL_STORAGE_S3_ACCESS_KEY` | 문자열 | - | S3 호환 외부 저장소의 액세스 키입니다. |
| `N8N_EXTERNAL_STORAGE_S3_ACCESS_SECRET` | 문자열 | - | S3 호환 외부 저장소의 액세스 비밀입니다. |
| `N8N_EXTERNAL_STORAGE_S3_AUTH_AUTO_DETECT` | 부울 | - | 외부 저장소에 대한 S3 호출을 인증하기 위해 자동 자격 증명 검색을 사용합니다. 이렇게 하면 액세스 키와 액세스 비밀이 무시되고 기본 [자격 증명 공급자 체인](https://docs.aws.amazon.com/sdk-for-javascript/v3/developer-guide/setting-credentials-node.html#credchain)이 사용됩니다. |