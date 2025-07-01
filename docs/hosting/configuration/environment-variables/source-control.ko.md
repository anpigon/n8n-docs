---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 소스 제어 환경 변수
description: 소스 제어 설정에 대한 기본 SSH 키 유형을 설정하는 환경 변수입니다.
contentType: reference
tags:
  - 환경 변수
hide:
  - toc
  - tags
---

# 소스 제어 환경 변수

--8<-- "_snippets/self-hosting/file-based-configuration.md"

n8n은 Git 기반 소스 제어를 사용하여 환경을 지원합니다. Git 리포지토리를 n8n 인스턴스에 연결하고 소스 제어를 구성하는 방법에 대한 자세한 내용은 [소스 제어 및 환경](/source-control-environments/setup.md)을 참조하십시오.

| 변수 | 유형 | 기본값 | 설명 |
| :------- | :---- | :------- | :---------- |
| `N8N_SOURCECONTROL_DEFAULT_SSH_KEY_TYPE` | 문자열 | `ed25519` | [소스 제어 설정](/source-control-environments/setup.md)에 대한 기본 SSH 키 유형으로 RSA를 만들려면 `rsa`로 설정합니다. |
