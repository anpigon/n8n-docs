---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
contentType: tutorial
---

# DigitalOcean에서 n8n 호스팅

이 호스팅 가이드는 DigitalOcean 드롭릿에서 n8n을 자체 호스팅하는 방법을 보여줍니다. 다음을 사용합니다.

* [Caddy](https://caddyserver.com){:target="_blank" .external-link}(리버스 프록시)를 사용하여 인터넷에서 드롭릿에 액세스할 수 있도록 합니다. Caddy는 또한 n8n 인스턴스에 대한 SSL/TLS 인증서를 자동으로 생성하고 관리합니다.
* [Docker Compose](https://docs.docker.com/compose/){:target="_blank" .external-link}를 사용하여 애플리케이션 구성 요소와 이들이 함께 작동하는 방식을 생성하고 정의합니다.

--8<-- "_snippets/self-hosting/warning.md"

--8<-- "_snippets/self-hosting/installation/latest-next-version.md"

## 드롭릿 생성

1. DigitalOcean에 [로그인](https://cloud.digitalocean.com/login){:target=_blank .external-link}합니다.
2. 드롭릿을 호스팅할 프로젝트를 선택하거나 [새 프로젝트를 생성](https://docs.digitalocean.com/products/projects/how-to/create/){:target=_blank .external-link}합니다.
3. 프로젝트에서 **관리** 메뉴의 **드롭릿**을 선택합니다.
4. **마켓플레이스** 탭에서 사용 가능한 [Docker 이미지](https://marketplace.digitalocean.com/apps/docker){:target="_blank" .external-link}를 사용하여 [새 드롭릿을 생성](https://docs.digitalocean.com/products/droplets/how-to/create/){:target="_blank" .external-link}합니다.

/// note | 드롭릿 리소스
드롭릿을 생성할 때 DigitalOcean은 플랜을 선택하도록 요청합니다. 대부분의 사용 수준에서는 기본 공유 CPU 플랜으로 충분합니다.
///
/// note | SSH 키 또는 암호
DigitalOcean에서는 SSH 키와 암호 기반 인증 중에서 선택할 수 있습니다. SSH 키가 더 안전한 것으로 간주됩니다.
///
## 드롭릿에 로그인하고 새 사용자 생성

이 가이드의 나머지 부분에서는 SSH를 사용하여 터미널을 통해 드롭릿에 로그인해야 합니다. 자세한 내용은 [SSH로 드롭릿에 연결하는 방법](https://docs.digitalocean.com/products/droplets/how-to/connect-with-ssh/){:target="_blank" .external-link}을 참조하십시오.

루트 사용자로 작업하지 않으려면 새 사용자를 만들어야 합니다.

1. 루트로 로그인합니다.
2. 새 사용자를 만듭니다.
	```shell
	adduser <username>
	```
3. CLI의 프롬프트에 따라 사용자 생성을 완료합니다.
4. 새 사용자에게 관리자 권한을 부여합니다.
	```shell
	usermod -aG sudo <username>
	```
	이제 명령 앞에 `sudo`를 사용하여 슈퍼유저 권한으로 명령을 실행할 수 있습니다.
5. 단계에 따라 새 사용자에 대한 SSH를 설정합니다. [공개 키 인증 추가](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-14-04#step-four-add-public-key-authentication-recommended){:target=_blank .external-link}.
5. 드롭릿에서 로그아웃합니다.
6. 새 사용자로 SSH를 사용하여 로그인합니다.

## 구성 리포지토리 복제

Docker Compose, n8n 및 Caddy에는 일련의 폴더와 구성 파일이 필요합니다. [이 리포지토리](https://github.com/n8n-io/n8n-docker-caddy){:target=_blank .external-link}에서 드롭릿에 로그인한 사용자의 홈 폴더로 복제할 수 있습니다. 다음 단계에서는 변경할 파일과 변경할 내용을 알려줍니다.

다음 명령으로 리포지토리를 복제합니다.

```shell
git clone https://github.com/n8n-io/n8n-docker-caddy.git
```

그리고 복제한 리포지토리의 루트로 디렉토리를 변경합니다.

```shell
cd n8n-docker-caddy
```

## 기본 폴더 및 파일

호스트 운영 체제(DigitalOcean 드롭릿)는 생성한 두 폴더를 Docker 컨테이너에 복사하여 Docker에서 사용할 수 있도록 합니다. 두 폴더는 다음과 같습니다.

- `caddy_config`: Caddy 구성 파일을 보관합니다.
- `local_files`: n8n을 사용하여 업로드하거나 추가하는 파일용 폴더입니다.

### Docker 볼륨 생성

재시작 간에 Caddy 캐시를 유지하고 시작 시간을 단축하려면 Docker가 재시작 간에 재사용하는 [Docker 볼륨](https://docs.docker.com/storage/volumes/){:target="_blank" .external-link}을 생성합니다.

```shell
sudo docker volume create caddy_data
```

n8n 데이터용 Docker 볼륨 생성:

```shell
sudo docker volume create n8n_data
```

## DNS 설정

n8n은 일반적으로 하위 도메인에서 작동합니다. 공급자와 함께 하위 도메인에 대한 DNS 레코드를 만들고 드롭릿의 IP 주소로 지정합니다. 이에 대한 정확한 단계는 DNS 공급자에 따라 다르지만 일반적으로 n8n 하위 도메인에 대한 새 "A" 레코드를 만들어야 합니다. DigitalOcean은 [DNS 용어, 구성 요소 및 개념 소개](https://www.digitalocean.com/community/tutorials/an-introduction-to-dns-terminology-components-and-concepts){:target="_blank" .external-link}를 제공합니다.

## 포트 열기

n8n은 웹 애플리케이션으로 실행되므로 드롭릿은 비보안 트래픽의 경우 포트 80, 보안 트래픽의 경우 포트 443에서 들어오는 트래픽 액세스를 허용해야 합니다.

다음 두 명령을 실행하여 드롭릿의 방화벽에서 다음 포트를 엽니다.

```shell
sudo ufw allow 80
sudo ufw allow 443
```

## n8n 구성

n8n은 Docker 컨테이너에서 실행되는 애플리케이션에 전달하기 위해 일부 환경 변수를 설정해야 합니다. 예제 `.env` 파일에는 자체 값으로 바꿔야 하는 자리 표시자가 포함되어 있습니다.

다음 명령으로 파일을 엽니다.

```shell
nano .env
```

파일에는 변경할 내용을 알 수 있도록 인라인 주석이 포함되어 있습니다.

자세한 내용은 [환경 변수](/hosting/configuration/environment-variables/index.md)를 참조하십시오.

## Docker Compose 파일

Docker Compose 파일(`docker-compose.yml`)은 이 경우 Caddy와 n8n과 같이 애플리케이션에 필요한 서비스를 정의합니다.

- Caddy 서비스 정의는 사용하는 포트와 컨테이너에 복사할 로컬 볼륨을 정의합니다.
- n8n 서비스 정의는 사용하는 포트, n8n이 실행하는 데 필요한 환경 변수(`.env` 파일에 일부 정의됨) 및 컨테이너에 복사해야 하는 볼륨을 정의합니다.

Docker Compose 파일은 `.env` 파일에 설정된 환경 변수를 사용하므로 내용을 변경할 필요는 없지만 내용을 보려면 다음 명령을 실행하십시오.

```shell
nano docker-compose.yml
```

## Caddy 구성

Caddy는 어떤 도메인을 제공해야 하는지, 외부 세계에 어떤 포트를 노출해야 하는지 알아야 합니다. `caddy_config` 폴더의 `Caddyfile` 파일을 편집합니다.

```shell
nano caddy_config/Caddyfile
```

자리 표시자 도메인을 자신의 도메인으로 변경합니다. 하위 도메인 이름을 n8n으로 지정하는 단계를 따랐다면 전체 도메인은 `n8n.example.com`과 유사합니다. `reverse_proxy` 설정의 `n8n`은 Caddy에게 `docker-compose.yml` 파일에 정의된 서비스 정의를 사용하도록 지시합니다.

```text
n8n.<domain>.<suffix> {
    reverse_proxy n8n:5678 {
      flush_interval -1
    }
}
```

`automate.example.com`을 사용했다면 `Caddyfile`은 다음과 같을 수 있습니다.

```text
automate.example.com {
    reverse_proxy n8n:5678 {
      flush_interval -1
    }
}
```

## Docker Compose 시작

다음 명령으로 n8n과 Caddy를 시작합니다.

```shell
sudo docker compose up -d
```

몇 분 정도 걸릴 수 있습니다.

## 설정 테스트

브라우저에서 이전에 정의한 하위 도메인과 도메인 이름으로 구성된 URL을 엽니다. 이전에 정의한 사용자 이름과 암호를 입력하면 n8n에 액세스할 수 있습니다.

## n8n 및 Caddy 중지

다음 명령으로 n8n과 Caddy를 중지할 수 있습니다.

```shell
sudo docker compose stop
```
## 업데이트

--8<-- "_snippets/self-hosting/installation/docker-compose-updating.md"

## 다음 단계

--8<-- "_snippets/self-hosting/installation/server-setups-next-steps.md"
