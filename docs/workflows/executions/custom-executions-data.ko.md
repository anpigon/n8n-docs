---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
description: 코드 노드를 사용하여 워크플로우 실행에 사용자 지정 데이터를 추가합니다. 그런 다음 이 데이터로 실행을 필터링할 수 있습니다.
contentType: howto
---

# 사용자 지정 실행 데이터

코드 노드 또는 [실행 데이터 노드](/integrations/builtin/core-nodes/n8n-nodes-base.executiondata.md)를 사용하여 워크플로우에 사용자 지정 데이터를 설정할 수 있습니다. n8n은 각 실행과 함께 이를 기록합니다. 그런 다음 실행 목록을 필터링할 때 이 데이터를 사용하거나 코드 노드를 사용하여 워크플로우에서 가져올 수 있습니다.

--8<-- "_snippets/workflows/executions/custom-execution-data-availability.md"

## 코드 노드를 사용하여 사용자 지정 데이터 설정 및 액세스

이 섹션에서는 코드 노드를 사용하여 데이터를 설정하고 액세스하는 방법을 설명합니다. 실행 데이터 노드를 사용하여 데이터를 설정하는 방법에 대한 정보는 [실행 데이터 노드](/integrations/builtin/core-nodes/n8n-nodes-base.executiondata.md)를 참조하십시오. 실행 데이터 노드를 사용하여 사용자 지정 데이터를 검색할 수 없습니다.

### 사용자 지정 실행 데이터 설정

단일 추가 데이터 조각 설정:

=== "JavaScript"
	```js
	$execution.customData.set("key", "value");
	```
=== "Python"
	```python
	_execution.customData.set("key", "value");
	```

모든 추가 데이터 설정. 이 실행에 대한 전체 사용자 지정 데이터 개체를 덮어씁니다.

=== "JavaScript"
	```js
	$execution.customData.setAll({"key1": "value1", "key2": "value2"})
	```
=== "Python"
	```python
	_execution.customData.setAll({"key1": "value1", "key2": "value2"})
	```

제한 사항이 있습니다.

* 문자열이어야 합니다.
* `key`의 최대 길이는 50자입니다.
* `value`의 최대 길이는 255자입니다.
* n8n은 최대 10개의 사용자 지정 데이터를 지원합니다.

### 실행 중 사용자 지정 데이터 개체에 액세스

실행 중에 사용자 지정 데이터 개체 또는 그 안의 특정 값을 검색할 수 있습니다.

<!-- vale off -->
=== "JavaScript"
	```js
	// 실행 중 개체의 현재 상태에 액세스
	const customData = $execution.customData.getAll();

	// 이 실행 중에 설정된 특정 값에 액세스
	const customData = $execution.customData.get("key");
	```
=== "Python"
	```python
	# 실행 중 개체의 현재 상태에 액세스
	customData = _execution.customData.getAll();

	# 이 실행 중에 설정된 특정 값에 액세스
	customData = _execution.customData.get("key");
	```
<!-- vale on -->
