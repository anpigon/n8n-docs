#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 워크플로우 환경 변수
description: 기본 이름 지정, 온보딩 흐름 기본 설정, 태그 관리 및 호출자 정책 설정을 포함하여 n8n에서 워크플로우를 구성하는 환경 변수입니다.
contentType: reference
tags:
  - 환경 변수
hide:
  - toc
  - tags
---

# 워크플로우 환경 변수

--8<-- "_snippets/self-hosting/file-based-configuration.md"

| 변수 | 유형 | 기본값 | 설명 |
| :------- | :---- | :------- | :---------- |
| `N8N_ONBOARDING_FLOW_DISABLED` | 부울 | `false` | 새 워크플로우를 만들 때 온보딩 팁을 비활성화할지(true) 여부(false)입니다. |
| `N8N_WORKFLOW_ACTIVATION_BATCH_SIZE` | 숫자 | `1` | 시작 중에 동시에 활성화할 워크플로우 수입니다.
| `N8N_WORKFLOW_CALLER_POLICY_DEFAULT_OPTION` | 문자열 | `workflowsFromSameOwner` | 워크플로우를 호출할 수 있는 워크플로우입니다. 옵션은 `any`, `none`, `workflowsFromAList`, `workflowsFromSameOwner`입니다. 이 기능에는 [워크플로우 공유](/workflows/sharing.md)가 필요합니다. |
| `N8N_WORKFLOW_TAGS_DISABLED` | 부울 | `false` | 워크플로우 태그를 비활성화할지(true) 또는 태그를 활성화할지(false) 여부입니다. |
| `WORKFLOWS_DEFAULT_NAME` | 문자열 | `내 워크플로우` | 새 워크플로우에 사용되는 기본 이름입니다. |