#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 외부 후크 환경 변수
description: 자체 호스팅 n8n 인스턴스에 외부 후크를 통합하기 위한 환경 변수입니다.
contentType: reference
tags:
  - 환경 변수
hide:
  - toc
  - tags
---

# 외부 후크 환경 변수

--8<-- "_snippets/self-hosting/file-based-configuration.md"

특정 작업이 실행될 때마다 n8n이 실행하는 외부 후크를 정의할 수 있습니다. 사용 가능한 후크의 예는 [백엔드 후크](/embed/configuration.md#backend-hooks)를 참조하고 파일 서식에 대한 정보는 [후크 파일](/embed/configuration.md#backend-hook-files)을 참조하십시오.

| 변수 | 유형 | 설명 |
| :------- | :---- | :---------- |
| `EXTERNAL_HOOK_FILES` | 문자열 | 백엔드 외부 후크가 포함된 파일입니다. 여러 파일을 콜론으로 구분된 목록("`:`")으로 제공하십시오. |
| `EXTERNAL_FRONTEND_HOOKS_URLS` | 문자열 | 프런트엔드 외부 후크가 포함된 파일의 URL입니다. 여러 URL을 콜론으로 구분된 목록("`:`")으로 제공하십시오. |