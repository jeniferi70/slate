--- 

title: LTL-Membership-API 

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

Build - 1.0-tag47_41_b353


	LTL Membership API
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

# /CREDITCARDS/{USERPROFILEID}/{CISCUSTNBR}
## ***DELETE*** 

**Summary:** deleteCreditCard - delete a credit card from 3dsi

**Description:** The operation deletes a previous registered card from vendor 3dsi

Pre-conditions:
1. Must be a registered user.
   -- cis customer number
Post-conditions:
   -- card is deleted and operation status returned


### HTTP Request 
`***DELETE*** /creditcards/{userProfileId}/{cisCustNbr}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| userProfileId | path | Unique Id of user profile | Yes | string |
| cisCustNbr | path | CIS Customer Account Number | Yes | string |
| format | query | Specify the format for responses. JSON or XML. Defaults to JSON | No | string |
| Transaction-Timestamp | header | For PUT and DELETE, the timestamp to check for concurrent updates | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |

## ***PUT*** 

**Summary:** updateCreditCard - update a credit card from 3dsi

**Description:** The operation update a previous registered card from vendor 3dsi with new expiration year and expiration month

Pre-conditions:
1. Must be a registered user.
   -- user profile id
   -- exp year
   -- exp month
Post-conditions:
   -- card is updated and operation status returned


### HTTP Request 
`***PUT*** /creditcards/{userProfileId}/{cisCustNbr}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| updateCreditCardRqst | body | update credit card information | Yes |  |
| userProfileId | path | Unique Id of the User Profile | Yes | string |
| cisCustNbr | path | CIS Customer Number | Yes | string |
| format | query | Specify the format for responses. JSON or XML. Defaults to JSON | No | string |
| Transaction-Timestamp | header | For PUT and DELETE, the timestamp to check for concurrent updates | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |

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

# /CREDIT-CARDS/{USERPROFILEID}
## ***GET*** 

**Summary:** listUserCreditCardDetails - show credit (E/A) accounts for a user

**Description:** The operation gets all info for accounts that were setup to be eligible for credit card or already registered for credit card for a given web user

Pre-conditions:
1. Must be a registered user.
   -- no iuput required
Post-conditions:
all info of the associatd account for user is returned


