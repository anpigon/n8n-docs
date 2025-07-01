#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 코드 노드에서 모듈 활성화
description: 코드 노드 내에서 내장 및 외부 모듈을 모두 사용할 수 있도록 허용합니다.
contentType: howto
---

# 코드 노드에서 모듈 활성화

보안상의 이유로 코드 노드는 모듈 가져오기를 제한합니다. 다음 환경 변수를 설정하여 내장 및 외부 모듈에 대한 제한을 해제할 수 있습니다.

- `NODE_FUNCTION_ALLOW_BUILTIN`: 내장 모듈용
- `NODE_FUNCTION_ALLOW_EXTERNAL`: n8n/node_modules 디렉토리에서 가져온 외부 모듈용. 환경 변수가 설정되지 않은 경우 외부 모듈 지원이 비활성화됩니다.

```bash
# 모든 내장 모듈 사용 허용
export NODE_FUNCTION_ALLOW_BUILTIN=*

# crypto만 사용 허용
export NODE_FUNCTION_ALLOW_BUILTIN=crypto

# crypto 및 fs만 사용 허용
export NODE_FUNCTION_ALLOW_BUILTIN=crypto,fs

# 외부 npm 모듈 사용 허용
export NODE_FUNCTION_ALLOW_EXTERNAL=moment,lodash
```
이러한 변수에 대한 자세한 내용은 [환경 변수 참조](/hosting/configuration/environment-variables/nodes.md)를 참조하십시오.