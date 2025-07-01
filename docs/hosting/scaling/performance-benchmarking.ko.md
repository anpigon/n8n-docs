---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
description: n8n 성능 및 리소스 소비 벤치마킹.
contentType: explanation
---

# 성능 및 벤치마킹

n8n은 단일 인스턴스에서 초당 최대 220개의 워크플로우 실행을 처리할 수 있으며, 더 많은 인스턴스를 추가하여 더 확장할 수 있습니다.

이 문서는 n8n의 성능 벤치마킹을 간략하게 설명합니다. 성능에 영향을 미치는 요소를 설명하고 두 가지 예제 벤치마크를 포함합니다.

## 성능 요인

n8n의 성능은 다음과 같은 요인에 따라 달라집니다.

* 워크플로우 유형
* n8n에서 사용할 수 있는 리소스
* n8n의 확장 옵션을 구성하는 방법


## 자체 벤치마킹 실행

사용 사례에 대한 정확한 추정치를 얻으려면 n8n의 [벤치마킹 프레임워크](https://github.com/n8n-io/n8n/tree/master/packages/%40n8n/benchmark){:target=_blank .external-link}를 실행하십시오. 리포지토리에는 벤치마킹에 대한 자세한 정보가 포함되어 있습니다.

## 예: 단일 인스턴스 성능

이 테스트는 초당 요청이 증가함에 따라 응답 시간이 어떻게 증가하는지 측정합니다. 웹훅 트리거 노드를 호출할 때의 응답 시간을 살펴봅니다.

설정:

- 하드웨어: ECS c5a.large 인스턴스(4GB RAM)
- n8n 설정: 단일 n8n 인스턴스(메인 모드에서 실행, Postgres 데이터베이스 포함)
- 워크플로우: 웹훅 트리거 노드, 필드 편집 노드

<figure markdown>
  ![초당 요청에 따른 n8n 응답 시간을 보여주는 그래프](/_images/hosting/scaling/benchmarking-single-instance-100-250.png)
  <figcaption>이 그래프는 웹훅 트리거 노드에 대한 요청이 100초 이내에 응답을 받는 비율과 부하에 따라 어떻게 달라지는지 보여줍니다. 부하가 높을수록 n8n은 일반적으로 데이터를 계속 처리하지만 응답하는 데 100초 이상 걸립니다.</figcaption>
</figure>



## 예: 다중 인스턴스 성능

이 테스트는 초당 요청이 증가함에 따라 응답 시간이 어떻게 증가하는지 측정합니다. 웹훅 트리거 노드를 호출할 때의 응답 시간을 살펴봅니다.

설정:

- 하드웨어: 7개의 ECS c5a.4xlarge 인스턴스(각각 8GB RAM)
- n8n 설정: 2개의 웹훅 인스턴스, 4개의 작업자 인스턴스, 1개의 데이터베이스 인스턴스(MySQL), n8n 및 Redis를 실행하는 1개의 메인 인스턴스
- 워크플로우: 웹훅 트리거 노드, 필드 편집 노드
- 다중 인스턴스 설정은 [큐 모드](/hosting/scaling/queue-mode.md)를 사용합니다.

<figure markdown>
  ![초당 요청에 따른 n8n 응답 시간을 보여주는 그래프](/_images/hosting/scaling/benchmarking-multi-instance-500-2500.png)
  <figcaption>이 그래프는 웹훅 트리거 노드에 대한 요청이 100초 이내에 응답을 받는 비율과 부하에 따라 어떻게 달라지는지 보여줍니다. 부하가 높을수록 n8n은 일반적으로 데이터를 계속 처리하지만 응답하는 데 100초 이상 걸립니다.</figcaption>
</figure>
