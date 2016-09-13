#Accounts

## /Account

```shell
curl --request POST \
  --url '' \
  --header 'content-type: application/json' \
  --header 'x-api-key: 1234567890ABCDEFGHI' \
  --data '{\n    "client_id" : "ABCDEFG1234567",\n    "sf_field_id" : "unique_field__c",\n    "account" : {\n        "sf_field_value" : "ABC123456",\n        "Name" : "ACME",\n        "Custom_Field_API_Name__c" : "Value"\n    }\n}'
```

This endpoint creates a new Account within Salesforce with a unique identifier specifed.

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
client_id | string | The unique identifier of the Saasli environment the request is destined for.
sf_field_id | string | The Salesforce API name of the field that uniquely identifies the object that triggered the event.
sf_field_value | string | The id value stored in the field specified by sf_field_id.

<aside class="notice">
Within the Account Object you may specify as many field values so long as the key matches the field's Salesforce API name and the value data type is the same as it is within Salesforce.
</aside>
<aside class="notice">
The only required field on the Account object is Name. If one isn't specified, the newly created account will have the name 'Unspecified'
</aside>



## /Accounts

```shell
curl --request POST \
  --url '' \
  --header 'content-type: application/json' \
  --header 'x-api-key: 1234567890ABCDEFGHI' \
  --data '{\n    "client_id" : "ABCDEFG1234567",\n    "sf_field_id" : "unique_field__c",\n    "accounts" : [\n        {\n            "sf_field_value" : "ABC123456",\n            "Name" : "ACME",\n            "Custom_Field_API_Name__c" : "Value"\n        }\n    ]\n}'
```

This endpoint creates new Accounts within Salesforce with a unique identifier specifed.

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
        "values" : {
          "Name" : "ACME",
          "Custom_Field_API_Name__c" : "Value"
        }
      }
    ]
}
```

### Body

Name | Data Type | Description
--------- | --------- | -----------
client_id | string | The unique identifier of the Saasli environment the request is destined for.
sf_field_id | string | The Salesforce API name of the field that uniquely identifies the object that triggered the event.
sf_field_value | string | The id value stored in the field specified by sf_field_id.

<aside class="warning">
Within the Account Object you may specify as many field values so long as the key matches the field's Salesforce API name and the value data type is the same as it is within Salesforce.
</aside>
<aside class="warning">
The only required field on the Account object is Name. If one isn't specified, the newly created account will have the name 'Unspecified'
</aside>