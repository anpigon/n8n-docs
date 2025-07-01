---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 작업 실행기 강화
description: "자체 호스팅 n8n 인스턴스에 대한 더 나은 격리를 위해 작업 실행기를 강화합니다."
contentType: howto
---

# 작업 실행기 강화

[작업 실행기](/hosting/configuration/task-runners.md)는 [코드 노드](/integrations/builtin/core-nodes/n8n-nodes-base.code/index.md)의 코드를 실행하는 역할을 합니다. 코드 노드 실행은 안전하지만 다음 권장 사항에 따라 작업 실행기를 더욱 강화할 수 있습니다.

## 외부 모드에서 사이드카로 작업 실행기 실행

핵심 n8n 프로세스와 코드 노드의 코드 간의 격리를 높이려면 [외부 모드](/hosting/configuration/task-runners.md#setting-up-external-mode)에서 작업 실행기를 실행하십시오. 외부 작업 실행기는 별도의 컨테이너로 시작되어 코드 노드에 정의된 JavaScript를 실행하기 위한 완전히 격리된 환경을 제공합니다.
