---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
contentType: tutorial
---

# Docker 설치

[Docker](https://www.docker.com/){:target=_blank .external-link}는 다음과 같은 이점을 제공합니다.

* 깨끗한 환경에 n8n을 설치합니다.
* 선호하는 데이터베이스를 더 쉽게 설정할 수 있습니다.
* Docker는 일관된 시스템을 제공하므로 다른 운영 체제로 인한 문제를 피할 수 있습니다.
* 운영 체제 및 도구의 차이로 인한 호환성 문제를 피할 수 있습니다.
* 새 호스트 또는 환경으로의 마이그레이션을 더 간단하게 만듭니다.

[Docker Compose](/hosting/installation/server-setups/docker-compose.md)와 함께 Docker에서 n8n을 사용할 수도 있습니다. [n8n-hosting 리포지토리](https://github.com/n8n-io/n8n-hosting)에서 다양한 아키텍처에 대한 Docker Compose 구성을 찾을 수 있습니다.

--8<-- "_snippets/self-hosting/warning.md"

## 전제 조건

진행하기 전에 [Docker Desktop](https://docs.docker.com/get-docker/){:target=_blank .external-link}을 설치하십시오.

/// note | Linux 사용자
Docker Desktop은 Mac 및 Windows에서 사용할 수 있습니다. Linux 사용자는 배포판에 대해 [Docker Engine](https://docs.docker.com/engine/install/) 및 [Docker Compose](https://docs.docker.com/compose/install/)를 개별적으로 설치해야 합니다.
///

--8<-- "_snippets/self-hosting/installation/latest-next-version.md"

## n8n 시작

터미널에서 다음을 실행합니다.

```sh
docker volume create n8n_data

docker run -it --rm --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n docker.n8n.io/n8nio/n8n
```

이 명령은 영구 데이터를 저장할 볼륨을 만들고, 필요한 n8n 이미지를 다운로드하고, 포트 `5678`에 노출된 컨테이너를 시작합니다. 컨테이너 재시작 사이에 작업을 저장하기 위해 로컬에 데이터를 유지하기 위해 도커 볼륨 `n8n_data`도 마운트합니다.

실행되면 다음을 열어 n8n에 액세스할 수 있습니다.
[http://localhost:5678](http://localhost:5678)

## PostgreSQL과 함께 사용

기본적으로 n8n은 SQLite를 사용하여 [자격 증명](/glossary.md#credential-n8n), 과거 실행 및 워크플로우를 저장합니다. n8n은 아래에 자세히 설명된 대로 환경 변수를 사용하여 구성할 수 있는 PostgreSQL도 지원합니다.

PostgreSQL을 사용하는 경우에도 `/home/node/.n8n` 폴더에 저장된 데이터를 유지하는 것이 중요합니다. 여기에는 n8n 사용자 데이터와 더 중요하게는 자격 증명에 대한 암호화 키가 포함됩니다. [n8n 터널](#n8n-with-tunnel)을 사용할 때 웹훅의 이름이기도 합니다.

n8n이 시작 시 `/home/node/.n8n` 디렉토리를 찾을 수 없으면 자동으로 하나를 만듭니다. 이 경우 다른 암호화 키로 n8n이 저장한 모든 기존 자격 증명은 더 이상 작동하지 않습니다.

/// note | 명심하세요
PostgreSQL과 함께 `/home/node/.n8n` 디렉토리를 유지하는 것이 권장되는 모범 사례이지만 명시적으로 필요하지는 않습니다. Docker 컨테이너를 시작할 때 [`N8N_ENCRYPTION_KEY` 환경 변수](/hosting/configuration/environment-variables/deployment.md)를 전달하여 암호화 키를 제공할 수 있습니다.
///

PostgreSQL과 함께 n8n을 사용하려면 다음 명령을 실행하고 자리 표시자(예: `<POSTGRES_USER>`)를 실제 값으로 바꿉니다.

```sh
docker volume create n8n_data

docker run -it --rm \
 --name n8n \
 -p 5678:5678 \
 -e DB_TYPE=postgresdb \
 -e DB_POSTGRESDB_DATABASE=<POSTGRES_DATABASE> \
 -e DB_POSTGRESDB_HOST=<POSTGRES_HOST> \
 -e DB_POSTGRESDB_PORT=<POSTGRES_PORT> \
 -e DB_POSTGRESDB_USER=<POSTGRES_USER> \
 -e DB_POSTGRESDB_SCHEMA=<POSTGRES_SCHEMA> \
 -e DB_POSTGRESDB_PASSWORD=<POSTGRES_PASSWORD> \
 -v n8n_data:/home/node/.n8n \
 docker.n8n.io/n8nio/n8n
```

[n8n 호스팅 리포지토리](https://github.com/n8n-io/n8n-hosting/tree/main/docker-compose/withPostgres)에서 PostgreSQL에 대한 전체 `docker-compose` 파일을 찾을 수 있습니다.

## 시간대 설정

n8n이 사용해야 하는 시간대를 정의하려면 [`GENERIC_TIMEZONE` 환경 변수](/hosting/configuration/environment-variables/timezone-localization.md)를 설정할 수 있습니다. [스케줄 트리거 노드](/integrations/builtin/core-nodes/n8n-nodes-base.scheduletrigger/index.md)와 같은 스케줄 지향 노드는 이를 사용하여 올바른 시간대를 결정합니다.

`TZ` 환경 변수를 사용하여 `date`와 같은 일부 스크립트 및 명령이 반환하는 시스템 시간대를 설정할 수 있습니다.

이 예에서는 두 변수에 대해 동일한 시간대를 설정합니다.

```sh
docker volume create n8n_data

docker run -it --rm \
 --name n8n \
 -p 5678:5678 \
 -e GENERIC_TIMEZONE="Europe/Berlin" \
 -e TZ="Europe/Berlin" \
 -v n8n_data:/home/node/.n8n \
 docker.n8n.io/n8nio/n8n
```

## 업데이트

n8n을 업데이트하려면 Docker Desktop에서 **이미지** 탭으로 이동하여 컨텍스트 메뉴에서 **가져오기**를 선택하여 최신 n8n 이미지를 다운로드합니다.

![Docker Desktop](/_images/hosting/installation/docker/docker_desktop.png)

명령줄을 사용하여 최신 또는 특정 버전을 가져올 수도 있습니다.

```sh
# 최신(안정) 버전 가져오기
docker pull docker.n8n.io/n8nio/n8n

# 특정 버전 가져오기
docker pull docker.n8n.io/n8nio/n8n:1.81.0

# 다음(불안정) 버전 가져오기
docker pull docker.n8n.io/n8nio/n8n:next
```

업데이트된 이미지를 가져온 후 n8n 컨테이너를 중지하고 다시 시작합니다. 명령줄을 사용할 수도 있습니다. 아래 명령에서 `<container_id>`를 첫 번째 명령에서 찾은 컨테이너 ID로 바꿉니다.

```sh
# 컨테이너 ID 찾기
docker ps -a

# `<container_id>`로 컨테이너 중지
docker stop <container_id>

# `<container_id>`로 컨테이너 제거
docker rm <container_id>

# 컨테이너 시작
docker run --name=<container_name> [options] -d docker.n8n.io/n8nio/n8n
```

### Docker Compose 업데이트

--8<-- "_snippets/self-hosting/installation/docker-compose-updating.md"

## 추가 자료

[Docker 이미지](https://github.com/n8n-io/n8n/tree/master/docker/images/n8n)의 README 파일에서 Docker 설정에 대한 자세한 정보를 찾을 수 있습니다.

--8<-- "_snippets/self-hosting/installation/tunnel.md"

다음을 실행하여 `--tunnel`로 n8n을 시작합니다.

```sh
docker volume create n8n_data

docker run -it --rm \
 --name n8n \
 -p 5678:5678 \
 -v n8n_data:/home/node/.n8n \
 docker.n8n.io/n8nio/n8n \
 start --tunnel
```

## 다음 단계

--8<-- "_snippets/self-hosting/installation/server-setups-next-steps.md"