### HTTP Request 
`***GET*** /credit-cards/{userProfileId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| userProfileId | path | Unique id of the User Profile | Yes | integer |
| format | query | Specify the format for responses. JSON or XML. Defaults to JSON | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |

# /USER-ACCOUNTS/{ACCTINSTID}
## ***GET*** 

**Summary:** getUserAccountDetails - Basic info for a user account

**Description:** The operation gets basic details for the requested user account.

Pre-conditions:
1. Must be a registered user.
   -- profileInstId is mandatory
Post-conditions:
1. The customer is registered and has accounts linked to the user profile. Status code 200 along with list is returned.
2. If no account is found or if the user is not authorized to view the account then status code 404 will be returned.


### HTTP Request 
`***GET*** /user-accounts/{acctInstId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| profileInstId | query | The unique identifier for the profile. | No | string |
| acctInstId | path | The unique identifier for the account. | Yes | string |
| format | query | Specify the format for responses. JSON or XML. Defaults to JSON | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |

# /USER-PROFILES/{PROFILEINSTID}/ADDRESS-BOOK
## ***GET*** 

**Summary:** listCustomerAddressBook - List customer address book details

**Description:** This operation will return a customer's Address Book based on their profileInstId or optionally their logon username.

Pre-conditions:
1. Must be a registered user.

Post-conditions:
1. Return address book entries.  
2. If the fields cannot be returned, an error message is returned.

### HTTP Request 
`***GET*** /user-profiles/{profileInstId}/address-book` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| profileInstId | path | The instance ID for the profile of the user who is attempting to access their account. | Yes | string |
| logonUsername | query | The username used to log in to the user's account. | No | string |
| levelOfDetail | query |  | No | string |
| numberOfRows | query | page size - number of rows | No | integer |
| startAt | query | start at row number | No | integer |
| fields | query | List of fields to include in response - if not populated, this will return all fields specified in the response type | No | array |
| sortByFieldName | query | Name of the column for sort | No | array |
| sortOrder | query | asc - ascending, desc - descending | No | array |
| format | query | Specify the format for responses. JSON or XML. Defaults to JSON | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |

# /AUTHORIZED-USERS/{CISCUSTNBR}
## ***GET*** 

**Summary:** listCisAuthorizedAccountUsers - Lists users authorized for given account

**Description:** The operation lists all users that are authorized for a given CIS account.

Pre-condition(s):
1. A valid CIS customer number is provided.

Post-condition(s):
1. If the number is valid, all users' logonIds that are authorized are returned.
2. Otherwise an appropriate error message is returned.

### HTTP Request 
`***GET*** /authorized-users/{cisCustNbr}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| cisCustNbr | path | The unique identifier of the CIS account. | Yes | string |
| format | query | Specify the format for responses. JSON or XML. Defaults to JSON | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |

# /CREDIT-CARDS-ADMIN/{USERPROFILEID}/{CISCUSTNBR}
## ***DELETE*** 

**Summary:** deleteEligibilityCardAdmin - Deletes eligibility and credit card

**Description:** The operation deletes an eligibility record from CIS_CUST_PROFILE and a previous registered card from vendor 3dsi if it is registered already.

Pre-conditions:
1. Must be a registered user.
   -- profile instance id
   -- cis customer number

Post-conditions:
1. The eligibility record is deleted.
2. The credit card is deleted from 3dsi if any exist with the input provided and operation status returned.
3. Otherwise an appropriate error message is returned.

### HTTP Request 
`***DELETE*** /credit-cards-admin/{userProfileId}/{cisCustNbr}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| userProfileId | path | Unique Id of user profile | Yes | string |
| cisCustNbr | path | CIS Customer Account Number | Yes | string |
| format | query | Specify the format for responses. JSON or XML. Defaults to JSON | No | string |
| Transaction-Timestamp | header | For PUT and DELETE, the timestamp to check for concurrent updates | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |

# /SUBMISSIONS/{SUBMISSIONID}/RESULT
## ***GET*** 

**Summary:** getSubmissionResultById - get submission results from 3dsi

**Description:** The operation gets a submission results from vendor 3dsi

Pre-conditions:
1. Must be a registered user.
   -- vendor name
   -- submission id
Post-conditions:
all info from a 3dsi submission is returned


### HTTP Request 
`***GET*** /submissions/{submissionId}/result` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| vendorName | query | name of the vendor | No | string |
| submissionId | path | a 3dsi submission id | Yes | string |
| cisCustNbr | query | CIS customer Number | No | string |
| userProfileId | query | user profile id | No | string |
| legalTermId | query | Identifier of Legal Terms | No | string |
| format | query | Specify the format for responses. JSON or XML. Defaults to JSON | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |

# /USER-PROFILES/{PROFILEINSTID}/ASSOCIATED-ACCOUNTS
## ***GET*** 

**Summary:** listAuthorizedUserAccounts - Basic info for a user account

**Description:** The operation gets basic details for the requested user account.

Pre-conditions:
1. Must be a registered user.
   -- profileInstId is mandatory
Post-conditions:
1. The customer is registered and has accounts linked to the user profile. Status code 200 along with list is returned.
2. If no account is found or if the user is not authorized to view the account then status code 404 will be returned.


### HTTP Request 
`***GET*** /user-profiles/{profileInstId}/associated-accounts` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| profileInstId | path | The unique identifier for the profile. | Yes | string |
| format | query | Specify the format for responses. JSON or XML. Defaults to JSON | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |

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

# /USER-ACCOUNTS/{USERPROFILEID}/{CISCUSTNBR}/APPLICATION
## ***POST*** 

**Summary:** addUserAccountByAppl - Adds used or pref acct by application

**Description:** The operation adds a used or preferred account by application. 

Pre-conditions:
1. Must be a registered user.
   -- user profile id
   -- cis nbr
   -- business unit code
   -- application id
   -- source code ('1'-admin (preferred); 'N' - from usage
   -- in-active indicator
   -- last update timestamp
   -- last update trans code
   -- last update UID

Post-conditions:
1. The application is designated as preferred or recently used when the record is added.
2. Otherwise an appropriate error message is returned.

### HTTP Request 
`***POST*** /user-accounts/{userProfileId}/{cisCustNbr}/application` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| addUserAccountByApplRqst | body |  | Yes |  |
| userProfileId | path | The unique identifier of the user profile. | Yes | string |
| cisCustNbr | path | The unique identifier of the CIS account. | Yes | string |
| format | query | Specify the format for responses. JSON or XML. Defaults to JSON | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |

# /USER-PROFILES/{PROFILEINSTID}/ACCOUNTS
## ***GET*** 

**Summary:** listUserAccountsByAppl - List of accounts for a user profile

**Description:** This operation will retrieve a list of CIS accounts that are associated with the customer profile. The list of accounts retrieved can be filtered based on Preferred or Recently used and for a given application.

Pre-conditions:
1. Must be a registered user.
   -- applName is mandatory (RateQuote or BOL etc)
   -- acctListType - P - Preferred Account List or R - Recently used account list - Optional. If not provided then all the accounts asoociated with the input profile will be retrieved.
Post-conditions:
1. The customer is registered and has a list of Preferred or Recently used accounts for input customer profile. Status code 200 along with list is returned.
2. If not customer found for given customer profile then status code 404 will be returned.


### HTTP Request 
`***GET*** /user-profiles/{profileInstId}/accounts` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| profileInstId | path | The instance ID for the profile of the user who is attempting to access their account. | Yes | string |
| acctInstId | query | Unique identifier of Customer Account | No | string |
| acctListType | query | Type of account to retrieve: R(Recently Used) or P(Preferred) | No | string |
| acctMadCd | query | Account MAD Code for the Customer | No | string |
| acctName | query | Account Name for the Customer | No | string |
| applName | query | Name of the Application - Ratequote or BOL etc. | No | string |
| businessUnitCode | query | Name of the busines unit | No | string |
| locationTypeCode | query | Type of Location | No | string |
| stateCd | query | State/Province code of the Customer | No | string |
| levelOfDetail | query |  | No | string |
| numberOfRows | query | page size - number of rows | No | integer |
| startAt | query | start at row number | No | integer |
| fields | query | List of fields to include in response - if not populated, this will return all fields specified in the response type | No | array |
| sortByFieldName | query | Name of the column for sort | No | array |
| sortOrder | query | asc - ascending, desc - descending | No | array |
| format | query | Specify the format for responses. JSON or XML. Defaults to JSON | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |

# /CREDIT-CARDS-ADMIN
## ***POST*** 

**Summary:** addEligibilityCardAdmin - Adds an eligibility

**Description:** The operation adds an eligibility card admin record to the DB.

Pre-conditions:
1. Must be a registered user.
   -- user profile id
   -- cis nbr

Post-conditions:
1. The eligibility record is added to DB if the input provided is valid.
2. Otherwise an appropriate error message is returned.

### HTTP Request 
`***POST*** /credit-cards-admin` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| addEligibilityCardAdminRqst | body | add eligibility information | Yes |  |
| format | query | Specify the format for responses. JSON or XML. Defaults to JSON | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 201 |  |

# /SUBMISSIONS/{USERPROFILEID}/{CISCUSTNBR}/ID
## ***GET*** 

**Summary:** getSubmissionIdByUserProfile - get submission id from 3dsi

**Description:** The operation gets a submission from vendor 3dsi

Pre-conditions:
1. Must be a registered user.
   -- vendor name
   -- cis customer number
Post-conditions:
a 3dsi submission id is returned


### HTTP Request 
`***GET*** /submissions/{userProfileId}/{cisCustNbr}/id` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| userProfileId | path | Unique Identifier of User profile | Yes | string |
| cisCustNbr | path | CIS Cust Nbr | Yes | string |
| vendorName | query | name of the vendor | No | string |
| format | query | Specify the format for responses. JSON or XML. Defaults to JSON | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 |  |

<!-- Converted with the swagger-to-slate https://github.com/lavkumarv/swagger-to-slate -->
