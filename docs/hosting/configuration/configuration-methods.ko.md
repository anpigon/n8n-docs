---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 구성 방법
description: n8n에 대한 환경 변수를 설정하는 방법입니다.
contentType: howto
---

# 구성

환경 변수를 사용하여 n8n의 설정을 변경할 수 있습니다. 사용 가능한 전체 구성 목록은 [환경 변수](/hosting/configuration/environment-variables/index.md)를 참조하십시오.

## 명령줄로 환경 변수 설정

### npm

npm의 경우 아래와 같이 `export` 명령을 사용하여 터미널에서 원하는 환경 변수를 설정하십시오.

```bash
export <variable>=<value>
```

### Docker

Docker에서는 명령줄에서 `-e` 플래그를 사용할 수 있습니다.

```bash
docker run -it --rm \
 --name n8n \
 -p 5678:5678 \
 -e N8N_TEMPLATES_ENABLED="false" \
 docker.n8n.io/n8nio/n8n
```

## 파일을 사용하여 환경 변수 설정

구성 파일을 사용하여 n8n을 구성할 수도 있습니다.

구성 파일에는 기본값과 다른 값만 정의하십시오. 여러 파일을 사용할 수 있습니다. 예를 들어, 일반 기본 설정이 있는 파일과 다른 환경에 대한 특정 값이 있는 파일을 가질 수 있습니다.

### npm

`N8N_CONFIG_FILES` 환경 변수를 사용하여 JSON 구성 파일의 경로를 설정하십시오.

```shell
# Bash - 단일 파일
export N8N_CONFIG_FILES=/<path-to-config>/my-config.json
# Bash - 여러 파일은 쉼표로 구분됩니다.
export N8N_CONFIG_FILES=/<path-to-config>/my-config.json,/<path-to-config>/production.json

# PowerShell - 단일 파일, 현재 사용자에 대해 유지
# 범위 설정(Process, User, Machine)은 Unix 시스템에 영향을 미치지 않습니다.
[Environment]::SetEnvironmentVariable('N8N_CONFIG_FILES', '<path-to-config>\config.json', 'User')
```

예제 파일:

```json
{
 "executions": {
  "saveDataOnSuccess": "none"
 },
 "generic": {
  "timezone": "Europe/Berlin"
 },
 "nodes": {
  "exclude": "["n8n-nodes-base.executeCommand","n8n-nodes-base.writeBinaryFile"]"
 }
}
```

/// note | JSON으로 서식 지정
[환경 변수 참조](/hosting/configuration/environment-variables/index.md)에서 항상 올바른 JSON을 알아낼 수는 없습니다. 예를 들어, `N8N_METRICS`를 `true`로 설정하려면 다음을 수행해야 합니다.

```json
{
	"endpoints": {
		"metrics": {
			"enable": true
		}
	}
}
```

예상되는 설정의 전체 세부 정보는 [소스 코드의 스키마 파일](https://github.com/n8n-io/n8n/blob/master/packages/cli/src/config/schema.ts){:target=_blank .external-link}을 참조하십시오.
///


### Docker

Docker에서는 `docker-compose.yaml` 파일의 `n8n: environment:` 요소에 환경 변수를 설정할 수 있습니다.

예를 들어:

```yaml
n8n:
    environment:
      - N8N_TEMPLATES_ENABLED=false
```

### 민감한 데이터를 별도 파일에 보관

개별 환경 변수에 `_FILE`을 추가하여 별도 파일에 구성을 제공할 수 있으므로 환경 변수를 사용하여 민감한 세부 정보를 전달하는 것을 피할 수 있습니다. n8n은 지정된 이름의 파일에서 데이터를 로드하므로 [Docker-Secrets](https://docs.docker.com/engine/swarm/secrets/){:target=_blank .external-link} 및 [Kubernetes-Secrets](https://kubernetes.io/docs/concepts/configuration/secret/){:target=_blank .external-link}에서 데이터를 로드할 수 있습니다.

각 변수에 대한 자세한 내용은 [환경 변수](/hosting/configuration/environment-variables/index.md)를 참조하십시오.

대부분의 환경 변수는 `_FILE` 접미사를 사용할 수 있지만 [자격 증명](/glossary.md#credential-n8n) 및 데이터베이스 구성과 같은 민감한 데이터에 더 유용합니다. 다음은 몇 가지 예입니다.

```yaml
CREDENTIALS_OVERWRITE_DATA_FILE=/path/to/credentials_data
DB_TYPE_FILE=/path/to/db_type
DB_POSTGRESDB_DATABASE_FILE=/path/to/database_name
DB_POSTGRESDB_HOST_FILE=/path/to/database_host
DB_POSTGRESDB_PORT_FILE=/path/to/database_port
DB_POSTGRESDB_USER_FILE=/path/to/database_user
DB_POSTGRESDB_PASSWORD_FILE=/path/to/database_password
DB_POSTGRESDB_SCHEMA_FILE=/path/to/database_schema
DB_POSTGRESDB_SSL_CA_FILE=/path/to/ssl_ca
DB_POSTGRESDB_SSL_CERT_FILE=/path/to/ssl_cert
DB_POSTGRESDB_SSL_KEY_FILE=/path/to/ssl_key
DB_POSTGRESDB_SSL_REJECT_UNAUTHORIZED_FILE=/path/to/ssl_reject_unauth
```
