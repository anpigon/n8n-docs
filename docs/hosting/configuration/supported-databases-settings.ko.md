---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
contentType: reference
---

# 지원되는 데이터베이스

기본적으로 n8n은 SQLite를 사용하여 자격 증명, 과거 실행 및 워크플로우를 저장합니다. n8n은 PostgresDB도 지원합니다.

## 공유 설정

다음 환경 변수는 모든 데이터베이스에서 사용됩니다.

 - `DB_TABLE_PREFIX` (기본값: -) - 테이블 이름 접두사

## PostgresDB

PostgresDB를 데이터베이스로 사용하려면 다음 환경 변수를 제공할 수 있습니다.

 - `DB_TYPE=postgresdb`
 - `DB_POSTGRESDB_DATABASE` (기본값: 'n8n')
 - `DB_POSTGRESDB_HOST` (기본값: 'localhost')
 - `DB_POSTGRESDB_PORT` (기본값: 5432)
 - `DB_POSTGRESDB_USER` (기본값: 'postgres')
 - `DB_POSTGRESDB_PASSWORD` (기본값: 비어 있음)
 - `DB_POSTGRESDB_SCHEMA` (기본값: 'public')
 - `DB_POSTGRESDB_SSL_CA` (기본값: 정의되지 않음): 연결 유효성 검사에 사용되는 서버의 CA 인증서 경로(기회적 암호화는 지원되지 않음)
 - `DB_POSTGRESDB_SSL_CERT` (기본값: 정의되지 않음): 클라이언트의 TLS 인증서 경로
 - `DB_POSTGRESDB_SSL_KEY` (기본값: 정의되지 않음): 인증서에 해당하는 클라이언트의 개인 키 경로
 - `DB_POSTGRESDB_SSL_REJECT_UNAUTHORIZED` (기본값: true): 유효성 검사에 실패한 TLS 연결을 거부해야 하는 경우

```bash
export DB_TYPE=postgresdb
export DB_POSTGRESDB_DATABASE=n8n
export DB_POSTGRESDB_HOST=postgresdb
export DB_POSTGRESDB_PORT=5432
export DB_POSTGRESDB_USER=n8n
export DB_POSTGRESDB_PASSWORD=n8n
export DB_POSTGRESDB_SCHEMA=n8n

# 선택 사항:
export DB_POSTGRESDB_SSL_CA=$(pwd)/ca.crt
export DB_POSTGRESDB_SSL_REJECT_UNAUTHORIZED=false

n8n start
```

### 필요한 권한

n8n은 사용하는 테이블의 스키마를 생성하고 수정해야 합니다.

권장 권한:

```sql
CREATE DATABASE n8n-db;
CREATE USER n8n-user WITH PASSWORD 'random-password';
GRANT ALL PRIVILEGES ON DATABASE n8n-db TO n8n-user;
```

### TLS

다음 구성 중에서 선택할 수 있습니다.

- 선언하지 않음(기본값): `SSL=off`로 연결
- CA 및 권한 없는 플래그만 선언: `SSL=on`으로 연결하고 서버 서명 확인
- `_{CERT,KEY}` 및 위 항목 선언: 클라이언트 TLS 인증에 인증서 및 키 사용

## SQLite

정의된 것이 없으면 사용되는 기본 데이터베이스입니다.

데이터베이스 파일은 다음에 있습니다.
`~/.n8n/database.sqlite`
