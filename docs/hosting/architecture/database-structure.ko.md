#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
description: n8n 데이터베이스 구조 이해하기
contentType: explanation
---

# 데이터베이스 구조

이 페이지는 n8n 데이터베이스의 각 테이블의 목적을 설명합니다.

## 데이터베이스 및 쿼리 기술

기본적으로 n8n은 SQLite를 데이터베이스로 사용합니다. 다른 데이터베이스를 사용하는 경우 구조는 비슷하지만, 데이터베이스에 따라 데이터 유형이 다를 수 있습니다.

n8n은 쿼리 및 마이그레이션을 위해 [TypeORM](https://github.com/typeorm/typeorm){:target=_blank .external-link}을 사용합니다.

n8n 데이터베이스를 검사하려면 오픈 소스 범용 데이터베이스 도구인 [DBeaver](https://dbeaver.io){:target=_blank .external-link}를 사용할 수 있습니다.

## 테이블

다음은 n8n이 설정 중에 생성하는 테이블입니다.
<!-- vale off -->
### auth_identity

[SAML](/user-management/saml/index.md) 사용 시 외부 인증 공급자의 세부 정보를 저장합니다.

### auth_provider_sync_history

SAML 연결 기록을 저장합니다.

### credentials_entity

통합 인증에 사용되는 [자격 증명](/glossary.md#credential-n8n)을 저장합니다.

### event_destinations

[로그 스트리밍](/log-streaming.md)의 대상 구성을 포함합니다.

### execution_data

실행 시점의 워크플로우와 실행 데이터를 포함합니다.

### execution_entity

저장된 모든 워크플로우 실행을 저장합니다. 워크플로우 설정은 n8n이 저장하는 실행에 영향을 줄 수 있습니다.

### execution_metadata

[사용자 지정 실행 데이터](/workflows/executions/custom-executions-data.md)를 저장합니다.

### installed_nodes

n8n 인스턴스에 설치된 [커뮤니티 노드](/integrations/community-nodes/installation/index.md)를 나열합니다.

### installed_packages

n8n 인스턴스에 설치된 npm 커뮤니티 노드 패키지의 세부 정보입니다. [installed_nodes](#installed_nodes)는 각 개별 노드를 나열합니다. `installed_packages`는 둘 이상의 노드를 포함할 수 있는 npm 패키지를 나열합니다.

### migrations

모든 데이터베이스 마이그레이션 로그입니다. TypeORM 문서에서 [마이그레이션](https://github.com/typeorm/typeorm/blob/master/docs/migrations.md){:target=_blank .external-link}에 대해 자세히 알아보세요.

### project

인스턴스의 [프로젝트](/user-management/rbac/projects.md)를 나열합니다.

### project_relation

사용자의 [역할 유형](/user-management/rbac/role-types.md)을 포함하여 사용자와 [프로젝트](/user-management/rbac/projects.md) 간의 관계를 설명합니다.

### role

현재 사용되지 않습니다. 향후 사용자 지정 역할 작업에 사용될 예정입니다.

### settings

사용자 지정 인스턴스 설정을 기록합니다. 환경 변수를 사용하여 제어할 수 없는 설정입니다. 여기에는 다음이 포함됩니다.

* 인스턴스 소유자가 설정되었는지 여부
* 사용자가 소유자 및 사용자 관리 설정을 건너뛰도록 선택했는지 여부
* 라이선스 키

### shared_credentials

자격 증명을 사용자에게 매핑합니다.

### shared_workflow

워크플로우를 사용자에게 매핑합니다.

### tag_entity

n8n 인스턴스에서 생성된 모든 워크플로우 태그입니다. 이 테이블은 태그를 나열합니다. [workflows_tags](#workflows_tags)는 어떤 워크플로우에 어떤 태그가 있는지 기록합니다.

### user

사용자 데이터를 포함합니다.

### variables

[변수](/code/variables.md)를 저장합니다.

### webhook_entity

n8n 인스턴스의 워크플로우에 있는 활성 웹훅을 기록합니다. 이는 웹훅 노드에서 사용되는 웹훅뿐만 아니라 모든 트리거 노드에서 사용하는 모든 활성 웹훅을 포함합니다.

### workflow_entity

n8n 인스턴스에 저장된 워크플로우입니다.

### workflow_history

이전 버전의 워크플로우를 저장합니다.

### workflow_statistics

워크플로우 ID와 해당 상태를 계산합니다.

### workflows_tags

태그를 워크플로우에 매핑합니다. [tag_entity](#tag_entity)에는 태그 세부 정보가 포함됩니다.

## 엔티티 관계 다이어그램 (ERD)

!["n8n ERD"](/_images/hosting/architecture/n8n-database-diagram.png)

<!-- vale on -->