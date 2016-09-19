#Account Endpoints

## /Account

```shell
curl --request POST \
  --url '' \
  --header 'content-type: application/json' \
  --header 'x-api-key: 1234567890ABCDEFGHI' \
  --data '{\n    "client_id" : "ABCDEFG1234567",\n    "sf_field_id" : "unique_field__c",\n    "account" : {\n        "sf_field_value" : "ABC123456",\n        "Name" : "ACME",\n        "Custom_Field_API_Name__c" : "Value"\n    }\n}'
```

This endpoint creates, or updates, an Account within Salesforce.

If an Account cannot be found in Salesforce that matches the idenifier you specify (sf_field_id), a new Account will be created with all the attributes defined in the "account" object in the body of the request.

If an Account is found in Salesforce that does match the identifier, that Account will be updated with all the attributes defined in the "account" object in the body of the request.

### HTTP Request

`POST <Endpoint to be provisioned>`

### Headers

Name | Value
--------- | ------- 
Content-Type | application/json
x-api-key |  1234567890ABCDEFGHI

> Sample Body

```json
{
    "client_id" : "ABCDEFG1234567",
    "sf_field_id" : "unique_field__c",
    "sf_field_value" : "ABC123456",
    "account" : {
        "Name" : "ACME",
        "Custom_Field_API_Name__c" : "Value"
    }
}
```


### Body

Name | Data Type | Description
--------- | --------- | -----------
client_id | string | The unique identifier of the Saasli environment the request is destined for. This will be provisioned to you.
sf_field_id | string | The API name of the Salesforce Account field that uniquely identifies the Account.
sf_field_value | string | The value stored by the identifying Salesforce Account field, sf_field_id.

<aside class="notice">
Within the Account Object you may specify as many field values so long as the key matches the field's Salesforce API name and the value data type is the same as it is within Salesforce.
</aside>
<aside class="notice">
The only required field on the Account object is Name. If one isn't specified, the newly created account will have the name 'Unspecified'
</aside>



## /Accounts

```shell
curl --request POST \
  --url http:// \
  --header 'cache-control: no-cache' \
  --header 'content-type: application/json' \
  --data '{\n    "client_id" : "ABCDEFG1234567",\n    "sf_field_id" : "unique_field__c",\n    "accounts" : [\n      {\n        "sf_field_value" : "ABC123456",\n        "Name" : "ACME",\n        "Custom_Field_API_Name__c" : "Value"\n      }\n    ]\n}'
```

This endpoint creates, or updates, multiple Accounts within Salesforce.

If an Account cannot be found in Salesforce that matches the idenifier you specify (sf_field_id), a new Account will be created with all the attributes defined in the "accounts" object in the body of the request.

If an Account is found in Salesforce that does match the identifier, that Account will be updated with all the attributes defined in the "accounts" object in the body of the request.

### HTTP Request

`POST <Endpoint to be provisioned>`

### Headers

Name | Value
--------- | ------- 
Content-Type | application/json
x-api-key |  1234567890ABCDEFGHI

> Sample Body

```json
{
    "client_id" : "ABCDEFG1234567",
    "sf_field_id" : "unique_field__c",
    "accounts" : [
      {
        "sf_field_value" : "ABC123456",
        "Name" : "ACME",
        "Custom_Field_API_Name__c" : "Value"
      }
    ]
}
```

### Body

Name | Data Type | Description
--------- | --------- | -----------
client_id | string | The unique identifier of the Saasli environment the request is destined for. This will be provisioned to you.
sf_field_id | string | The API name of the Salesforce Account field that uniquely identifies the Account.
sf_field_value | string | The value stored by the identifying Salesforce Account field, sf_field_id.

<aside class="warning">
Within the Account Object you may specify as many field values so long as the key matches the field's Salesforce API name and the value data type is the same as it is within Salesforce.
</aside>
<aside class="warning">
The only required field on the Account object is Name. If one isn't specified, the newly created account will have the name 'Unspecified'
</aside>