#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 바이너리 데이터 환경 변수
description: 자체 호스팅 n8n 인스턴스에 대한 환경 변수로 바이너리 데이터 저장 모드 및 경로를 사용자 지정합니다.
contentType: reference
tags:
  - 환경 변수
hide:
  - toc
  - tags
---

# 바이너리 데이터 환경 변수

--8<-- "_snippets/self-hosting/file-based-configuration.md"

기본적으로 n8n은 메모리를 사용하여 바이너리 데이터를 저장합니다. 엔터프라이즈 사용자는 대신 외부 서비스를 사용하도록 선택할 수 있습니다. 바이너리 데이터에 외부 저장소를 사용하는 방법에 대한 자세한 내용은 [외부 저장소](/hosting/scaling/external-storage.md)를 참조하십시오.


| 변수 | 유형 | 기본값 | 설명 |
| :------- | :---- | :------- | :---------- |
| `N8N_AVAILABLE_BINARY_DATA_MODES` | 문자열 | `filesystem` | 사용 가능한 바이너리 데이터 모드의 쉼표로 구분된 목록입니다. |
| `N8N_BINARY_DATA_STORAGE_PATH` | 문자열 | `N8N_USER_FOLDER/binaryData` | n8n이 바이너리 데이터를 저장하는 경로입니다. |
| `N8N_DEFAULT_BINARY_DATA_MODE` | 문자열 | `default` | 기본 바이너리 데이터 모드입니다. `default`는 바이너리 데이터를 메모리에 유지합니다. 파일 시스템을 사용하려면 `filesystem`으로 설정하고 AWS S3를 사용하려면 `s3`로 설정합니다. 바이너리 데이터 정리는 활성 바이너리 데이터 모드에서 작동합니다. 예를 들어 인스턴스가 S3에 데이터를 저장하고 나중에 파일 시스템 모드로 전환한 경우 n8n은 파일 시스템의 바이너리 데이터만 정리합니다. 이는 향후 변경될 수 있습니다. |