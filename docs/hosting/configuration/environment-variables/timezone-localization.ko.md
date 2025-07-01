#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 시간대 및 현지화 환경 변수
description: 자체 호스팅 n8n 인스턴스의 시간대 및 기본 언어 로케일을 설정합니다.
contentType: reference
tags:
  - 환경 변수
hide:
  - toc
  - tags
---

# 시간대 및 현지화 환경 변수

--8<-- "_snippets/self-hosting/file-based-configuration.md"

| 변수 | 유형 | 기본값 | 설명 |
| :------- | :---- | :------- | :---------- |
| `GENERIC_TIMEZONE` | * | `America/New_York` | n8n 인스턴스 시간대입니다. Cron과 같은 스케줄 노드에 중요합니다. |
| `N8N_DEFAULT_LOCALE` | 문자열 | `en` | [Accept-Language 헤더](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Accept-Language){:target="_blank" .external-link}와 호환되는 로케일 식별자입니다. n8n은 `de-AT`와 같은 지역 식별자를 지원하지 않습니다. 기본값 이외의 로케일에서 실행할 때 n8n은 선택한 로케일로 UI 문자열을 표시하고 번역되지 않은 문자열에 대해서는 `en`으로 대체합니다. |