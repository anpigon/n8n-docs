---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
contentType: tutorial
---

# npm

npm은 로컬 컴퓨터에서 n8n을 시작하는 빠른 방법입니다. [Node.js](https://nodejs.org/en/){:target=_blank .external-link}가 설치되어 있어야 합니다. n8n에는 Node.js 18 이상이 필요합니다.

--8<-- "_snippets/self-hosting/installation/latest-next-version.md"

## npx로 n8n 사용해보기

npx를 사용하여 설치하지 않고 n8n을 사용해 볼 수 있습니다.

터미널에서 다음을 실행합니다.

```bash
npx n8n
```

이 명령은 n8n을 시작하는 데 필요한 모든 것을 다운로드합니다. 그런 다음 [http://localhost:5678](http://localhost:5678){:target=_blank .external-link}을 열어 n8n에 액세스하고 워크플로우 빌드를 시작할 수 있습니다.

## npm으로 전역 설치

n8n을 전역으로 설치하려면 npm을 사용하십시오.

```bash
npm install n8n -g
```

n8n의 특정 버전을 설치하거나 업데이트하려면 `@` 구문을 사용하여 버전을 지정하십시오. 예를 들어:

```bash
npm install -g n8n@0.126.1
```

`next`를 설치하려면:

```bash
npm install -g n8n@next
```

설치 후 다음을 실행하여 n8n을 시작하십시오.

```bash
n8n
# 또는
n8n start
```


### 다음 단계

[빠른 시작](/try-it-out/index.md)을 사용하여 n8n을 사용해 보십시오.

## 업데이트

n8n 인스턴스를 `최신` 버전으로 업데이트하려면 다음을 실행하십시오.

```bash
npm update -g n8n
```

`next` 버전을 설치하려면:

```bash
npm install -g n8n@next
```

--8<-- "_snippets/self-hosting/installation/tunnel.md"

`--tunnel`로 n8n을 시작하려면 다음을 실행하십시오.

```bash
n8n start --tunnel
```

## 업그레이드 되돌리기

돌아가려는 이전 버전을 설치하십시오.

업그레이드에 데이터베이스 마이그레이션이 포함된 경우:

1. 기능 설명서 및 릴리스 노트를 확인하여 수동으로 변경해야 할 사항이 있는지 확인하십시오.
2. 현재 버전에서 `n8n db:revert`를 실행하여 데이터베이스를 롤백하십시오. 둘 이상의 데이터베이스 마이그레이션을 되돌리려면 이 프로세스를 반복해야 합니다.

## Windows 문제 해결

Windows에서 n8n을 실행하는 데 문제가 있는 경우 Node.js 환경이 올바르게 설정되었는지 확인하십시오. Microsoft의 [Windows에 NodeJS 설치](https://learn.microsoft.com/en-us/windows/dev-environment/javascript/nodejs-on-windows){:target=_blank .external-link} 가이드를 따르십시오.
