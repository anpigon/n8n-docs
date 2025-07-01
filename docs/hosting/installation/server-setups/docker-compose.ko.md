---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
contentType: tutorial
description: Docker Compose를 사용하여 n8n 설치 및 실행
---

# Docker-Compose

이미 Docker 및 Docker-Compose를 설치했다면 [3단계](#3-dns-setup)부터 시작할 수 있습니다.

[n8n-hosting 리포지토리](https://github.com/n8n-io/n8n-hosting)에서 다양한 아키텍처에 대한 Docker Compose 구성을 찾을 수 있습니다.

--8<-- "_snippets/self-hosting/warning.md"

--8<-- "_snippets/self-hosting/installation/latest-next-version.md"

## 1. Docker 및 Docker Compose 설치

Docker 및 Docker Compose를 설치하는 방법은 사용하는 Linux 배포판에 따라 다를 수 있습니다. [Docker](https://docs.docker.com/engine/install/) 및 [Docker Compose](https://docs.docker.com/compose/install/) 설치 설명서에서 자세한 지침을 찾을 수 있습니다. 다음 예는 Ubuntu용입니다.

```bash
# 호환되지 않거나 오래된 Docker 구현이 있는 경우 제거
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done
# 필수 패키지 설치
sudo apt-get update
sudo apt-get install ca-certificates curl
# 리포지토리 서명 키 다운로드
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
# 리포지토리 구성
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Docker 및 Docker Compose 업데이트 및 설치
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

다음을 입력하여 Docker 및 Docker Compose를 사용할 수 있는지 확인합니다.

```bash
docker --version
docker compose version
```

## 2. 선택 사항: 루트가 아닌 사용자 액세스

선택적으로 `sudo` 명령 없이 Docker를 실행할 수 있는 액세스 권한을 부여할 수 있습니다.

현재 로그인한 사용자에게 액세스 권한을 부여하려면(해당 사용자가 `sudo` 액세스 권한이 있다고 가정) 다음을 실행합니다.

```bash
sudo usermod -aG docker ${USER}
# 기본 그룹을 변경하지 않고 현재 세션에 `docker` 그룹 멤버십 등록
exec sg docker newgrp
```

다른 사용자에게 액세스 권한을 부여하려면 `<USER_TO_RUN_DOCKER>`를 적절한 사용자 이름으로 대체하여 다음을 입력합니다.

```bash
sudo usermod -aG docker <USER_TO_RUN_DOCKER>
```

새 그룹 권한에 액세스하려면 해당 사용자의 기존 세션에서 `exec sg docker newgrp`를 실행해야 합니다.

다음을 입력하여 현재 세션이 `docker` 그룹을 인식하는지 확인할 수 있습니다.

```bash
groups
```

## 3. DNS 설정

n8n을 온라인 또는 네트워크에서 호스팅하려면 서버를 가리키는 전용 하위 도메인을 만듭니다.

하위 도메인을 적절하게 라우팅하려면 A 레코드를 추가합니다.

* **유형**: A
* **이름**: `n8n` (또는 원하는 하위 도메인)
* **IP 주소**: (서버의 IP 주소)

## 4. `.env` 파일 만들기

n8n 환경 구성 및 Docker Compose 파일을 저장할 프로젝트 디렉토리를 만들고 내부로 이동합니다.

```bash
mkdir n8n-compose
cd n8n-compose
```

`n8n-compose` 디렉토리 내에서 n8n 인스턴스의 세부 정보를 사용자 지정하기 위해 `.env` 파일을 만듭니다. 자신의 정보와 일치하도록 변경합니다.

```bash title=".env 파일"
# DOMAIN_NAME과 SUBDOMAIN은 n8n에 연결할 수 있는 위치를 함께 결정합니다.
# 서비스할 최상위 도메인
DOMAIN_NAME=example.com

# 서비스할 하위 도메인
SUBDOMAIN=n8n

# 위 예는 n8n을 https://n8n.example.com에서 서비스합니다.

# Cron 및 기타 스케줄링 노드에서 사용하는 시간대를 설정하는 선택적 시간대
# 설정하지 않으면 뉴욕이 기본값입니다.
GENERIC_TIMEZONE=Europe/Berlin

# TLS/SSL 인증서 생성에 사용할 이메일 주소
SSL_EMAIL=user@example.com
```

## 5. 로컬 파일 디렉토리 만들기

프로젝트 디렉토리 내에서 n8n 인스턴스와 호스트 시스템 간에 파일을 공유하기 위해 `local-files`라는 디렉토리를 만듭니다(예: [디스크에서 파일 읽기/쓰기 노드](/integrations/builtin/core-nodes/n8n-nodes-base.readwritefile.md) 사용).

```bash
mkdir local-files
```

아래 Docker Compose 파일은 이 디렉토리를 자동으로 만들 수 있지만 수동으로 만들면 올바른 소유권 및 권한으로 생성됩니다.

## 6. Docker Compose 파일 만들기

`compose.yaml` 파일을 만듭니다. 파일에 다음을 붙여넣습니다.

```yaml title="compose.yaml 파일"
services:
  traefik:
    image: "traefik"
    restart: always
    command:
      - "--api.insecure=true"
      - "--providers.docker=true"
      - "--providers.docker.exposedbydefault=false"
      - "--entrypoints.web.address=:80"
      - "--entrypoints.web.http.redirections.entryPoint.to=websecure"
      - "--entrypoints.web.http.redirections.entrypoint.scheme=https"
      - "--entrypoints.websecure.address=:443"
      - "--certificatesresolvers.mytlschallenge.acme.tlschallenge=true"
      - "--certificatesresolvers.mytlschallenge.acme.email=${SSL_EMAIL}"
      - "--certificatesresolvers.mytlschallenge.acme.storage=/letsencrypt/acme.json"
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - traefik_data:/letsencrypt
      - /var/run/docker.sock:/var/run/docker.sock:ro

  n8n:
    image: docker.n8n.io/n8nio/n8n
    restart: always
    ports:
      - "127.0.0.1:5678:5678"
    labels:
      - traefik.enable=true
      - traefik.http.routers.n8n.rule=Host(`${SUBDOMAIN}.${DOMAIN_NAME}`)
      - traefik.http.routers.n8n.tls=true
      - traefik.http.routers.n8n.entrypoints=web,websecure
      - traefik.http.routers.n8n.tls.certresolver=mytlschallenge
      - traefik.http.middlewares.n8n.headers.SSLRedirect=true
      - traefik.http.middlewares.n8n.headers.STSSeconds=315360000
      - traefik.http.middlewares.n8n.headers.browserXSSFilter=true
      - traefik.http.middlewares.n8n.headers.contentTypeNosniff=true
      - traefik.http.middlewares.n8n.headers.forceSTSHeader=true
      - traefik.http.middlewares.n8n.headers.SSLHost=${DOMAIN_NAME}
      - traefik.http.middlewares.n8n.headers.STSIncludeSubdomains=true
      - traefik.http.middlewares.n8n.headers.STSPreload=true
      - traefik.http.routers.n8n.middlewares=n8n@docker
    environment:
      - N8N_HOST=${SUBDOMAIN}.${DOMAIN_NAME}
      - N8N_PORT=5678
      - N8N_PROTOCOL=https
      - NODE_ENV=production
      - WEBHOOK_URL=https://${SUBDOMAIN}.${DOMAIN_NAME}/
      - GENERIC_TIMEZONE=${GENERIC_TIMEZONE}
    volumes:
      - n8n_data:/home/node/.n8n
      - ./local-files:/files

volumes:
  n8n_data:
  traefik_data:
```

위의 Docker Compose 파일은 n8n용 컨테이너 하나와 TLS/SSL 인증서를 관리하고 라우팅을 처리하는 애플리케이션 프록시인 [traefik](https://github.com/traefik/traefik)을 실행하는 컨테이너 하나, 이렇게 두 개의 컨테이너를 구성합니다.

또한 두 개의 [Docker 볼륨](https://docs.docker.com/engine/storage/volumes/)을 만들고 이전에 만든 `local-files` 디렉토리를 마운트합니다.

   | 이름 | 유형 | 컨테이너 마운트 | 설명 |
   |-----------------|-------------------------------------------------------------|-------------------|-------------------------------------------------------------------------------------------------------------------------------------|
   | `n8n_data` | [볼륨](https://docs.docker.com/engine/storage/volumes/) | `/home/node/.n8n` | n8n이 SQLite 데이터베이스 파일과 암호화 키를 저장하는 위치입니다. |
   | `traefik_data` | [볼륨](https://docs.docker.com/engine/storage/volumes/) | `/letsencrypt` | traefik이 TLS/SSL 인증서 데이터를 저장하는 위치입니다. |
   | `./local-files` | [바인드](https://docs.docker.com/engine/storage/bind-mounts/) | `/files` | n8n 인스턴스와 호스트 간에 공유되는 로컬 디렉토리입니다. n8n에서는 `/files` 경로를 사용하여 이 디렉토리에서 읽고 씁니다. |

## 7. Docker Compose 시작

이제 다음을 입력하여 n8n을 시작할 수 있습니다.

```bash
sudo docker compose up -d
```

컨테이너를 중지하려면 다음을 입력합니다.

```bash
sudo docker compose stop
```

## 8. 완료

이제 `.env` 파일 구성에서 정의한 하위 도메인 + 도메인 조합을 사용하여 n8n에 연결할 수 있습니다. 위 예는 `https://n8n.example.com`이 됩니다.

n8n은 일반 HTTP가 아닌 보안 HTTPS를 사용해서만 액세스할 수 있습니다.

## 다음 단계

--8<-- "_snippets/self-hosting/installation/server-setups-next-steps.md"
