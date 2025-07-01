---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 사용자 지정 암호화 키 설정
description: n8n이 자격 증명을 안전하게 암호화하도록 사용자 지정 암호화 키를 설정합니다.
contentType: howto
---

# 사용자 지정 암호화 키 설정

n8n은 첫 실행 시 자동으로 임의의 암호화 키를 생성하여
`~/.n8n` 폴더에 저장합니다. n8n은 해당 키를 사용하여 자격 증명을 암호화한 후
데이터베이스에 저장합니다. 키가 아직 설정 파일에 없는 경우
환경 변수를 사용하여 설정할 수 있으므로 n8n이
새 키를 생성하는 대신 사용자 지정 키를 사용합니다.

[큐 모드](/hosting/scaling/queue-mode.md)에서는 모든 워커에 대해 암호화 키 환경 변수를 지정해야 합니다.

```bash
export N8N_ENCRYPTION_KEY=<임의의 문자열>
```
이 변수에 대한 자세한 내용은 [환경 변수 참조](/hosting/configuration/environment-variables/deployment.md)를 참조하십시오.
