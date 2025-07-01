---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 데이터베이스 환경 변수
description: 자체 호스팅 n8n 인스턴스에 대한 환경 변수로 데이터베이스를 설정하고 구성합니다.
contentType: reference
tags:
  - 환경 변수
hide:
  - toc
  - tags
---

# 데이터베이스 환경 변수

--8<-- "_snippets/self-hosting/file-based-configuration.md"

기본적으로 n8n은 SQLite를 사용합니다. n8n은 PostgreSQL도 지원합니다. n8n은 v1.0에서 [MySQL 및 MariaDB에 대한 지원을 제거했습니다](/1-0-migration-checklist.md#mysql-and-mariadb).

이 페이지에서는 자체 호스팅 n8n 인스턴스에 대해 선택한 데이터베이스를 구성하기 위한 환경 변수를 간략하게 설명합니다.

| 변수 | 유형 | 기본값 | 설명 |
| :------- | :---- | :------- | :---------- |
| `DB_TYPE`<br>/`_FILE` | 열거형 문자열:<br> `sqlite`, `postgresdb` | `sqlite` | 사용할 데이터베이스입니다. |
| `DB_TABLE_PREFIX` | * | - | 테이블 이름에 사용할 접두사입니다. |
| `DB_PING_INTERVAL_SECONDS` | 숫자 | `2` | 연결이 아직 살아 있는지 확인하기 위해 데이터베이스에 대한 핑 간격(초)입니다. |

## PostgreSQL

| 변수 | 유형 | 기본값 | 설명 |
| :------- | :---- | :------- | :---------- |
| `DB_POSTGRESDB_DATABASE`<br>/`_FILE` | 문자열 | `n8n` | PostgreSQL 데이터베이스의 이름입니다. |
| `DB_POSTGRESDB_HOST`<br>/`_FILE` | 문자열 | `localhost` | PostgreSQL 호스트입니다. |
| `DB_POSTGRESDB_PORT`<br>/`_FILE` | 숫자 | `5432` | PostgreSQL 포트입니다. |
| `DB_POSTGRESDB_USER`<br>/`_FILE` | 문자열 | `postgres` | PostgreSQL 사용자입니다. |
| `DB_POSTGRESDB_PASSWORD`<br>/`_FILE` | 문자열 | - | PostgreSQL 암호입니다. |
| `DB_POSTGRESDB_POOL_SIZE`<br>/`_FILE` | 숫자 | `2` | n8n이 가져야 하는 병렬 열린 Postgres 연결 수를 제어합니다. 늘리면 리소스 활용에 도움이 될 수 있지만 연결이 너무 많으면 성능이 저하될 수 있습니다. |
| `DB_POSTGRESDB_CONNECTION_TIMEOUT`<br>/`_FILE` | 숫자 | `20000` | Postgres 연결 시간 초과(ms)입니다.
| `DB_POSTGRESDB_IDLE_CONNECTION_TIMEOUT`<br>/`_FILE` | 숫자 | `30000` | 유휴 연결이 유휴 상태로 인해 제거될 수 있기까지의 시간입니다.
| `DB_POSTGRESDB_SCHEMA`<br>/`_FILE` | 문자열 | `public` | PostgreSQL 스키마입니다. |
| `DB_POSTGRESDB_SSL_ENABLED`<br>/`_FILE` | 부울 | `false` | SSL을 활성화할지 여부입니다. `DB_POSTGRESDB_SSL_CA`, `DB_POSTGRESDB_SSL_CERT` 또는 `DB_POSTGRESDB_SSL_KEY`가 정의된 경우 자동으로 활성화됩니다. |
| `DB_POSTGRESDB_SSL_CA`<br>/`_FILE` | 문자열 | - | PostgreSQL SSL 인증 기관입니다. |
| `DB_POSTGRESDB_SSL_CERT`<br>/`_FILE` | 문자열 | - | PostgreSQL SSL 인증서입니다. |
| `DB_POSTGRESDB_SSL_KEY`<br>/`_FILE` | 문자열 | - | PostgreSQL SSL 키입니다. |
| `DB_POSTGRESDB_SSL_REJECT_UNAUTHORIZED`<br>/`_FILE` | 부울 | `true` | n8n이 승인되지 않은 SSL 연결을 거부해야 하는지(true) 여부(false)입니다. |

## SQLite

| 변수 | 유형 | 기본값 | 설명 |
| :------- | :---- | :------- | :---------- |
| `DB_SQLITE_POOL_SIZE` | 숫자 | `0` | SQLite 파일을 [WAL 모드](https://www.sqlite.org/wal.html) 또는 [롤백 저널 모드](https://www.sqlite.org/lockingv3.html#rollback)로 열지 여부를 제어합니다. 0으로 설정하면 롤백 저널 모드를 사용합니다. 0보다 크면 구성할 병렬 SQL 읽기 연결 수를 결정하는 값과 함께 WAL 모드를 사용합니다. WAL 모드는 롤백 저널 모드보다 훨씬 성능이 뛰어나고 안정적입니다. |
| `DB_SQLITE_VACUUM_ON_STARTUP` | 부울 | `false` | 시작 시 [VACUUM](https://www.sqlite.org/lang_vacuum.html){:target="_blank" .external-link} 작업을 실행하여 데이터베이스를 다시 빌드합니다. 파일 크기를 줄이고 인덱스를 최적화합니다. 이것은 장기 실행 차단 작업이며 시작 시간을 늘립니다. |
