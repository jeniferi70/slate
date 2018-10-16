--- 

title: LTL-Imaging-API 

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

Build - 1.0-tag47_02_b30


	LTL Imaging API
	```
	https://api.ltl.xpo.com
	```
	 

**Version:** 1.0 

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

# /SHIPMENTS/{PRONBR}/IMAGED-DOCS
## ***GET*** 

**Summary:** getShipmentImagedDocuments - Get Imaged Documents for Single Pro

**Description:** This service retrieves imaged documents for a single Pro number from DMS.1 Shipment Pro Number must be provided and optional 1 or more image types can be input. If no image type is provided then all imaged documents will be retrieved. Supported Imaged Documents are: BL(Bill of Lading),DR(Delivery Receipt),DRRR(Delivery Return Receipt), CUST(Customs Documents),IR(Inspection Report),LOA(Letter of Authority), NCIC (NMFC Certificate),WI(Weights and Corrections),WRFO(Weights and Research photos).

Pre-conditions: 
 Valid input data - Pro Number and image type are provided, and imaged document exists.
Post-conditions: 
 Imaged data is returned.
Pre-conditions: 
 Imaged document doesn't exist for input Pro Number and image type.
Post-conditions: 
 Not found message is returned.



### HTTP Request 
`***GET*** /shipments/{proNbr}/imaged-docs` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| proNbr | path | Business Identifier of the Shipment | Yes | string |
| imageFormat | query | Format of image requested:jpg, tiff, png, or pdf | No | string |
| imageType | query | Type of image requested | No | array |
| format | query | Specify the format for responses. JSON or XML. Defaults to JSON | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |

<!-- Converted with the swagger-to-slate https://github.com/lavkumarv/swagger-to-slate -->
