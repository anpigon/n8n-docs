---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 대기
description: 워크플로우 실행을 대기시키는 방법입니다.
contentType: howto
---

# 대기

대기를 사용하면 워크플로우 실행 중에 일시 중지한 다음 동일한 데이터로 워크플로우가 중단된 지점에서 다시 시작할 수 있습니다. 이는 서비스에 대한 호출 속도를 제한하거나 외부 이벤트가 완료될 때까지 기다려야 하는 경우에 유용합니다. 지정된 기간 동안 또는 웹훅이 실행될 때까지 기다릴 수 있습니다.

워크플로우를 대기시키려면 [대기](/integrations/builtin/core-nodes/n8n-nodes-base.wait.md) 노드를 사용합니다. 사용 세부 정보는 노드 설명서를 참조하십시오.

n8n은 [속도 제한 및 외부 이벤트 대기](https://n8n.io/workflows/1749-rate-limiting-and-waiting-for-external-events/){:target=_blank .external-link}의 기본 예제가 포함된 워크플로우 템플릿을 제공합니다.
