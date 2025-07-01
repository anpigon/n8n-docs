---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 사용자 폴더 경로 지정
description: 사용자별 데이터를 저장하는 폴더의 위치를 지정합니다.
contentType: howto
---

# 사용자 폴더 경로 지정

n8n은 암호화 키, SQLite 데이터베이스 파일 및
터널 ID(사용된 경우)와 같은 사용자별 데이터를 n8n을 시작한 사용자의 하위 폴더 `.n8n`에 저장합니다. 환경 변수를 사용하여 사용자 폴더를 덮어쓸 수 있습니다.

```bash
export N8N_USER_FOLDER=/home/jim/n8n
```
이 변수에 대한 자세한 내용은 [환경 변수 참조](/hosting/configuration/environment-variables/deployment.md)를 참조하십시오.
