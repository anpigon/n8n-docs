#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 노드 환경 변수
description: 자체 호스팅 n8n 인스턴스에서 노드 관리를 구성하는 환경 변수입니다.
contentType: reference
tags:
  - 환경 변수
hide:
  - toc
  - tags
---

# 노드 환경 변수

--8<-- "_snippets/self-hosting/file-based-configuration.md"

이 페이지에는 n8n에서 [노드](/glossary.md#node-n8n)를 관리하기 위한 환경 변수 구성 옵션이 나열되어 있으며, 여기에는 로드하거나 제외할 노드 지정, 코드 노드에서 내장 또는 외부 모듈 가져오기, 커뮤니티 노드 활성화가 포함됩니다.

| 변수 | 유형 | 기본값 | 설명 |
| :------- | :---- | :------- | :---------- |
| `NODES_INCLUDE` | 문자열 배열 | - | 로드할 노드를 지정합니다. |
| `NODES_EXCLUDE` | 문자열 배열 | - | 로드하지 않을 노드를 지정합니다. 예를 들어, 사용자가 신뢰할 수 없는 경우 보안 위험이 될 수 있는 노드를 차단하려면: `NODES_EXCLUDE: "["n8n-nodes-base.executeCommand", "n8n-nodes-base.readWriteFile"]"` |
| `NODE_FUNCTION_ALLOW_BUILTIN` | 문자열 | - | 사용자가 코드 노드에서 특정 내장 모듈을 가져올 수 있도록 허용합니다. 모두 허용하려면 *를 사용하십시오. n8n은 기본적으로 모듈 가져오기를 비활성화합니다. |
| `NODE_FUNCTION_ALLOW_EXTERNAL` | 문자열 | - | 사용자가 코드 노드에서 특정 외부 모듈(`n8n/node_modules`에서)을 가져올 수 있도록 허용합니다. n8n은 기본적으로 모듈 가져오기를 비활성화합니다. |
| `NODES_ERROR_TRIGGER_TYPE` | 문자열 | `n8n-nodes-base.errorTrigger` | 오류 트리거로 사용할 노드 유형을 지정합니다. |
| `N8N_CUSTOM_EXTENSIONS` | 문자열 | - | 사용자 지정 노드가 포함된 디렉토리의 경로를 지정합니다. |
| `N8N_COMMUNITY_PACKAGES_ENABLED` | 부울 | `true` | 커뮤니티 노드를 설치하고 로드하는 기능을 활성화(true) 또는 비활성화(false)합니다. false로 설정하면 개별 설정에 관계없이 확인된 커뮤니티 패키지와 확인되지 않은 커뮤니티 패키지를 모두 사용할 수 없습니다. |
| `N8N_COMMUNITY_PACKAGES_REGISTRY` | 문자열 | `https://registry.npmjs.org` | 커뮤니티 패키지를 가져올 NPM 레지스트리 URL입니다(라이선스 필요). |
| `N8N_VERIFIED_PACKAGES_ENABLED` | 부울 | `true` | `N8N_COMMUNITY_PACKAGES_ENABLED`가 true인 경우 이 변수는 설치 및 사용을 위해 노드 패널에 확인된 커뮤니티 노드를 표시할지(true) 또는 숨길지(false)를 제어합니다. |
| `N8N_UNVERIFIED_PACKAGES_ENABLED` | 부울 | `true` | `N8N_COMMUNITY_PACKAGES_ENABLED`가 true인 경우 이 변수는 NPM 레지스트리에서 확인되지 않은 커뮤니티 노드의 설치 및 사용을 활성화할지(true) 여부(false)를 제어합니다. |
| `N8N_COMMUNITY_PACKAGES_PREVENT_LOADING` | 부울 | `false` | 인스턴스 시작 시 설치된 커뮤니티 노드 로드를 방지(true)하거나 허용(false)합니다. 결함이 있는 노드가 인스턴스 시작을 방해하는 경우 이 기능을 사용하십시오. |