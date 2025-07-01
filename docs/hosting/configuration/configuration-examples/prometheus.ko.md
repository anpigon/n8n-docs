---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 프로메테우스 메트릭 활성화
description: 프로메테우스 메트릭 엔드포인트를 활성화합니다.
contentType: howto
---

# 프로메테우스 메트릭 활성화

메트릭을 수집하고 노출하기 위해 n8n은 [prom-client](https://www.npmjs.com/package/prom-client){:target="_blank" .external-link} 라이브러리를 사용합니다.

`/metrics` 엔드포인트는 기본적으로 비활성화되어 있지만 `N8N_METRICS` 환경 변수를 사용하여 활성화할 수 있습니다.

```bash
export N8N_METRICS=true
```

노출할 메트릭 및 레이블을 구성하려면 해당 [환경 변수](/hosting/configuration/environment-variables/endpoints.md) (`N8N_METRICS_INCLUDE_*`)를 참조하십시오.

`main` 및 `worker` 인스턴스 모두 메트릭을 노출할 수 있습니다.

## 큐 메트릭

큐 메트릭을 활성화하려면 `N8N_METRICS_INCLUDE_QUEUE_METRICS` 환경 변수를 `true`로 설정하십시오. `N8N_METRICS_QUEUE_METRICS_INTERVAL`로 새로 고침 빈도를 조정할 수 있습니다.

큐 메트릭은 단일 메인 모드의 `main` 인스턴스에서만 사용할 수 있습니다.

```
# HELP n8n_scaling_mode_queue_jobs_active 스케일링 모드에서 모든 워커에서 처리 중인 현재 작업 수입니다.
# TYPE n8n_scaling_mode_queue_jobs_active gauge
n8n_scaling_mode_queue_jobs_active 0

# HELP n8n_scaling_mode_queue_jobs_completed 인스턴스 시작 이후 스케일링 모드에서 모든 워커에서 완료된 총 작업 수입니다.
# TYPE n8n_scaling_mode_queue_jobs_completed counter
n8n_scaling_mode_queue_jobs_completed 0

# HELP n8n_scaling_mode_queue_jobs_failed 인스턴스 시작 이후 스케일링 모드에서 모든 워커에서 실패한 총 작업 수입니다.
# TYPE n8n_scaling_mode_queue_jobs_failed counter
n8n_scaling_mode_queue_jobs_failed 0

# HELP n8n_scaling_mode_queue_jobs_waiting 스케일링 모드에서 픽업을 기다리는 현재 대기 중인 작업 수입니다.
# TYPE n8n_scaling_mode_queue_jobs_waiting gauge
n8n_scaling_mode_queue_jobs_waiting 0
```
