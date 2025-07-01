#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
description: 스티커 메모를 사용하여 워크플로우에 주석을 답니다.
contentType: howto
---

# 스티커 메모

스티커 메모를 사용하면 워크플로우에 주석을 달고 댓글을 달 수 있습니다.

n8n은 특히 [템플릿 워크플로우](/glossary.md#template-n8n)에서 다른 사용자가 워크플로우를 이해하는 데 도움이 되도록 스티커 메모를 많이 사용하는 것을 권장합니다.

![예제 스티커 메모가 있는 기본 워크플로우의 스크린샷](/_images/workflows/components/stickies/example-sticky-note.png)

## 스티커 메모 만들기

스티커 메모는 핵심 노드입니다. 새 스티커 메모를 추가하려면:

1. 노드 패널을 엽니다.
2. `note`를 검색합니다.
3. **스티커 메모** 노드를 클릭합니다. n8n이 캔버스에 새 스티커 메모를 추가합니다.

## 스티커 메모 편집

1. 편집하려는 스티커 메모를 두 번 클릭합니다.
2. 메모를 작성합니다. [이 가이드](https://commonmark.org/help/)는 마크다운으로 텍스트 서식을 지정하는 방법을 설명합니다. n8n은 CommonMark 사양을 구현하는 [markdown-it](https://github.com/markdown-it/markdown-it)을 사용합니다.
3. 메모에서 벗어나거나 `Esc`를 눌러 편집을 중지합니다.

## 색상 변경

스티커 메모 색상을 변경하려면:

1. 스티커 메모 위로 마우스를 가져갑니다.
2. **색상 변경** <span class="inline-image">![스티커 메모 색상 변경 아이콘](/_images/common-icons/change-color.png){.off-glb}</span>을 선택합니다.

## 스티커 메모 위치 지정

다음을 수행할 수 있습니다.

* 스티커 메모를 캔버스 어디든 드래그합니다.
* 스티커 메모를 노드 뒤로 드래그합니다. 이를 사용하여 노드를 시각적으로 그룹화할 수 있습니다.
* 메모 가장자리에 마우스를 가져가 드래그하여 스티커 메모 크기를 조정합니다.
* 색상 변경: **옵션** <span class="inline-image">![옵션 아이콘](/_images/common-icons/three-dot-options-menu.png){.off-glb}</span>을 선택하여 색상 선택기를 엽니다.

## 마크다운으로 작성

스티커 메모는 마크다운 서식을 지원합니다. 이 섹션에서는 몇 가지 일반적인 옵션을 설명합니다.

```
이중 별표 안의 텍스트는 **굵게** 표시됩니다.

단일 별표 안의 텍스트는 *기울임꼴*로 표시됩니다.

#을 사용하여 제목을 나타냅니다.
# 이것은 최상위 제목입니다.
## 이것은 하위 제목입니다.
### 이것은 더 작은 하위 제목입니다.

링크를 추가할 수 있습니다.
[예제](https://example.com/)

별표를 사용하여 목록을 만듭니다.

* 항목 1
* 항목 2

또는 숫자로 순서 있는 목록을 만듭니다.

1. 항목 1
2. 항목 2
```

자세한 가이드는 [CommonMark의 도움말](https://commonmark.org/help/)을 참조하십시오. n8n은 CommonMark 사양을 구현하는 [markdown-it](https://github.com/markdown-it/markdown-it)을 사용합니다.

## 이미지를 전체 너비로 만들기

파일 이름에 `#full-width`를 추가하여 이미지를 스티커 메모의 100% 너비로 강제할 수 있습니다.

```markdown
![소스 예제](https://<IMAGE-URL>/<IMAGE-NAME>.png#full-width)
```