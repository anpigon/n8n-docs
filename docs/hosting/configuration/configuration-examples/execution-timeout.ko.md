---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 워크플로우 시간 초과 설정 구성
description: 워크플로우가 실행될 수 있는 시간을 결정하기 위해 실행 시간 초과를 설정합니다.
contentType: howto
---

# 워크플로우 시간 초과 설정 구성

워크플로우는 이 시간(초) 후에 시간 초과되어 취소됩니다. 워크플로우가 주 프로세스에서 실행되는 경우 소프트 시간 초과가 발생합니다(현재 노드가 완료된 후 적용됨). 워크플로우가 자체 프로세스에서 실행되는 경우 n8n은 먼저 소프트 시간 초과를 시도한 다음 지정된 시간 초과 기간의 5분의 1을 기다린 후 프로세스를 종료합니다.

`EXECUTIONS_TIMEOUT` 기본값은 `-1`입니다. 예를 들어 시간 초과를 1시간으로 설정하려면 다음과 같이 하십시오.

```bash
export EXECUTIONS_TIMEOUT=3600
```

각 워크플로우에 대해 최대 실행 시간(초)을 개별적으로 설정할 수도 있습니다. 예를 들어 최대 실행 시간을 2시간으로 설정하려면 다음과 같이 하십시오.

```bash
export EXECUTIONS_TIMEOUT_MAX=7200
```
이러한 변수에 대한 자세한 내용은 [환경 변수 참조](/hosting/configuration/environment-variables/executions.md)를 참조하십시오.
