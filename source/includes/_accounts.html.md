#Account Endpoints

## /Account

```shell
curl --request POST \
  --url '' \
  --header 'content-type: application/json' \
  --header 'x-api-key: 1234567890ABCDEFGHI' \
  --data '{\n    "client_id" : "ABCDEFG1234567",\n    "sf_field_id" : "unique_field__c",\n    "sf_field_value" : "ABC123456",\n    "account" : {\n        "Name" : "ACME",\n\n        "Website" : "https://www.companywebsite.com",\n        "Custom_Field_API_Name__c" : "Value"\n    }\n}'
```

This endpoint creates, or updates, an Account within Salesforce.

If an Account cannot be found in Salesforce that matches the idenifier you specify (*account_id_field*), a new Account will be created with all the attributes defined in the *account* object in the body of the request.

If an Account is found in Salesforce that does match the identifier, that Account will be updated with all the attributes defined in the *account* object in the body of the request.

### HTTP Request

`POST https://api.saasli.com/v1/account/{account_id_field}`

### Headers

Name | Value | Required?
--------- | ------- | --------- 
*Content-Type* | application/json | Yes
*x-api-key* |  1234567890ABCDEFGHI | Yes

### URL Parameters

Name | Description | Required?
--------- | ------- | --------- 
*account_id_field* | The full API name of the Salesforce field that will be used to identify the account. That field must also exist in the account object defined in the body | Yes

> Sample Body

```json
{
    "client_id" : "ad2d965b-57d9-4943-a879-c2a33d9a857b",
    "account" : {
        "Name" : "ACME",
        "Id" : "0011a00000DlaOMAAZ"
    }
}
```


### Body

Name | Data Type | Description | Required?
--------- | --------- | ----------- | --------- 
*client_id* | string | The unique identifier of the Saasli environment the request is destined for. This will be provisioned to you. | Yes
*account* | object | A key/value representation of the Salesforce field API name and it's desired value. | Yes

<aside class="notice">
You may specify as many Salesforce Account field API names, and their corresponding values, as you would like in the <i>account</i> object in the body of the request, except for the record id field: <i>Id</i>.
</aside>
<aside class="warning">
<i>Name</i> is a required Salesforce Account field. If one isn't specified, the request will return an error.
<!--If one isn't specified, the newly created Account will have the name 'Unspecified'.-->
</aside>



## /Accounts

```shell
curl --request POST \
  --url https://hjfielpxwj.execute-api.us-east-1.amazonaws.com/dev/account/Id \
  --header 'cache-control: no-cache' \
  --header 'content-type: application/json' \
  --data '{\n    "client_id" : "ad2d965b-57d9-4943-a879-c2a33d9a857b",\n    "account" : {\n        "Name" : "ACME",\n        "Id" : "0011a00000DlaOMAAZ"\n    }\n}'
```

This endpoint creates, or updates, multiple Accounts within Salesforce.

If an Account cannot be found in Salesforce that matches the idenifier you specify (*sf_field_id*), a new Account will be created with all the attributes defined in the *accounts* object in the body of the request.

If an Account is found in Salesforce that does match the identifier, that Account will be updated with all the attributes defined in the *accounts* object in the body of the request.

### HTTP Request

`POST <Endpoint to be provisioned>`

### Headers

Name | Value | Required?
--------- | ------- | --------- 
*Content-Type* | application/json | Yes
*x-api-key* |  1234567890ABCDEFGHI | Yes

> Sample Body

```json
{
    "client_id" : "ABCDEFG1234567",
    "sf_field_id" : "unique_field__c",
    "accounts" : [
      {
        "sf_field_value" : "ABC123456",
        "Name" : "ACME",

        "Website" : "https://www.companywebsite.com",
        "Custom_Field_API_Name__c" : "Value"
        etc.
      }
    ]
}
```

### Body

Name | Data Type | Description | Required?
--------- | --------- | ----------- | --------- 
*client_id* | string | The unique identifier of the Saasli environment the request is destined for. This will be provisioned to you. | Yes
*sf_field_id* | string | The API name of the Salesforce Account field that uniquely identifies the Account. | Yes
*sf_field_value* | string | The value stored by the identifying Salesforce Account field, *sf_field_id*. | Yes
*Name* | string | The name of the account. This is a required Salesforce field. | Yes

<aside class="notice">
You may specify as many Salesforce Account field API names, and their corresponding values, as you would like in the <i>accounts</i> object in the body of the request, except for the record id field: <i>Id</i>.
</aside>
<aside class="warning">
<i>Name</i> is a required Salesforce Account field. If one isn't specified, the request will return an error.
<!--If one isn't specified, the newly created Account will have the name 'Unspecified'.-->
</aside>