#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
contentType: howto
---

# n8n 로깅

로깅은 디버깅에 중요한 기능입니다. n8n은 [winston](https://www.npmjs.com/package/winston){:target=_blank .external-link} 로깅 라이브러리를 사용합니다.

/// note | 로그 스트리밍
n8n 자체 호스팅 엔터프라이즈 티어에는 이 문서에 설명된 로깅 옵션 외에 [로그 스트리밍](/log-streaming.md)이 포함됩니다.
///
## 설정

n8n에서 로깅을 설정하려면 다음 환경 변수를 설정해야 합니다([구성 파일](/hosting/configuration/environment-variables/index.md)에서도 값을 설정할 수 있음)

| 구성 파일의 설정 | 환경 변수 사용 | 설명 |
|-----------------------------------|-----------------------------|-------------|
| n8n.log.level | N8N_LOG_LEVEL | 로그 출력 수준입니다. 사용 가능한 옵션은 (가장 낮은 수준에서 가장 높은 수준으로) error, warn, info 및 debug입니다. 기본값은 `info`입니다. 이러한 옵션에 대한 자세한 내용은 [여기](#log-levels)에서 확인할 수 있습니다. |
| n8n.log.output | N8N_LOG_OUTPUT | 로그를 출력할 위치입니다. 사용 가능한 옵션은 `console` 및 `file`입니다. 여러 값은 쉼표(`,`)로 구분하여 사용할 수 있습니다. 기본적으로 `console`이 사용됩니다. |
| n8n.log.file.location | N8N_LOG_FILE_LOCATION | 로그 파일 위치이며, 로그 출력이 파일로 설정된 경우에만 사용됩니다. 기본적으로 `<n8nFolderPath>/logs/n8n.log`가 사용됩니다. |
| n8n.log.file.maxsize | N8N_LOG_FILE_SIZE_MAX | 각 로그 파일의 최대 크기(MB)입니다. 기본적으로 n8n은 16MB를 사용합니다. |
| n8n.log.file.maxcount | N8N_LOG_FILE_COUNT_MAX | 보관할 최대 로그 파일 수입니다. 기본값은 100입니다. 이 값은 워커를 사용할 때 설정해야 합니다. |


```bash
# 로깅 수준을 'debug'로 설정
export N8N_LOG_LEVEL=debug

# 로그 출력을 콘솔과 로그 파일 모두로 설정
export N8N_LOG_OUTPUT=console,file

# 로그 파일의 저장 위치 설정
export N8N_LOG_FILE_LOCATION=/home/jim/n8n/logs/n8n.log

# 각 로그 파일의 최대 크기를 50MB로 설정
export N8N_LOG_FILE_MAXSIZE=50

# 보관할 최대 로그 파일 수를 60으로 설정
export N8N_LOG_FILE_MAXCOUNT=60
```

### 로그 수준

n8n은 표준 로그 수준을 사용하여 다음을 보고합니다.

- `silent`: 아무것도 출력하지 않음
- `error`: 오류만 출력하고 다른 것은 출력하지 않음
- `warn`: 오류 및 경고 메시지 출력
- `info`: 진행 상황에 대한 유용한 정보 포함
- `debug`: 가장 상세한 출력. n8n은 문제 디버깅에 도움이 되는 많은 정보를 출력합니다.


## 개발

개발 중에 로그 메시지를 추가하는 것은 좋은 습관입니다. 오류 디버깅에 도움이 됩니다. 개발을 위한 로깅을 구성하려면 아래 가이드를 따르십시오.

### 구현 세부 정보

n8n은 `workflow` 패키지에 있는 `LoggerProxy` 클래스를 사용합니다. `Logger` 인스턴스를 전달하여 `LoggerProxy.init()`을 호출하면 사용 전에 클래스가 초기화됩니다.

초기화 프로세스는 한 번만 발생합니다. [`start.ts`](https://github.com/n8n-io/n8n/blob/master/packages/cli/src/commands/start.ts) 파일은 이미 이 프로세스를 수행합니다. 처음부터 새 명령을 만드는 경우 `LoggerProxy` 클래스를 초기화해야 합니다.

`cli` 패키지에서 `Logger` 구현이 생성되면 내보낸 모듈에서 `getInstance` 편의 메서드를 호출하여 얻을 수 있습니다.

이 프로세스가 작동하는 방식에 대한 자세한 내용은 [start.ts](https://github.com/n8n-io/n8n/blob/master/packages/cli/src/commands/start.ts) 파일을 확인하십시오.

### 로그 추가

프로젝트에서 `LoggerProxy` 클래스가 초기화되면 다른 파일로 가져와 로그를 추가할 수 있습니다.

모든 로깅 수준에 대해 편의 메서드가 제공되므로 `Logger.<logLevel>('<message>', ...meta)` 형식을 사용하여 필요할 때마다 새 로그를 추가할 수 있습니다. 여기서 `meta`는 `message` 외에 원하는 추가 속성을 나타냅니다.

위 예에서는 [위](#log-levels)에서 설명한 표준 로그 수준을 사용합니다. `message` 인수는 문자열이고 `meta`는 데이터 개체입니다.

```js
// LoggerProxy를 가져와야 합니다. 더 쉽게 만들기 위해 Logger로 이름을 바꿉니다.

import {
	LoggerProxy as Logger
} from 'n8n-workflow';

// 워크플로우 이름과 워크플로우 ID를 추가 메타데이터 속성으로 사용하여 트리거 함수의 정보 수준 로깅

Logger.info(`"${workflow.name}" 워크플로우에 대한 폴링 트리거가 시작되었습니다.`, {workflowName: workflow.name, workflowId: workflow.id});
```

새 로거를 만들 때 염두에 두어야 할 몇 가지 유용한 표준은 다음과 같습니다.

- 로그 메시지를 가능한 한 사람이 읽을 수 있도록 만듭니다. 예를 들어, 항상 이름을 따옴표로 묶습니다.
- 위 예의 워크플로우 이름과 같이 로그 메시지와 메타데이터에서 정보를 복제하는 것은 메시지를 검색하기 쉽고 메타데이터를 통해 필터링이 더 쉬워지므로 유용할 수 있습니다.
- 모든 로그에 여러 ID(예: `executionId`, `workflowId` 및 `sessionId`)를 포함합니다.
- 노드 이름 대신(또는 둘 다) 노드 유형을 사용하면 더 일관성이 있고 검색하기 쉽습니다.

## 프런트엔드 로그

현재 프런트엔드 로그는 사용할 수 없습니다. `Logger` 또는 `LoggerProxy`를 사용하면 `editor-ui` 패키지에서 오류가 발생합니다. 이 기능은 향후 버전에 구현될 예정입니다.