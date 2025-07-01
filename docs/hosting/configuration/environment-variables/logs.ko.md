---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 로그 환경 변수
description: 로깅 및 진단 데이터를 구성하는 환경 변수입니다.
contentType: reference
tags:
  - 환경 변수
hide:
  - toc
  - tags
---

# 로그 환경 변수

--8<-- "_snippets/self-hosting/file-based-configuration.md"

이 페이지에는 디버깅을 위한 로깅을 설정하는 환경 변수가 나열되어 있습니다. 자세한 내용은 [n8n의 로깅](/hosting/logging-monitoring/logging.md)을 참조하십시오.

## n8n 로그

<!-- vale off -->
| 변수 | 유형 | 기본값 | 설명 |
| :------- | :---- | :------- | :---------- |
| `N8N_LOG_LEVEL` | 열거형 문자열: `info`, `warn`, `error`, `debug` | `info` | 로그 출력 수준입니다. 자세한 내용은 [로그 수준](/hosting/logging-monitoring/logging.md#log-levels)을 참조하십시오. |
| `N8N_LOG_OUTPUT` | 열거형 문자열: `console`, `file` | `console` | 로그를 출력할 위치입니다. 여러 값을 쉼표로 구분하여 제공할 수 있습니다. |
| `N8N_LOG_FORMAT` | 열거형 문자열: `text`, `json` | `text` | 사용할 로그 형식입니다. `text`는 사람이 읽을 수 있는 메시지를 인쇄합니다. `json`은 메시지, 수준, 타임스탬프 및 모든 메타데이터를 포함하는 줄당 하나의 JSON 개체를 인쇄합니다. 이는 프로덕션 모니터링 및 디버깅에 유용합니다. |
| `N8N_LOG_FILE_COUNT_MAX` | 숫자 | `100` | 보관할 최대 로그 파일 수입니다. |
| `N8N_LOG_FILE_SIZE_MAX` | 숫자 | `16` | 각 로그 파일의 최대 크기(MB)입니다. |
| `N8N_LOG_FILE_LOCATION` | 문자열 | `<n8n-directory-path>/logs/n8n.log` | 로그 파일 위치입니다. N8N_LOG_OUTPUT을 `file`로 설정해야 합니다. |
| `DB_LOGGING_ENABLED` | 부울 | `false` | 데이터베이스별 로깅을 활성화할지 여부입니다. |
| `DB_LOGGING_OPTIONS` | 열거형 문자열: `query`, `error`, `schema`, `warn`, `info`, `log` | `error` | 데이터베이스 로그 출력 수준입니다. 모든 로깅을 활성화하려면 `all`을 지정하십시오. [TypeORM 로깅 옵션](https://orkhan.gitbook.io/typeorm/docs/logging#logging-options){:target=_blank .external-link}을 참조하십시오. |
| `DB_LOGGING_MAX_EXECUTION_TIME` | 숫자 | `1000` | n8n이 경고를 기록하기 전의 최대 실행 시간(밀리초)입니다. 장기 실행 쿼리 경고를 비활성화하려면 `0`으로 설정하십시오. |
| `CODE_ENABLE_STDOUT` | 부울 | `false` | 디버깅, 모니터링 또는 로깅 목적으로 코드 노드 로그를 프로세스의 stdout으로 보내려면 `true`로 설정하십시오. |
| `NO_COLOR` | any | `undefined` | ANSI 색상 없이 로그를 출력하려면 아무 값이나 설정하십시오. 자세한 내용은 [no-color.org 웹사이트](https://no-color.org/){:target=_blank .external-link}를 참조하십시오. |
<!-- vale on -->

## 로그 스트리밍

이 기능에 대한 자세한 내용은 [로그 스트리밍](/log-streaming.md)을 참조하십시오.

| 변수 | 유형 | 기본값 | 설명 |
| :------- | :---- | :------- | :---------- |
| `N8N_EVENTBUS_CHECKUNSENTINTERVAL` | 숫자 | `0` | 보내지 않은 이벤트 메시지를 확인하는 빈도(밀리초)입니다. 드문 경우에 메시지를 두 번 보낼 수 있습니다. 비활성화하려면 `0`으로 설정하십시오. |
| `N8N_EVENTBUS_LOGWRITER_SYNCFILEACCESS` | 부울 | `false` | 모든 파일 액세스가 스레드 내에서 동기적으로 발생하는지(true) 여부(false)입니다. |
| `N8N_EVENTBUS_LOGWRITER_KEEPLOGCOUNT` | 숫자 | `3` | 보관할 이벤트 로그 파일 수입니다. |
| `N8N_EVENTBUS_LOGWRITER_MAXFILESIZEINKB` | 숫자 | `10240` | 새 파일이 시작되기 전의 이벤트 로그 파일의 최대 크기(KB)입니다. |
| `N8N_EVENTBUS_LOGWRITER_LOGBASENAME` | 문자열 | `n8nEventLog` | 이벤트 로그 파일의 기본 이름입니다. |
