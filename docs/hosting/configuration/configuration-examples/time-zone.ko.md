---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 자체 호스팅 인스턴스 시간대 설정
description: 자체 호스팅 n8n 인스턴스의 기본 시간대를 변경합니다.
contentType: howto
---

# 자체 호스팅 인스턴스 시간대 설정

기본 시간대는 America/New_York입니다. 예를 들어, 스케줄 노드는 워크플로우가 시작되어야 하는 시간을 알기 위해 이 시간대를 사용합니다. 다른 기본 시간대를 설정하려면 `GENERIC_TIMEZONE`을 적절한 값으로 설정하십시오. 예를 들어, 시간대를 베를린(독일)으로 설정하려면 다음과 같이 하십시오.

```bash
export GENERIC_TIMEZONE=Europe/Berlin
```

시간대 이름은 [여기](https://momentjs.com/timezone/){:target="_blank" .external-link}에서 찾을 수 있습니다.

이 변수에 대한 자세한 내용은 [환경 변수 참조](/hosting/configuration/environment-variables/timezone-localization.md)를 참조하십시오.
