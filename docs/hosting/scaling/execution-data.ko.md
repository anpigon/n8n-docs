#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
contentType: howto
---

# 실행 데이터

실행 설정 및 볼륨에 따라 n8n 데이터베이스의 크기가 커져 저장 공간이 부족해질 수 있습니다.

이를 방지하기 위해 n8n은 불필요한 데이터를 저장하지 않고 오래된 실행 데이터를 정리하도록 설정하는 것을 권장합니다.

이를 위해 해당 [환경 변수](/hosting/configuration/environment-variables/executions.md)를 구성하십시오.

## 저장된 데이터 줄이기

/// note | 워크플로우 수준의 구성
[워크플로우 설정](/workflows/settings.md)을 사용하여 개별 워크플로우 기준으로 이러한 설정을 구성할 수도 있습니다.
///
n8n이 저장하는 실행 데이터를 선택할 수 있습니다. 예를 들어 `오류`가 발생하는 실행만 저장할 수 있습니다.

```sh
# npm
# 오류로 끝나는 실행 저장
export EXECUTIONS_DATA_SAVE_ON_ERROR=all

# 성공적인 실행 저장
export EXECUTIONS_DATA_SAVE_ON_SUCCESS=all

# 각 실행에 대한 노드 진행률을 저장하지 않음
export EXECUTIONS_DATA_SAVE_ON_PROGRESS=false

# 수동으로 시작된 실행을 저장하지 않음
export EXECUTIONS_DATA_SAVE_MANUAL_EXECUTIONS=false

```

```sh
# Docker
docker run -it --rm \
 --name n8n \
 -p 5678:5678 \
 -e EXECUTIONS_DATA_SAVE_ON_ERROR=all \
 -e EXECUTIONS_DATA_SAVE_ON_SUCCESS=none \
 -e EXECUTIONS_DATA_SAVE_ON_PROGRESS=true \
 -e EXECUTIONS_DATA_SAVE_MANUAL_EXECUTIONS=false \
 docker.n8n.io/n8nio/n8n
```

```yaml
# Docker Compose
n8n:
    environment:
      - EXECUTIONS_DATA_SAVE_ON_ERROR=all
      - EXECUTIONS_DATA_SAVE_ON_SUCCESS=none
      - EXECUTIONS_DATA_SAVE_ON_PROGRESS=true
      - EXECUTIONS_DATA_SAVE_MANUAL_EXECUTIONS=false
```

## 데이터 정리 활성화

데이터 정리를 활성화하여 지정된 시간이 지나면 완료된 실행을 자동으로 삭제할 수 있습니다. `EXECUTIONS_DATA_MAX_AGE`를 설정하지 않으면 기본값은 336시간(14일)입니다.

`EXECUTIONS_DATA_PRUNE_MAX_COUNT`를 사용하여 `EXECUTIONS_DATA_MAX_AGE`에 설정된 시간 전에 완료된 실행 데이터를 정리하도록 선택할 수 있습니다. 이렇게 하면 데이터베이스에 저장할 최대 실행 수가 설정됩니다. 한도에 도달하면 n8n은 가장 오래된 실행 레코드를 삭제하기 시작합니다. 이는 특히 SQLite를 사용하는 경우 데이터베이스 성능 문제에 도움이 될 수 있습니다. 데이터베이스 크기는 설정한 한도를 초과할 수 있습니다. 실행이 완료되지 않은 오래된 실행은 삭제 대상이 되더라도 삭제되지 않습니다.

```sh
# npm
# 자동 데이터 정리 활성화
export EXECUTIONS_DATA_PRUNE=true

# n8n이 데이터를 삭제하는 실행 후 시간(시간)
export EXECUTIONS_DATA_MAX_AGE=168

# 저장할 실행 수
export EXECUTIONS_DATA_PRUNE_MAX_COUNT=50000
```

```sh
# Docker
docker run -it --rm \
 --name n8n \
 -p 5678:5678 \
 -e EXECUTIONS_DATA_PRUNE=true \
 -e EXECUTIONS_DATA_MAX_AGE=168 \
 docker.n8n.io/n8nio/n8n
```

```yaml
# Docker Compose
n8n:
    environment:
      - EXECUTIONS_DATA_PRUNE=true
      - EXECUTIONS_DATA_MAX_AGE=168
	  	- EXECUTIONS_DATA_PRUNE_MAX_COUNT=50000
```

/// note | SQLite
기본 SQLite 데이터베이스를 사용하여 n8n을 실행하는 경우 정리된 데이터의 디스크 공간은 자동으로 해제되지 않고 향후 실행 데이터에 재사용됩니다. 이 공간을 해제하려면 `DB_SQLITE_VACUUM_ON_STARTUP` [환경 변수](/hosting/configuration/environment-variables/database.md#sqlite)를 구성하거나 [VACUUM](https://www.sqlite.org/lang_vacuum.html){:target=_blank .external-link} 작업을 수동으로 실행하십시오.
///

--8<-- "_snippets/self-hosting/scaling/binary-data-pruning.md"
