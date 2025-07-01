#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
contentType: tutorial
---

# Heroku에서 n8n 호스팅

이 호스팅 가이드는 Heroku에서 n8n을 자체 호스팅하는 방법을 보여줍니다. 다음을 사용합니다.


- [Docker Compose](https://docs.docker.com/compose/){:target="_blank" .external-link}를 사용하여 애플리케이션 구성 요소와 이들이 함께 작동하는 방식을 생성하고 정의합니다.
- [Heroku의 PostgreSQL 서비스](https://devcenter.heroku.com/categories/heroku-postgres){:target="_blank" .external-link}를 사용하여 n8n의 데이터 스토리지를 호스팅합니다.
- **Heroku에 배포** 버튼은 약간의 구성으로 원클릭 배포를 제공합니다.

--8<-- "_snippets/self-hosting/warning.md"

--8<-- "_snippets/self-hosting/installation/latest-next-version.md"


## 배포 템플릿을 사용하여 Heroku 프로젝트 생성

Heroku에 n8n을 배포하는 가장 빠른 방법은 **Heroku에 배포** 버튼을 사용하는 것입니다.

[![배포](https://www.herokucdn.com/deploy/button.svg)](https://dashboard.heroku.com/new?template=https://github.com/n8n-io/n8n-heroku/tree/main)

그러면 Heroku에서 **새 앱 만들기** 페이지가 열립니다. 프로젝트 이름을 설정하고 프로젝트를 배포할 지역을 선택합니다.

### 환경 변수 구성

Heroku는 `app.json` 파일의 `env` 섹션에 정의된 구성 옵션을 미리 채우며, 이는 n8n이 사용하는 환경 변수의 기본값도 설정합니다.

필요에 맞게 이러한 값을 변경할 수 있습니다. 다음 값을 변경해야 합니다.

- **N8N_ENCRYPTION_KEY**: n8n이 데이터베이스에 저장하기 전에 [사용자 계정 세부 정보를 암호화](/hosting/configuration/environment-variables/deployment.md)하는 데 사용합니다.
- **WEBHOOK_URL**: 웹훅이 올바른 URL을 갖도록 생성하는 애플리케이션 이름과 일치해야 합니다.

### n8n 배포

**앱 배포**를 선택합니다.

Heroku가 앱을 빌드하고 배포한 후 **앱 관리** 또는 애플리케이션 **보기** 링크를 제공합니다.

/// note | Heroku 및 DNS
도메인을 Heroku 애플리케이션에 연결하는 방법을 알아보려면 [Heroku 설명서](https://devcenter.heroku.com/categories/networking-dns){:target="_blank" .external-link}를 참조하십시오.
///
## 배포 템플릿 변경

[리포지토리](https://github.com/n8n-io/n8n-heroku){:target="_blank" .external-link}를 포크하고 포크에서 배포하여 배포 템플릿을 변경할 수 있습니다.

### Dockerfile

기본적으로 Dockerfile은 최신 n8n 이미지를 가져옵니다. 다른 또는 고정 버전을 사용하려면 `Dockerfile`의 맨 위 줄에 있는 이미지 태그를 업데이트하십시오.

### Heroku 및 포트 노출

Heroku는 Docker 기반 애플리케이션이 `EXPOSE` 명령으로 노출된 포트를 정의하는 것을 허용하지 않습니다. 대신 Heroku는 애플리케이션 런타임에 동적으로 채워지는 `PORT` 환경 변수를 제공합니다. `entrypoint.sh` 파일은 기본 Docker 이미지 명령을 재정의하여 Heroku가 제공하는 포트 변수를 대신 설정합니다. 그런 다음 웹 브라우저에서 포트 80으로 n8n에 액세스할 수 있습니다.

/// note | Heroku의 Docker 제한 사항
Heroku와 함께 Docker를 사용하는 제한 사항에 대한 자세한 내용은 [이 가이드](https://devcenter.heroku.com/articles/container-registry-and-runtime#unsupported-dockerfile-commands){:target="_blank" .external-link}를 참조하십시오.
///
### Heroku 구성

`heroku.yml` 파일은 Heroku에서 만들려는 애플리케이션을 정의합니다. 두 섹션으로 구성됩니다.

* `setup` > `addons`는 사용할 Heroku 애드온을 정의합니다. 이 경우 PostgreSQL 데이터베이스 애드온입니다.
* `build` 섹션은 Heroku가 애플리케이션을 빌드하는 방법을 정의합니다. 이 경우 Docker 빌드팩을 사용하여 제공된 `Dockerfile`을 기반으로 `web` 서비스를 빌드합니다.

## 다음 단계

--8<-- "_snippets/self-hosting/installation/server-setups-next-steps.md"