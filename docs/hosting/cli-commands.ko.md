---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
description: n8n에서 사용 가능한 CLI 명령어입니다.
contentType: reference
---

# n8n용 CLI 명령어

n8n에는 CLI(명령줄 인터페이스)가 포함되어 있어 n8n 편집기 대신 CLI를 사용하여 작업을 수행할 수 있습니다. 여기에는 워크플로우 시작, 워크플로우 및 자격 증명 내보내기 및 가져오기가 포함됩니다.

## CLI 명령어 실행

자체 호스팅 n8n과 함께 CLI 명령어를 사용할 수 있습니다. n8n을 설치하는 방법에 따라 명령어를 실행하는 방법이 다릅니다.

* npm: `n8n` 명령어를 직접 사용할 수 있습니다. 이 문서에서는 아래 예제에서 이 명령어를 사용합니다.
* Docker: `n8n` 명령어는 Docker 컨테이너 내에서 사용할 수 있습니다.

    ```sh
    docker exec -u node -it <n8n-container-name> <n8n-cli-command>
    ```

## 워크플로우 시작

CLI를 사용하여 직접 워크플로우를 시작할 수 있습니다.

ID로 저장된 워크플로우 실행:

```bash
n8n execute --id <ID>
```

## 워크플로우의 활성 상태 변경

CLI를 사용하여 워크플로우의 활성 상태를 변경할 수 있습니다.

/// note | 재시작 필요
이 명령어는 n8n 데이터베이스에서 작동합니다. n8n이 실행 중일 때 실행하면 변경 사항이 n8n을 다시 시작할 때까지 적용되지 않습니다.
///

ID로 워크플로우의 활성 상태를 false로 설정:

```bash
n8n update:workflow --id=<ID> --active=false
```

ID로 워크플로우의 활성 상태를 true로 설정:

```bash
n8n update:workflow --id=<ID> --active=true
```

모든 워크플로우의 활성 상태를 false로 설정:

```bash
n8n update:workflow --all --active=false
```

모든 워크플로우의 활성 상태를 true로 설정:

```bash
n8n update:workflow --all --active=true
```

## 워크플로우 및 자격 증명 내보내기

CLI를 사용하여 n8n에서 워크플로우 및 자격 증명을 내보낼 수 있습니다.

명령 플래그:

| 플래그 | 설명 |
|-------------|-------|
| --help | 도움말 프롬프트. |
| --all | 모든 워크플로우/자격 증명을 내보냅니다. |
| --backup | 백업을 위해 --all --pretty --separate를 설정합니다. 선택적으로 --output을 설정할 수 있습니다. |
| --id | 내보낼 워크플로우의 ID입니다. |
| --output | 별도 파일을 사용하는 경우 파일 이름 또는 디렉토리를 출력합니다. |
| --pretty | 더 읽기 쉬운 형식으로 출력을 포맷합니다. |
| --separate | 워크플로우당 하나의 파일을 내보냅니다(버전 관리에 유용). --output을 사용하여 디렉토리를 설정해야 합니다. |
| --decrypted | 자격 증명을 일반 텍스트 형식으로 내보냅니다. |

### 워크플로우

모든 워크플로우를 표준 출력(터미널)으로 내보내기:

```bash
n8n export:workflow --all
```

ID로 워크플로우를 내보내고 출력 파일 이름 지정:

```bash
n8n export:workflow --id=<ID> --output=file.json
```

모든 워크플로우를 단일 파일의 특정 디렉토리로 내보내기:

```bash
n8n export:workflow --all --output=backups/latest/file.json
```

`--backup` 플래그를 사용하여 모든 워크플로우를 특정 디렉토리로 내보내기(자세한 내용은 위 참조):

```bash
n8n export:workflow --backup --output=backups/latest/
```

### 자격 증명

모든 자격 증명을 표준 출력(터미널)으로 내보내기:

```bash
n8n export:credentials --all
```

ID로 자격 증명을 내보내고 출력 파일 이름 지정:

```bash
n8n export:credentials --id=<ID> --output=file.json
```

모든 자격 증명을 단일 파일의 특정 디렉토리로 내보내기:

```bash
n8n export:credentials --all --output=backups/latest/file.json
```

`--backup` 플래그를 사용하여 모든 자격 증명을 특정 디렉토리로 내보내기(자세한 내용은 위 참조):

```bash
n8n export:credentials --backup --output=backups/latest/
```

모든 자격 증명을 일반 텍스트 형식으로 내보냅니다. 이를 사용하여 구성 파일에 다른 비밀 키가 있는 한 설치에서 다른 설치로 마이그레이션할 수 있습니다.

/// warning | 민감한 정보
모든 민감한 정보는 파일에 표시됩니다.
///

```bash
n8n export:credentials --all --decrypted --output=backups/decrypted.json
```

## 워크플로우 및 자격 증명 가져오기

CLI를 사용하여 n8n에서 워크플로우 및 자격 증명을 가져올 수 있습니다.

/// warning | ID 업데이트
워크플로우 및 자격 증명을 내보낼 때 n8n은 해당 ID도 내보냅니다. 기존 데이터베이스에 동일한 ID를 가진 워크플로우 및 자격 증명이 있는 경우 덮어쓰여집니다. 이를 방지하려면 가져오기 전에 ID를 삭제하거나 변경하십시오.
///

사용 가능한 플래그:

