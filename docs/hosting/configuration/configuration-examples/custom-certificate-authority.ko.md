---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: n8n이 자체 인증 기관을 사용하도록 구성
description: 서비스에 연결할 때 자체 서명된 인증서와 함께 작동하도록 n8n 컨테이너를 사용자 정의합니다.
contentType: howto
---

# n8n이 자체 인증 기관 또는 자체 서명된 인증서를 사용하도록 구성

자체 인증 기관(CA) 또는 자체 서명된 인증서를 n8n에 추가할 수 있습니다. 즉, 잠재적인 보안 위험인 모든 잘못된 인증서를 신뢰하는 대신 특정 SSL 인증서를 신뢰할 수 있습니다.

/// note | 버전 1.42.0에서 사용 가능
이 기능은 버전 1.42.0 이상에서만 사용할 수 있습니다.
///

이 기능을 사용하려면 인증서를 폴더에 넣고 해당 폴더를 컨테이너의 `/opt/custom-certificates`에 마운트해야 합니다.

## Docker

아래 예제에서는 명령을 실행하는 디렉토리 또는 docker compose 파일 옆에 인증서가 포함된 `pki`라는 폴더가 있다고 가정합니다.

### Docker CLI
CLI를 사용하는 경우 명령줄에서 `-v` 플래그를 사용할 수 있습니다.

```bash
docker run -it --rm \
 --name n8n \
 -p 5678:5678 \
 -v ./pki:/opt/custom-certificates \
 docker.n8n.io/n8nio/n8n
```

### Docker Compose

```yaml
name: n8n
services:
    n8n:
        volumes:
            - ./pki:/opt/custom-certificates
        container_name: n8n
        ports:
            - 5678:5678
        image: docker.n8n.io/n8nio/n8n
```

가져온 인증서에 올바른 권한을 부여해야 합니다. 컨테이너가 실행 중일 때 이 작업을 수행할 수 있습니다(컨테이너 이름으로 n8n 가정).

```bash
docker exec --user 0 n8n chown -R 1000:1000 /opt/custom-certificates
```
