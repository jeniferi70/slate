--- 

title: LTL-B2B-API 

language_tabs: 
   - shell 

toc_footers: 
   - <a href='#'>Sign Up for a Developer Key</a> 
   - <a href='https://github.com/lavkumarv'>Documentation Powered by lav</a> 

includes: 
   - errors 

search: true 

--- 

# Introduction 

Build - 1.0-tag47_10b01-B2B_b359


	LTL B2B API
	``` 
	https://api.ltl.xpo.com
	```
	 

**Version:** 1.0 

# /HEALTH-CHECK
## ***GET*** 

**Summary:** Check if service is running

**Description:** Health check URL. Responds with success message if the service is running.

### HTTP Request 
`***GET*** /health-check` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| format | query | Specify the format for responses. JSON or XML. Defaults to JSON | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Indicates service is operating normally |

# /OPTIONS
## ***GET*** 

**Summary:** List of resources

**Description:** List of resources.

### HTTP Request 
`***GET*** /options` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| format | query | Specify the format for responses. JSON or XML. Defaults to JSON | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | List of resource links |

# /APPUSERS/LOGGED-IN-USER
## ***GET*** 

**Summary:** Details of user invoking the API.

**Description:** Details of user invoking the API.

### HTTP Request 
`***GET*** /appusers/logged-in-user` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| format | query | Specify the format for responses. JSON or XML. Defaults to JSON | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | User details |

# /TRANSACTION-RULESETS
## ***GET*** 

**Summary:** listTransactionRuleset - List Transaction Ruleset

**Description:** This service will return a list of transaction rulesets for a given ediIsaId or ediGSId

Pre-conditions:
1. Either ediIsaId or ediGSId is provided. optionally, 1 or more tranTypeCodes are also provided.

Post-conditions:
1. 1 or more Transaction Manager, Transaction Rulesets and TRS Requirement codes are returned for input ediIsaId or ediGSId.


### HTTP Request 
`***GET*** /transaction-rulesets` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| includeLocationOverrideInd | query |  | No | boolean |
| ediIsaId | query | EDI ISA Identifier. | No | string |
| ediGsId | query | EDI GS Identifier | No | string |
| tranTypeCd | query | Transaction type codes | No | array |
| format | query | Specify the format for responses. JSON or XML. Defaults to JSON | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Response message |

<!-- Converted with the swagger-to-slate https://github.com/lavkumarv/swagger-to-slate -->
