---
#https://www.notion.so/n8n/Frontmatter-432c2b8dff1f43d4b1c8d20075510fe4
title: 외부 시크릿
description: n8n에서 외부 시크릿 저장소를 사용하세요.
contentType: howto
---

# 외부 시크릿

/// info | 기능 사용 가능 여부
* 외부 시크릿은 엔터프라이즈 자체 호스팅 및 엔터프라이즈 클라우드 요금제에서 사용할 수 있습니다.
* n8n은 AWS Secrets Manager, Azure Key Vault, GCP Secrets Manager, Infisical 및 HashiCorp Vault를 지원합니다. 
* n8n은 [HashiCorp Vault Secrets](https://developer.hashicorp.com/hcp/docs/vault-secrets){:target=_blank .external-link}를 지원하지 않습니다.
///

외부 시크릿 저장소를 사용하여 n8n의 [자격 증명](/glossary.md#credential-n8n)을 관리할 수 있습니다.

n8n은 모든 자격 증명을 데이터베이스에 암호화하여 저장하고 기본적으로 접근을 제한합니다. 외부 시크릿 기능을 사용하면 민감한 자격 증명 정보를 외부 저장소에 저장하고 필요할 때 n8n이 로드하도록 할 수 있습니다. 이는 추가적인 보안 계층을 제공하며 여러 [n8n 환경](/source-control-environments/index.md)에서 사용되는 자격 증명을 중앙에서 관리할 수 있게 해줍니다.

## n8n을 시크릿 저장소에 연결하기

/// note | 시크릿 이름
시크릿 이름에는 공백, 하이픈 또는 기타 특수 문자를 포함할 수 없습니다. n8n은 영숫자(`a-z`, `A-Z`, `0-9`)와 밑줄이 포함된 시크릿 이름을 지원합니다. n8n은 현재 시크릿에 대해 일반 텍스트 값만 지원하며 JSON 객체나 키-값 쌍은 지원하지 않습니다.
///

1. n8n에서 **설정** > **외부 시크릿**으로 이동합니다.
1. 저장소 제공업체에 대해 **설정**을 선택합니다.
1. 제공업체의 자격 증명을 입력합니다:
	* Azure Key Vault: **저장소 이름**, **테넌트 ID**, **클라이언트 ID**, **클라이언트 시크릿**을 제공합니다. Azure 문서에서 [Microsoft Entra ID 앱 등록 및 서비스 주체 생성](https://learn.microsoft.com/en-us/entra/identity-platform/howto-create-service-principal-portal){:target=_blank .external-link}을 참조하세요. n8n은 시크릿에 대해 단일 라인 값만 지원합니다.
	* AWS Secrets Manager: **액세스 키 ID**, **비밀 액세스 키**, **리전**을 제공합니다. IAM 사용자는 `secretsmanager:ListSecrets`, `secretsmanager:BatchGetSecretValue`, `secretsmanager:GetSecretValue` 권한이 있어야 합니다.

		n8n에 AWS Secrets Manager의 모든 시크릿에 대한 접근 권한을 부여하려면 IAM 사용자에 다음 정책을 연결할 수 있습니다:
		```json
		{
			"Version": "2012-10-17",
			"Statement": [
				{
					"Sid": "AccessAllSecrets",
					"Effect": "Allow",
					"Action": [
						"secretsmanager:ListSecrets",
						"secretsmanager:BatchGetSecretValue",
 						"secretsmanager:GetResourcePolicy",
						"secretsmanager:GetSecretValue",
						"secretsmanager:DescribeSecret",
						"secretsmanager:ListSecretVersionIds"
					],
					"Resource": "*"
				}
			]
		}
		```

		더 제한적으로 특정 AWS Secret Manager 시크릿에 대한 접근 권한을 n8n에 부여할 수도 있습니다. 모든 리소스에 접근하려면 여전히 `secretsmanager:ListSecrets` 및 `secretsmanager:BatchGetSecretValue` 권한을 허용해야 합니다. 이러한 권한은 n8n이 ARN 범위의 시크릿을 검색할 수 있게 하지만 시크릿 값에 대한 접근은 제공하지 않습니다.

		다음으로, n8n과 공유하려는 시크릿의 특정 Amazon 리소스 이름(ARN)에 대해 `secretsmanager:GetSecretValue` 권한의 범위를 설정해야 합니다. 각 리소스 ARN에 올바른 리전과 계정 ID를 사용했는지 확인하세요. 시크릿의 ARN 세부 정보는 AWS 대시보드에서 찾을 수 있습니다.
		
		예를 들어, 다음 IAM 정책은 지정된 AWS 계정 및 리전에서 `n8n`으로 시작하는 이름의 시크릿에만 접근을 허용합니다:

		```json
		{
			"Version": "2012-10-17",
			"Statement": [
				{
					"Sid": "ListingSecrets",
					"Effect": "Allow",
					"Action": [
						"secretsmanager:ListSecrets",
						"secretsmanager:BatchGetSecretValue"
					],
					"Resource": "*"
				},
				{
					"Sid": "RetrievingSecrets",
					"Effect": "Allow",
					"Action": [
						"secretsmanager:GetSecretValue",
						"secretsmanager:DescribeSecret"
					],
					"Resource": [
						"arn:aws:secretsmanager:us-west-2:123456789000:secret:n8n*"
					]
				}
			]
		}
		```

		더 많은 IAM 권한 정책 예시는 [AWS 문서](https://docs.aws.amazon.com/secretsmanager/latest/userguide/auth-and-access_iam-policies.html#auth-and-access_examples_batch){:target=_blank .external-link}를 참조하세요.

	* HashiCorp Vault: 저장소 인스턴스의 **Vault URL**을 제공하고 **인증 방법**을 선택합니다.  인증 세부 정보를 입력합니다. 선택적으로 네임스페이스를 제공합니다.
		- 인증 방법에 대한 HashiCorp 문서를 참조하세요:
				[토큰 인증 방법](https://developer.hashicorp.com/vault/docs/auth/token){:target=_blank .external-link}  
				[AppRole 인증 방법](https://developer.hashicorp.com/vault/docs/auth/approle){:target=_blank .external-link}  
				[Userpass 인증 방법](https://developer.hashicorp.com/vault/docs/auth/userpass){:target=_blank .external-link}  
		- Vault 네임스페이스를 사용하는 경우, n8n이 연결해야 할 네임스페이스를 입력할 수 있습니다. HashiCorp Vault 네임스페이스에 대한 자세한 내용은 [Vault 엔터프라이즈 네임스페이스](https://developer.hashicorp.com/vault/docs/enterprise/namespaces){:target=_blank .external-link}를 참조하세요.

	* Infisical: **서비스 토큰**을 제공합니다. 토큰을 얻는 방법에 대한 정보는 Infisical의 [서비스 토큰](https://infisical.com/docs/documentation/platform/token){:target=_blank .external-link} 문서를 참조하세요. Infisical을 자체 호스팅하는 경우 **사이트 URL**을 입력합니다.

	    /// note | Infisical 환경
		토큰을 생성할 때 올바른 Infisical 환경을 선택했는지 확인하세요. n8n은 이 환경에서 시크릿을 로드하며 다른 Infisical 환경의 시크릿에는 접근할 수 없습니다. n8n은 단일 환경에만 접근할 수 있는 서비스 토큰만 지원합니다.
		///

	    /// note | Infisical 폴더
	 	n8n은 [Infisical 폴더](https://infisical.com/docs/documentation/platform/folder){:target=_blank .external-link}를 지원하지 않습니다.
		///

	* Google Cloud Platform: 최소한 `Secret Manager 시크릿 접근자` 및 `Secret Manager 시크릿 뷰어` 역할을 가진 서비스 계정의 **서비스 계정 키**(JSON)를 제공합니다. 자세한 내용은 Google의 [서비스 계정 문서](https://cloud.google.com/iam/docs/service-account-overview){:target=_blank .external-link}를 참조하세요.

1. 구성을 **저장**합니다.
1. **비활성화 / 활성화** 토글을 사용하여 제공업체를 활성화합니다.


## n8n 자격 증명에서 시크릿 사용하기

n8n 자격 증명에서 저장소의 시크릿을 사용하려면:

1. 새 자격 증명을 만들거나 기존 자격 증명을 엽니다.
1. 시크릿을 사용하려는 필드에서:
	1. 필드 위로 마우스를 가져갑니다.
	1. **표현식**을 선택합니다.
1. 시크릿을 사용하려는 필드에 시크릿 이름을 참조하는 [표현식](/glossary.md#expression-n8n)을 입력합니다:
	```js
	{{ $secrets.<vault-name>.<secret-name> }}
	```
	`<vault-name>`은 `vault`(HashiCorp의 경우) 또는 `infisical` 또는 `awsSecretsManager`입니다. `<secret-name>`을 저장소에 표시되는 이름으로 바꿉니다.

## n8n 환경에서 외부 시크릿 사용하기

n8n의 [소스 제어 및 환경](/source-control-environments/index.md) 기능을 사용하면 Git으로 지원되는 다양한 n8n 환경을 만들 수 있습니다. 이 기능은 다른 인스턴스에서 다른 자격 증명을 사용하는 것을 지원하지 않습니다. 각 n8n 인스턴스를 다른 저장소 또는 프로젝트 환경에 연결하여 다른 환경에 다른 자격 증명을 제공하기 위해 외부 시크릿 저장소를 사용할 수 있습니다.

예를 들어, 개발용과 프로덕션용으로 두 개의 n8n 인스턴스가 있습니다. 저장소로 Infisical을 사용합니다. Infisical에서 개발 및 프로덕션 두 환경으로 프로젝트를 만듭니다. 각 Infisical 환경에 대한 토큰을 생성합니다. 개발 환경용 토큰을 사용하여 개발 n8n 인스턴스를 연결하고, 프로덕션 환경용 토큰을 사용하여 프로덕션 n8n 인스턴스를 연결합니다.

## 프로젝트에서 외부 시크릿 사용하기

[RBAC 프로젝트](/user-management/rbac/index.md)에서 외부 시크릿을 사용하려면 프로젝트의 멤버로 [인스턴스 소유자 또는 인스턴스 관리자](/user-management/account-types.md)가 있어야 합니다.

## 문제 해결

### Infisical 버전 변경

Infisical 버전 업그레이드는 n8n 연결에 문제를 일으킬 수 있습니다. Infisical 연결이 작동을 멈추면 최근 버전 변경이 있었는지 확인하세요. 그렇다면 help@n8n.io로 문제를 보고하세요.

### 인스턴스 소유자 또는 관리자가 소유한 자격 증명에만 외부 시크릿 설정

인스턴스 소유자 및 관리자가 가진 권한 때문에 소유자 및 관리자는 다른 사용자가 소유한 자격 증명을 시크릿 표현식으로 업데이트할 수 있습니다. 이는 인스턴스 소유자 또는 관리자의 미리보기에서는 작동하는 것처럼 보이지만, 워크플로우가 프로덕션에서 실행될 때 시크릿이 확인되지 않습니다. 

인스턴스 관리자 또는 소유자가 소유한 자격 증명에만 외부 시크릿을 사용하세요. 이렇게 하면 프로덕션에서 올바르게 확인됩니다.