#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
description: n8n 인스턴스의 바이너리 데이터 외부 저장소입니다.
contentType: howto
tags:
  - 외부 저장소
  - 저장소
hide:
  - tags
search:
  boost: 1.5
---

# 외부 저장소

/// info | 기능 가용성

* 자체 호스팅 엔터프라이즈 플랜에서 사용 가능
* 클라우드 엔터프라이즈에서 이 기능에 액세스하려면 [n8n에 문의](https://n8n-community.typeform.com/to/y9X2YuGa){:target=_blank .external-link}하십시오.
///

n8n은 워크플로우 실행에서 생성된 바이너리 데이터를 외부에 저장할 수 있습니다. 이 기능은 대량의 바이너리 데이터를 저장하기 위해 파일 시스템에 의존하는 것을 피하는 데 유용합니다.

n8n은 향후 다른 데이터 유형에 대한 외부 저장소를 도입할 예정입니다.

## n8n의 바이너리 데이터를 S3에 저장

n8n은 워크플로우 실행에서 생성된 바이너리 데이터의 외부 저장소로 [AWS S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html){:target=_blank .external-link}를 지원합니다. Cloudflare R2 및 Backblaze B2와 같은 다른 S3 호환 서비스를 사용할 수 있지만 n8n은 공식적으로 지원하지 않습니다.

/// info | 엔터프라이즈급 기능
외부 저장소에는 [엔터프라이즈 라이선스 키](/license-key.md)가 필요합니다. 라이선스 키가 만료되고 S3 모드를 계속 사용하는 경우 인스턴스는 S3 버킷에서 읽을 수는 있지만 쓸 수는 없습니다.
///

### 설정

[AWS 설명서](https://docs.aws.amazon.com/AmazonS3/latest/userguide/creating-bucket.html){:target=_blank .external-link}에 따라 버킷을 만들고 구성합니다. 다음 정책을 사용할 수 있으며 `<bucket-name>`을 만든 버킷 이름으로 바꿉니다.

```json
{
 "Version": "2012-10-17",
 "Statement": [
  {
   "Sid": "VisualEditor0",
   "Effect": "Allow",
   "Action": ["s3:*"],
   "Resource": ["arn:aws:s3:::<bucket-name>", "arn:aws:s3:::<bucket-name>/*"]
  }
 ]
}
```

S3가 오래된 바이너리 데이터를 자동으로 삭제하도록 버킷 수준 수명 주기 구성을 설정합니다. n8n은 바이너리 데이터 정리를 S3에 위임하므로 바이너리 데이터를 무기한 보존하려는 경우가 아니면 수명 주기 구성을 설정해야 합니다.

버킷 생성을 마치면 호스트, 버킷 이름 및 지역, 액세스 키 ID 및 비밀 액세스 키가 제공됩니다. n8n의 환경에서 설정해야 합니다.

```sh
export N8N_EXTERNAL_STORAGE_S3_HOST=... # 예: s3.us-east-1.amazonaws.com
export N8N_EXTERNAL_STORAGE_S3_BUCKET_NAME=...
export N8N_EXTERNAL_STORAGE_S3_BUCKET_REGION=...
export N8N_EXTERNAL_STORAGE_S3_ACCESS_KEY=...
export N8N_EXTERNAL_STORAGE_S3_ACCESS_SECRET=...
```

/// note | 지역 없음
공급자가 지역을 요구하지 않는 경우 `N8N_EXTERNAL_STORAGE_S3_BUCKET_REGION`을 `'auto'`로 설정할 수 있습니다.
///
n8n에 바이너리 데이터를 S3에 저장하도록 지시합니다.

```sh
export N8N_AVAILABLE_BINARY_DATA_MODES=filesystem,s3
export N8N_DEFAULT_BINARY_DATA_MODE=s3
```


/// note | 인증 자동 감지
S3 호출을 인증하기 위해 자격 증명을 자동으로 감지하려면 `N8N_EXTERNAL_STORAGE_S3_AUTH_AUTO_DETECT`를 `true`로 설정하십시오. 이렇게 하면 기본 [자격 증명 공급자 체인](https://docs.aws.amazon.com/sdk-for-javascript/v3/developer-guide/setting-credentials-node.html#credchain)이 사용됩니다.
///

서버를 다시 시작하여 새 구성을 로드합니다.

### 사용법

S3를 활성화하면 n8n은 새 바이너리 데이터를 S3 버킷에 쓰고 읽습니다. n8n은 바이너리 데이터를 S3 버킷에 다음 형식으로 씁니다.

```
workflows/{workflowId}/executions/{executionId}/binary_data/{binaryFileId}
```

`N8N_AVAILABLE_BINARY_DATA_MODES`에 `filesystem`이 옵션으로 계속 나열되어 있는 경우 n8n은 파일 시스템에 저장된 이전 바이너리 데이터를 파일 시스템에서 계속 읽습니다.

바이너리 데이터를 S3에 저장하고 나중에 파일 시스템 모드로 전환하는 경우 `N8N_AVAILABLE_BINARY_DATA_MODES`에 `s3`가 계속 나열되어 있고 S3 자격 증명이 유효한 한 인스턴스는 S3에 저장된 모든 데이터를 계속 읽습니다.

--8<-- "_snippets/self-hosting/scaling/binary-data-pruning.md"