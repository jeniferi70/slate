--- 

title: LTL-AmazonWebServices-API 

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

Build - 1.0-P2D_MSAT_b829


	LTL AmazonWebServices API
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

# /AMAZON-FILES
## ***GET*** 

**Summary:** listFiles - Retrieve list of files from AWS

**Description:** Returns a list of files from Amazon Web Services, S3, using a full folder path as input key.
Pre-condition: The full folder import path is provided as input; partial or full file name is provided as input.
Post-condition: All contents within that folder/subfolder matching either part or the entire name will be returned.

### HTTP Request 
`***GET*** /amazon-files` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| folderFileKeyName | query | Contains the full folder path and either partial or full file name | No | string |
| format | query | Specify the format for responses. JSON or XML. Defaults to JSON | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Contains the response of an AWS file list inquiry |

## ***POST*** 

**Summary:** uploadFile - Uploads one file to AWS

**Description:** Using an import of complete file information, this service method will store a file into AWS/S3.  If uploading a binary file, it must be decoded into a String using base64 and sent in  on the uploadFile request; on the receiving re-encode the String back into binary data to store the file.
Pre-condition: The file name, file contents and full folder path where the file should exist in AWS is provided as input.
Post-condition: The import file is uploaded and stored in AWS/S3.

### HTTP Request 
`***POST*** /amazon-files` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| folderFileKeyName | formData | Full folder path including file name | Yes | string |
| fileContents | formData | Contents of the file to be uploaded. | Yes | file |
| fileContentType | formData | The MIME type for the file data | Yes | string |
| format | query | Specify the format for responses. JSON or XML. Defaults to JSON | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 | Object created |

# /AMAZON-FILES/{FILEKEY}
## ***GET*** 

**Summary:** downloadAwsFile - Downloads a file from AWS

**Description:** Using the file key, which contains the full AWS path, this service method will download the file from the AWS/S3 datastore to the requestor.


### HTTP Request 
`***GET*** /amazon-files/{fileKey}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| fileKey | path | The full path location and file name in AWS/S3 where the requested file resides. | Yes | string |
| format | query | Specify the format for responses. JSON or XML. Defaults to JSON | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | File contents including name and file type, and a byte array of the actual file data. |

<!-- Converted with the swagger-to-slate https://github.com/lavkumarv/swagger-to-slate -->
