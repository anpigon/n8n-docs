---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: n8n v1.0 마이그레이션 가이드
description: 버전 1의 새로운 기능
contentType: reference
---

# n8n v1.0 마이그레이션 가이드

이 문서는 n8n 1.0 버전으로 업데이트하기 전에 알아야 할 사항을 요약하여 제공합니다.

n8n 1.0 출시는 까다로운 프로덕션 환경에서 n8n을 사용할 수 있도록 만들려는 n8n 여정의 이정표입니다. 버전 1.0은 n8n을 가장 접근하기 쉽고 강력하며 다재다능한 자동화 도구로 만들기 위해 지난 4년간 투자한 노력의 결실입니다. n8n 1.0은 이제 프로덕션 환경에서 사용할 준비가 되었습니다.

## 새로운 기능

### 코드 노드에서 파이썬 지원

자바스크립트가 기본 언어로 유지되지만, 이제 [코드 노드](/code/code-node.md)에서 파이썬을 옵션으로 선택할 수 있으며, [많은 파이썬 모듈](https://pyodide.org/en/stable/usage/packages-in-pyodide.html#packages-in-pyodide){:target=_blank .external link}도 활용할 수 있습니다. v1.0 이전에 워크플로우에 추가된 코드 노드에서는 파이썬을 사용할 수 없습니다.

[PR #4295](https://github.com/n8n-io/n8n/pull/4295){:target=_blank .external link}, [PR #6209](https://github.com/n8n-io/n8n/pull/6209){:target=_blank .external link}

### 실행 순서

n8n 1.0은 다중 분기 워크플로우에 대한 새로운 실행 순서를 도입합니다.

다중 분기 워크플로우에서 n8n은 분기의 노드를 실행할 순서를 결정해야 합니다. 이전에는 n8n이 각 분기의 첫 번째 노드를 실행한 다음 각 분기의 두 번째 노드를 실행하는 방식(너비 우선)이었습니다. 새로운 실행 순서는 각 분기가 다음 분기를 시작하기 전에 완전히 실행되도록 보장합니다(깊이 우선). 분기는 캔버스에서의 위치에 따라 위에서 아래로 실행됩니다. 두 분기가 같은 높이에 있으면 왼쪽 분기가 먼저 실행됩니다.

n8n은 다중 입력 노드가 첫 번째 입력에서 데이터를 받는 한 해당 노드를 실행했습니다. 다중 입력 노드의 두 번째 입력에 연결된 노드는 데이터를 받았는지 여부에 관계없이 자동으로 실행되었습니다. n8n 1.0에 도입된 새로운 실행 순서는 이 동작을 단순화합니다. 이제 노드는 데이터를 받을 때만 실행되며, 다중 입력 노드는 실행되기 위해 최소한 하나의 입력에서 데이터를 필요로 합니다.

기존 워크플로우는 레거시 순서를 사용하고 새로운 워크플로우는 v1 순서를 사용하여 실행됩니다. [워크플로우 설정](/workflows/settings.md)에서 각 워크플로우의 실행 순서를 구성할 수 있습니다.

[PR #4238](https://github.com/n8n-io/n8n/pull/4238){:target=_blank .external link}, [PR #6246](https://github.com/n8n-io/n8n/pull/6246){:target=_blank .external link}, [PR #6507](https://github.com/n8n-io/n8n/pull/6507){:target=_blank .external link}

## 지원 중단

### MySQL 및 MariaDB

n8n은 n8n의 스토리지 백엔드로 MySQL 및 MariaDB에 대한 지원을 제거했습니다. 이러한 데이터베이스 시스템은 소수의 사용자만 사용하지만 지속적인 개발 및 유지 관리 노력이 필요합니다. n8n은 더 나은 호환성과 장기적인 지원을 위해 PostgreSQL로 마이그레이션할 것을 권장합니다.

[PR #6189](https://github.com/n8n-io/n8n/pull/6189){:target=_blank .external link}

### EXECUTIONS_PROCESS 및 "own" 모드

이전에는 `EXECUTIONS_PROCESS` 환경 변수를 사용하여 실행이 `main` 프로세스에서 실행되어야 하는지 또는 `own` 프로세스에서 실행되어야 하는지를 지정할 수 있었습니다. 이 옵션과 `own` 모드는 이제 더 이상 사용되지 않으며 향후 n8n 버전에서 제거될 예정입니다. 이는 미미한 이점을 제공하면서 코드 복잡성을 증가시켰기 때문입니다. n8n 1.0부터 `main`이 새로운 기본값이 됩니다.

`main` 모드에서는 `own` 모드보다 실행이 훨씬 빠르게 시작됩니다. 그러나 워크플로우가 사용 가능한 메모리보다 더 많은 메모리를 소비하면 작업자 스레드뿐만 아니라 전체 n8n 애플리케이션이 충돌할 수 있습니다. 이를 완화하려면 충분한 시스템 리소스를 할당하거나 [큐 모드](/hosting/scaling/queue-mode.md)를 구성하여 여러 작업자에게 실행을 분산해야 합니다.

[PR #6196](https://github.com/n8n-io/n8n/pull/6196){:target=_blank .external link}

## 주요 변경 사항

### 도커

#### 권한 변경

도커 기반 배포를 사용할 때 n8n 프로세스는 이제 `root` 대신 `node` 사용자에 의해 실행됩니다. 이 변경으로 보안이 강화됩니다.

_n8n을 시작할 때 n8n 컨테이너 로그에 권한 오류가 나타나면 도커 호스트에서 다음 명령을 실행하여 권한을 업데이트해야 할 수 있습니다._

```bash
docker run --rm -it --user root -v ~/.n8n:/home/node/.n8n --entrypoint chown n8nio/base:16 -R node:node /home/node/.n8n
```

#### 이미지 제거

Debian 및 RHEL 이미지를 제거했습니다. 이러한 이미지를 사용하고 있었다면 사용하는 이미지를 변경해야 합니다. 이러한 이미지 중 하나를 기반으로 사용자 지정 이미지를 만들지 않는 한 오류가 발생하지 않아야 합니다.

#### 진입점 변경

컨테이너의 진입점이 변경되어 더 이상 n8n 명령을 지정할 필요가 없습니다. 이전에 `n8n worker --concurrency=5`를 실행했다면 이제 `worker --concurrency=5`입니다.

[PR #6365](https://github.com/n8n-io/n8n/pull/6365){:target=_blank .external link}

### 표현식 오류로 인한 워크플로우 실패

워크플로우 실행은 존재하지 않는 노드를 참조하는 것과 같은 표현식의 구문 또는 런타임 오류로 인해 실패할 수 있습니다. 표현식은 이미 프런트엔드에서 오류를 발생시키지만, 이 변경으로 n8n은 이전에 자동으로 무시되었던 백엔드에서도 오류를 발생시킵니다. 실패한 워크플로우에 대한 알림을 받으려면 워크플로우 설정에서 "오류 워크플로우"를 설정하는 것이 좋습니다.

[PR #6352](https://github.com/n8n-io/n8n/pull/6352){:target=_blank .external link}

### 필수 소유자 계정

이 변경으로 [사용자 관리](/user-management/index.md)가 필수가 되며 BasicAuth 및 외부 JWT와 같은 다른 인증 방법에 대한 지원이 제거됩니다. [n8n.cloud](https://n8n.cloud/){:target=_blank .external link} 또는 사용자 지정 요금제에서 허용되는 사용자 수는 구독에 따라 여전히 다릅니다.

[PR #6362](https://github.com/n8n-io/n8n/pull/6362){:target=_blank .external link}

### 사용자 지정 노드 설치 디렉토리

n8n은 더 이상 전역 `node_modules` 디렉토리에서 사용자 지정 노드를 로드하지 않습니다. 대신 `~/.n8n/custom`(또는 `N8N_CUSTOM_EXTENSIONS`에 의해 정의된 디렉토리)에 설치(또는 링크)해야 합니다. npm 패키지인 사용자 지정 노드는 `~/.n8n/nodes`에 위치합니다.
전역 `node_modules` 디렉토리에 `npm link`를 사용하여 연결된 사용자 지정 노드가 있는 경우, 대신 `~/.n8n/nodes`에 다시 연결해야 합니다.

[PR #6396](https://github.com/n8n-io/n8n/pull/6396){:target=_blank .external link}

### 웹소켓

`N8N_PUSH_BACKEND` 환경 변수를 사용하여 사용자 인터페이스에 업데이트를 푸시하는 두 가지 사용 가능한 방법 중 하나인 `sse` 및 `websocket`을 구성할 수 있습니다. n8n 1.0부터 `websocket`이 기본 방법입니다.

[PR #6196](https://github.com/n8n-io/n8n/pull/6196){:target=_blank .external link}

### 날짜 변환 함수

n8n은 날짜에 대해 작동하는 다양한 변환 함수를 제공합니다. 이러한 함수는 자바스크립트 `Date` 또는 Luxon `DateTime` 객체를 반환할 수 있습니다. 새로운 동작에서는 반환 유형이 항상 입력과 일치합니다. `Date`에서 날짜 변환 함수를 호출하면 `Date`를 반환합니다. 마찬가지로 `DateTime` 객체에서 호출하면 `DateTime` 객체를 반환합니다.

이 변경의 영향을 받을 수 있는 워크플로우 및 노드를 식별하려면 이 [유틸리티 워크플로우](https://n8n.io/workflows/1929-v1-helper-find-params-with-affected-expressions/){:target=_blank .external link}를 사용할 수 있습니다.

날짜 변환 함수에 대한 자세한 내용은 [공식 문서](/code/builtin/data-transformation-functions/dates.md)를 참조하십시오.

[PR #6435](https://github.com/n8n-io/n8n/pull/6435){:target=_blank .external link}

### 실행 데이터 보존

n8n 1.0부터 모든 성공, 실패 및 수동 워크플로우 실행이 기본적으로 저장됩니다. 이러한 설정은 "워크플로우 설정"에서 각 워크플로우에 대해 수정하거나 각 환경 변수를 사용하여 전역적으로 수정할 수 있습니다. 또한 `EXECUTIONS_DATA_PRUNE` 설정이 기본적으로 활성화되며 `EXECUTIONS_DATA_PRUNE_MAX_COUNT`는 10,000으로 설정됩니다. 이러한 기본 설정은 SQLite를 사용할 때 성능 저하를 방지하도록 설계되었습니다. 개별 요구 사항 및 시스템 용량에 따라 구성해야 합니다.

[PR #6577](https://github.com/n8n-io/n8n/pull/6577){:target=_blank .external link}

### N8N_USE_DEPRECATED_REQUEST_LIB 제거됨

레거시 `request` 라이브러리는 한동안 더 이상 사용되지 않았습니다. n8n 1.0부터 `N8N_USE_DEPRECATED_REQUEST_LIB` 환경 변수를 설정하여 HTTP 요청 노드에서 이전 버전으로 대체하는 기능이 완전히 제거되었습니다. HTTP 요청 노드는 이제 항상 새로운 `HttpRequest` 인터페이스를 사용합니다.

사용자 지정 노드를 빌드하는 경우 새 인터페이스로 마이그레이션하는 방법에 대한 자세한 내용은 [HTTP 요청 도우미](/integrations/creating-nodes/build/reference/http-helpers.md)를 참조하십시오.

[PR #6413](https://github.com/n8n-io/n8n/pull/6413){:target=_blank .external link}

### WEBHOOK_TUNNEL_URL 제거됨

버전 0.227.0부터 n8n은 `WEBHOOK_TUNNEL_URL` 구성 옵션의 이름을 `WEBHOOK_URL`로 변경했습니다. n8n 1.0에서는 `WEBHOOK_TUNNEL_URL`이 제거되었습니다. 새 이름을 반영하도록 설정을 업데이트하십시오. 이 구성 옵션에 대한 자세한 내용은 [문서](/hosting/configuration/configuration-examples/webhook-url.md)를 참조하십시오.

[PR #1408](https://github.com/n8n-io/n8n/pull/1408){:target=_blank .external link}

### 노드 16 지원 제거

n8n은 이제 노드 18.17.0 이상이 필요합니다.

## n8n 1.0으로 업데이트

1. n8n의 전체 백업을 만듭니다.
2. n8n은 n8n 1.x로 업데이트하기 전에 최신 n8n 0.x 릴리스로 업데이트할 것을 권장합니다. 이렇게 하면 잠재적인 문제를 올바른 릴리스로 정확히 찾아낼 수 있습니다. n8n 0.x가 문제 없이 시작되는지 확인한 후 다음 단계로 진행하십시오.
3. 위의 [지원 중단](#지원-중단) 및 [주요-변경-사항](#주요-변경-사항) 섹션을 주의 깊게 읽고 설정에 미치는 영향을 평가하십시오.
4. n8n 1.0으로 업데이트:
	* 베타 기간(2023년 7월 24일 이전): 도커를 사용하는 경우 `next` 도커 이미지를 가져옵니다.
	* 2023년 7월 24일 이후: 도커를 사용하는 경우 `latest` 도커 이미지를 가져옵니다.
5. 문제가 발생하면 이전 n8n 버전을 다시 배포하고 백업을 복원하십시오.

## 문제 보고

_n8n 1.0으로 업데이트하는 과정에서 문제가 발생하면 커뮤니티 [포럼](https://community.n8n.io/){:target=_blank .external link}에서 도움을 요청하십시오._

## 감사합니다

잠시 시간을 내어 지속적인 지원과 피드백을 보내주신 모든 사용자에게 감사의 말씀을 전합니다. 여러분의 기여는 n8n을 최고의 자동화 도구로 만드는 데 매우 중요합니다. 버전 1.0 및 그 이후 릴리스를 진행하면서 여러분과 계속 협력하게 되어 기쁩니다. 저희 여정에 함께해주셔서 감사합니다!