| 플래그 | 설명 |
|------|-------------|
| --help | 도움말 프롬프트. |
| --input | --separate를 사용하는 경우 입력 파일 이름 또는 디렉토리. |
| --projectId | 지정된 프로젝트로 워크플로우 또는 자격 증명을 가져옵니다. `--userId`와 함께 사용할 수 없습니다. |
| --separate | --input에서 제공하는 디렉토리에서 `*.json` 파일을 가져옵니다. |
| --userId | 지정된 사용자로 워크플로우 또는 자격 증명을 가져옵니다. `--projectId`와 함께 사용할 수 없습니다. |

/// note | SQLite로 마이그레이션
n8n은 워크플로우 및 자격 증명 이름을 128자로 제한하지만 SQLite는 크기 제한을 적용하지 않습니다.

이로 인해 가져오기 프로세스 중에 **열 이름에 비해 데이터가 너무 깁니다**와 같은 오류가 발생할 수 있습니다.

이 경우 n8n 인터페이스에서 이름을 편집하고 다시 내보내거나 가져오기 전에 JSON 파일을 직접 편집할 수 있습니다.
///

### 워크플로우

특정 파일에서 워크플로우 가져오기:

```bash
n8n import:workflow --input=file.json
```

지정된 디렉토리에서 모든 워크플로우 파일을 JSON으로 가져오기:

```bash
n8n import:workflow --separate --input=backups/latest/
```

### 자격 증명

특정 파일에서 자격 증명 가져오기:

```bash
n8n import:credentials --input=file.json
```

지정된 디렉토리에서 모든 자격 증명 파일을 JSON으로 가져오기:

```bash
n8n import:credentials --separate --input=backups/latest/
```

## 라이선스

### 지우기

n8n 데이터베이스에서 기존 라이선스를 지우고 n8n을 기본 기능으로 재설정합니다.

```sh
n8n license:clear
```

라이선스에 [부동 인타이틀먼트](/glossary.md#entitlement-n8n)가 포함된 경우 이 명령을 실행하면 해당 인타이틀먼트를 풀로 다시 해제하여 다른 인스턴스에서 사용할 수 있도록 시도합니다.

### 정보

기존 라이선스에 대한 정보 표시:

```sh
n8n license:info
```

## 사용자 관리

n8n CLI를 사용하여 사용자 관리를 재설정할 수 있습니다. 이렇게 하면 사용자 관리가 설정 전 상태로 돌아갑니다. 모든 사용자 계정이 제거됩니다.

비밀번호를 잊어버렸고 이메일로 비밀번호 재설정을 수행하도록 SMTP가 설정되어 있지 않은 경우 이 기능을 사용하십시오.

```sh
n8n user-management:reset
```

### 사용자에 대해 MFA 비활성화

사용자가 복구 코드를 분실한 경우 이 명령으로 사용자에 대해 MFA를 비활성화할 수 있습니다. 그러면 사용자는 다시 로그인하여 MFA를 다시 설정할 수 있습니다.

```sh
n8n mfa:disable --email=johndoe@example.com
```

### LDAP 비활성화

아래 명령을 사용하여 LDAP 설정을 재설정할 수 있습니다.

```sh
n8n ldap:reset
```

## 커뮤니티 노드 및 자격 증명 제거

n8n CLI를 사용하여 [커뮤니티 노드](/integrations/community-nodes/installation/index.md)를 관리할 수 있습니다. 현재로서는 커뮤니티 노드 및 자격 증명만 제거할 수 있으며, 이는 커뮤니티 노드가 불안정성을 유발하는 경우에 유용합니다.

명령 플래그:

 | 플래그 | 설명 |
 |--------------|----------------------------------------------------------------------------------------------------------------------------------|
 | --help | CLI 도움말을 표시합니다. |
 | --credential | 자격 증명 유형입니다. 노드의 `<NODE>.credential.ts` 파일을 방문하여 `name` 값을 가져와 이 값을 얻습니다. |
 | --package | 커뮤니티 노드의 패키지 이름입니다. |
 | --uninstall | 노드를 제거합니다. |
 | --userId | 자격 증명을 소유한 사용자의 ID입니다. 자체 호스팅에서는 데이터베이스를 쿼리합니다. 클라우드에서는 API 키로 API를 쿼리합니다. |

### 노드

패키지 이름으로 커뮤니티 노드 제거:

```sh
n8n community-node --uninstall --package <COMMUNITY_NODE_NAME>
```

예를 들어, [Evolution API 커뮤니티 노드](https://www.npmjs.com/package/n8n-nodes-evolution-api)를 제거하려면 다음을 입력합니다.

```sh
n8n community-node --uninstall --package n8n-nodes-evolution-api
```

### 자격 증명

커뮤니티 노드 자격 증명 제거:

```sh
n8n community-node --uninstall --credential <CREDENTIAL_TYPE> --userId <ID>
```

예를 들어, [Evolution API 커뮤니티 노드 자격 증명](https://www.npmjs.com/package/n8n-nodes-evolution-api)을 제거하려면 [리포지토리](https://github.com/oriondesign2015/n8n-nodes-evolution-api)를 방문하여 [`credentials.ts` 파일](https://github.com/oriondesign2015/n8n-nodes-evolution-api/blob/main/credentials/EvolutionApi.credentials.ts)로 이동하여 `name`을 찾습니다.

```sh
n8n community-node --uninstall --credential evolutionApi --userId 1234
```

## 보안 감사

n8n 인스턴스에서 [보안 감사](/hosting/securing/security-audit.md)를 실행하여 일반적인 보안 문제를 감지할 수 있습니다.

```sh
n8n audit
```
