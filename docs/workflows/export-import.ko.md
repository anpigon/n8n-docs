---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 워크플로우 내보내기 및 가져오기
description: n8n에서 워크플로우를 내보내고 가져오는 다양한 방법입니다.
contentType: howto
---

# 워크플로우 내보내기 및 가져오기

n8n은 워크플로우를 JSON 형식으로 저장합니다. 워크플로우를 JSON 파일로 내보내거나 JSON 파일을 n8n 라이브러리로 가져올 수 있습니다.
여러 가지 방법으로 워크플로우를 내보내고 가져올 수 있습니다.

--8<-- "_snippets/workflows/sharing-credentials.md"

## 복사-붙여넣기

클립보드에 복사하려는 노드를 선택(`Ctrl + c` 또는 `cmd +c`)하고 편집기 UI에 붙여넣어(`Ctrl + v` 또는 `cmd + v`) 워크플로우 또는 그 일부를 복사하여 붙여넣을 수 있습니다.

모든 노드 또는 노드 그룹을 선택하려면 클릭하고 드래그합니다.
  ![노드 그룹 선택](/_images/workflows/export-import/selectingnodes.gif)

## 편집기 UI 메뉴에서

상단 탐색 모음에서 오른쪽 상단의 점 세 개 <img alt="워크플로우 메뉴 아이콘" class="off-glb" src="/_images/common-icons/three-dots-horizontal.png">를 선택하여 다음 옵션을 확인합니다.

<figure><img src="/_images/courses/level-one/chapter-six/l1-c6-import-export-menu.png" alt="가져오기/내보내기 메뉴" style="width:100%"><figcaption align = "center"><i>워크플로우 가져오기 및 내보내기 메뉴</i></figcaption></figure>

* **다운로드**: 현재 워크플로우를 JSON 파일로 컴퓨터에 다운로드합니다.
* **URL에서 가져오기**: URL에서 워크플로우 JSON을 가져옵니다. 예를 들어 [GitHub의 이 워크플로우 JSON 파일](https://raw.githubusercontent.com/n8n-io/demo-setup/main/n8n/backup/workflows/srOnR8PAY3u4RSwb.json){:target=_blank .external-link}입니다.
* **파일에서 가져오기**: 컴퓨터에서 워크플로우를 JSON 파일로 가져옵니다.

## 명령줄에서

* 내보내기: 워크플로우 또는 자격 증명 내보내기에 대한 [명령 전체 목록](/hosting/cli-commands.md#export-workflows-and-credentials){:target="_blank" .external}을 참조하십시오.
* 가져오기: 워크플로우 또는 자격 증명 가져오기에 대한 [명령 전체 목록](/hosting/cli-commands.md#import-workflows-and-credentials){:target="_blank" .external}을 참조하십시오.
