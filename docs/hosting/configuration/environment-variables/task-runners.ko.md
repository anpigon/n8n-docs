---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 작업 실행기 환경 변수
description: 자체 호스팅 n8n 인스턴스에 대한 작업 실행기를 구성하는 환경 변수입니다.
contentType: reference
tags:
  - 환경 변수
hide:
  - toc
  - tags
---

# 작업 실행기 환경 변수

--8<-- "_snippets/self-hosting/file-based-configuration.md"

[작업 실행기](/hosting/configuration/task-runners.md)는 [코드 노드](/integrations/builtin/core-nodes/n8n-nodes-base.code/index.md)에서 정의한 코드를 실행합니다.

## n8n 인스턴스 환경 변수

| 변수 | 유형 | 기본값 | 설명 |
| :------- | :---- | :------- | :---------- |
| `N8N_RUNNERS_ENABLED` | 부울 | `false` | 작업 실행기가 활성화되었습니까? |
| `N8N_RUNNERS_MODE` | 열거형 문자열: `internal`, `external` | `internal` | 작업 실행기를 시작하고 실행하는 방법입니다. `internal`은 n8n이 작업 실행기를 자식 프로세스로 시작한다는 의미입니다. `external`은 외부 오케스트레이터가 작업 실행기를 시작한다는 의미입니다. |
| `N8N_RUNNERS_AUTH_TOKEN` | 문자열 | 임의 문자열 | 작업 실행기가 n8n에 인증하는 데 사용하는 공유 비밀입니다. `external` 모드를 사용할 때 필요합니다. |
| `N8N_RUNNERS_BROKER_PORT` | 숫자 | `5679` | 작업 브로커가 작업 실행기 연결을 수신하는 포트입니다. |
| `N8N_RUNNERS_BROKER_LISTEN_ADDRESS` | 문자열 | `127.0.0.1` | 작업 브로커가 수신하는 주소입니다. |
| `N8N_RUNNERS_MAX_PAYLOAD` | 숫자 | `1 073 741 824` | 작업 브로커와 작업 실행기 간의 통신을 위한 최대 페이로드 크기(바이트)입니다. |
| `N8N_RUNNERS_MAX_OLD_SPACE_SIZE` | 문자열 | | 작업 실행기에 사용할 `--max-old-space-size` 옵션(MB)입니다. 기본적으로 Node.js는 사용 가능한 메모리를 기반으로 이를 설정합니다. |
| `N8N_RUNNERS_MAX_CONCURRENCY` | 숫자 | `5` | 작업 실행기가 한 번에 실행할 수 있는 동시 작업 수입니다. |
| `N8N_RUNNERS_TASK_TIMEOUT` | 숫자 | `60` | 작업이 중단되고 실행기가 다시 시작되기 전에 작업을 완료하는 데 걸리는 시간(초)입니다. 0보다 커야 합니다. |
| `N8N_RUNNERS_HEARTBEAT_INTERVAL` | 숫자 | `30` | 실행기가 브로커에 하트비트를 보내야 하는 빈도(초)이며, 그렇지 않으면 작업이 중단되고 실행기가 다시 시작됩니다. 0보다 커야 합니다. |


## 작업 실행기 시작 프로그램 환경 변수

| 변수 | 유형 | 기본값 | 설명 |
| :------- | :---- | :------- | :---------- |
| `N8N_RUNNERS_LAUNCHER_LOG_LEVEL` | 열거형 문자열: `debug`, `info`, `warn`, `error` | `info` | 표시할 로그 메시지입니다. |
| `N8N_RUNNERS_AUTH_TOKEN` | 문자열 | - | n8n에 인증하는 데 사용되는 공유 비밀입니다. |
| `N8N_RUNNERS_AUTO_SHUTDOWN_TIMEOUT` | 숫자 | `15` | 유휴 실행기를 종료하기 전에 기다리는 시간(초)입니다. |
| `N8N_RUNNERS_TASK_BROKER_URI` | 문자열 | `http://127.0.0.1:5679` | 작업 브로커 서버(n8n 인스턴스)의 URI입니다. |
| `N8N_RUNNERS_LAUNCHER_HEALTH_CHECK_PORT` | 숫자 | `5680` | 시작 프로그램의 상태 확인 서버 포트입니다. |
| `N8N_RUNNERS_MAX_PAYLOAD` | 숫자 | `1 073 741 824` | 작업 브로커와 작업 실행기 간의 통신을 위한 최대 페이로드 크기(바이트)입니다. |
| `N8N_RUNNERS_MAX_CONCURRENCY` | 숫자 | `5` | 작업 실행기가 한 번에 실행할 수 있는 동시 작업 수입니다. |
| `NODE_OPTIONS` | 문자열 | - | Node.js에 대한 [옵션](https://nodejs.org/api/cli.html#node_optionsoptions)입니다. |


## 작업 실행기 환경 변수

| 변수 | 유형 | 기본값 | 설명 |
| :------- | :---- | :------- | :---------- |
| `N8N_RUNNERS_GRANT_TOKEN` | 문자열 | 임의 문자열 | 실행기가 작업 브로커에 인증하는 데 사용하는 토큰입니다. 이는 시작 프로그램에서 자동으로 제공됩니다. |
| `N8N_RUNNERS_AUTO_SHUTDOWN_TIMEOUT` | 숫자 | `15` | 유휴 실행기를 종료하기 전에 기다리는 시간(초)입니다. |
| `N8N_RUNNERS_TASK_BROKER_URI` | 문자열 | `http://127.0.0.1:5679` | 작업 브로커 서버(n8n 인스턴스)의 URI입니다. |
| `N8N_RUNNERS_LAUNCHER_HEALTH_CHECK_PORT` | 숫자 | `5680` | 시작 프로그램의 상태 확인 서버 포트입니다. |
| `N8N_RUNNERS_MAX_PAYLOAD` | 숫자 | `1 073 741 824` | 작업 브로커와 작업 실행기 간의 통신을 위한 최대 페이로드 크기(바이트)입니다. |
| `N8N_RUNNERS_MAX_CONCURRENCY` | 숫자 | `5` | 작업 실행기가 한 번에 실행할 수 있는 동시 작업 수입니다. |
| `NODE_FUNCTION_ALLOW_BUILTIN` | 문자열 | - | 사용자가 코드 노드에서 특정 내장 모듈을 가져올 수 있도록 허용합니다. 모두 허용하려면 *를 사용하십시오. n8n은 기본적으로 모듈 가져오기를 비활성화합니다. |
| `NODE_FUNCTION_ALLOW_EXTERNAL` | 문자열 | - | 사용자가 코드 노드에서 특정 외부 모듈(`n8n/node_modules`에서)을 가져올 수 있도록 허용합니다. n8n은 기본적으로 모듈 가져오기를 비활성화합니다. |
| `N8N_RUNNERS_ALLOW_PROTOTYPE_MUTATION` | 부울 | `false` | 외부 라이브러리에 대한 프로토타입 변형을 허용할지 여부입니다. 보안을 완화하는 대신 런타임 프로토타입 변형에 의존하는 모듈(예: [`puppeteer`](https://pptr.dev/))을 허용하려면 `true`로 설정합니다. | 
| `GENERIC_TIMEZONE` | * | `America/New_York` | [n8n 인스턴스에 대해 구성된 것과 동일한 기본 시간대](/hosting/configuration/environment-variables/timezone-localization.md)입니다. |
