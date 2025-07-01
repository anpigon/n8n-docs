---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 사용자 지정 노드의 위치 지정
description: 사용자 지정 노드의 폴더를 추가하고 경로를 지정합니다.
contentType: howto
---

# 사용자 지정 노드의 위치 지정

모든 사용자는 시작 시 n8n에 의해 로드되는 사용자 지정 노드를 추가할 수 있습니다. 기본
위치는 n8n을 시작한 사용자의 하위 폴더 `.n8n/custom`에 있습니다.

환경 변수를 사용하여 더 많은 폴더를 정의할 수 있습니다.

```bash
export N8N_CUSTOM_EXTENSIONS="/home/jim/n8n/custom-nodes;/data/n8n/nodes"
```
이 변수에 대한 자세한 내용은 [환경 변수 참조](/hosting/configuration/environment-variables/nodes.md)를 참조하십시오.
