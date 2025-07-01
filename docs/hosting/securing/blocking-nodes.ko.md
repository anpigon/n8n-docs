#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 노드에 대한 액세스 차단
description: "n8n 사용자가 특정 노드에 액세스하는 것을 방지합니다."
contentType: howto
---

# 노드에 대한 액세스 차단

보안상의 이유로 사용자가 특정 n8n 노드에 액세스하거나 작업하는 것을 차단하고 싶을 수 있습니다. 이는 사용자가 신뢰할 수 없는 경우에 유용합니다.

`NODES_EXCLUDE` 환경 변수를 사용하여 사용자가 특정 노드에 액세스하는 것을 방지합니다.

## 노드 제외

`NODES_EXCLUDE` 환경 변수를 업데이트하여 사용자가 사용하지 못하도록 차단하려는 노드가 포함된 문자열 배열을 포함합니다.

예를 들어 변수를 다음과 같이 설정합니다.

```
NODES_EXCLUDE: "[\"n8n-nodes-base.executeCommand\", \"n8n-nodes-base.readWriteFile\"]"
```

[명령 실행](/integrations/builtin/core-nodes/n8n-nodes-base.executecommand/index.md) 및 [디스크에서 파일 읽기/쓰기](/integrations/builtin/core-nodes/n8n-nodes-base.readwritefile.md) 노드를 차단합니다.

n8n 사용자는 이러한 노드를 검색하거나 사용할 수 없습니다.

## 차단할 권장 노드

보안 위험을 초래할 수 있는 노드는 사용 사례 및 사용자 프로필에 따라 다릅니다. 시작할 수 있는 몇 가지 노드는 다음과 같습니다.

* [명령 실행](/integrations/builtin/core-nodes/n8n-nodes-base.executecommand/index.md)
* [디스크에서 파일 읽기/쓰기](/integrations/builtin/core-nodes/n8n-nodes-base.readwritefile.md)

## 관련 리소스

이 환경 변수에 대한 자세한 내용은 [노드 환경 변수](/hosting/configuration/environment-variables/nodes.md)를 참조하십시오.

환경 변수 설정에 대한 자세한 내용은 [구성](/hosting/configuration/configuration-methods.md)을 참조하십시오.
