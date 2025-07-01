---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: n8n에서 바이너리 데이터 확장
description: n8n의 성능을 저하시키지 않고 대용량 파일을 처리하는 방법입니다.
contentType: howto
---

# 바이너리 데이터

바이너리 데이터는 워크플로우 실행 중에 생성되거나 처리되는 이미지 파일이나 문서와 같은 모든 파일 형식 데이터입니다.

## 파일 시스템 모드 활성화

바이너리 데이터를 처리할 때 n8n은 기본적으로 데이터를 메모리에 보관합니다. 이로 인해 대용량 파일로 작업할 때 충돌이 발생할 수 있습니다.

이를 방지하려면 `N8N_DEFAULT_BINARY_DATA_MODE` [환경 변수](/hosting/configuration/environment-variables/binary-data.md)를 `filesystem`으로 변경하십시오. 이렇게 하면 n8n이 메모리를 사용하는 대신 디스크에 데이터를 저장하게 됩니다.

큐 모드를 사용하는 경우 이 값을 `default`로 유지하십시오. n8n은 큐 모드에서 파일 시스템 모드를 지원하지 않습니다.

## 바이너리 데이터 정리

n8n은 실행 데이터 정리의 일부로 바이너리 데이터 정리를 실행합니다. 자세한 내용은 [실행 데이터 | 데이터 정리 활성화](/hosting/scaling/execution-data.md#enable-data-pruning)를 참조하십시오.

여러 바이너리 데이터 모드를 구성하는 경우 바이너리 데이터 정리는 활성 바이너리 데이터 모드에서 작동합니다. 예를 들어 인스턴스가 S3에 데이터를 저장하고 나중에 파일 시스템 모드로 전환한 경우 n8n은 파일 시스템의 바이너리 데이터만 정리합니다. 자세한 내용은 [외부 저장소](/hosting/scaling/external-storage.md#usage)를 참조하십시오.
