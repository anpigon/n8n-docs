---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 인사이트 환경 변수
description: 자체 호스팅 n8n 인스턴스에 대한 환경 변수로 인사이트 메트릭 수집을 구성합니다.
contentType: reference
tags:
  - 환경 변수
hide:
  - toc
  - tags
---

# 인사이트 환경 변수

--8<-- "_snippets/self-hosting/file-based-configuration.md"

인사이트는 인스턴스 소유자 및 관리자에게 시간 경과에 따른 워크플로우 수행 방식에 대한 가시성을 제공합니다. 자세한 내용은 [인사이트](/insights.md)를 참조하십시오.

 | 변수 | 유형 | 기본값 | 설명 |
 |:---------------------------------------------------------|:-------|:--------|:----------------------------------------------------------------------------------------|
 | `N8N_DISABLED_MODULES` | 문자열 | - | 인스턴스에 대한 기능 및 메트릭 수집을 비활성화하려면 `insights`로 설정합니다. |
 | `N8N_INSIGHTS_COMPACTION_BATCH_SIZE` | 숫자 | 500 | 단일 배치에서 압축할 원시 인사이트 데이터의 수입니다. |
 | `N8N_INSIGHTS_COMPACTION_DAILY_TO_WEEKLY_THRESHOLD_DAYS` | 숫자 | 180 | 압축할 일일 인사이트 데이터의 최대 기간(일)입니다. |
 | `N8N_INSIGHTS_COMPACTION_HOURLY_TO_DAILY_THRESHOLD_DAYS` | 숫자 | 90 | 압축할 시간별 인사이트 데이터의 최대 기간(일)입니다. |
 | `N8N_INSIGHTS_COMPACTION_INTERVAL_MINUTES` | 숫자 | 60 | 압축을 실행해야 하는 간격(분)입니다. |
 | `N8N_INSIGHTS_FLUSH_BATCH_SIZE` | 숫자 | 1000 | 플러시하기 전에 버퍼에 보관할 최대 인사이트 데이터 수입니다. |
 | `N8N_INSIGHTS_FLUSH_INTERVAL_SECONDS` | 숫자 | 30 | 인사이트 데이터를 데이터베이스에 플러시해야 하는 간격(초)입니다. |
