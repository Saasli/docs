#Contacts

## /Contact

```shell
curl --request POST \
  --url '' \
  --header 'content-type: application/json' \
  --header 'x-api-key: 1234567890ABCDEFGHI' \
  --data '{\n    "client_id" : "ABCDEFG1234567",\n    "sf_field_id" : "unique_field__c",\n    "contact" : {\n        "sf_field_value" : "ABC123456",\n        "Name" : "John Doe",\n        "Custom_Field_API_Name__c" : "Value"\n    }\n}'
```

This endpoint creates, or updates, a Contact within Salesforce. If a Contact cannot be found in Salesforce that matches the idenifier you specify (sf_field_id), a new Contact will be created with all the attributes defined in the "contact" object in the body of the request. If a Contact is found in Salesforce that does match the identifier, that Contact will be updated with all the attributes defined in the "contact" object.

with a unique identifier specifed.

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
    "sf_account_field_id" : "Id",
    "sf_field_id" : "unique_field__c",
    "contact" : {
        "sf_account_field_value" : "00158000006mkd1AAA",
        "sf_field_value" : "ABC123456",
        "Name" : "John Doe",
        "Custom_Field_API_Name__c" : "Value"
    }
}
```


### Body

Name | Data Type | Description
--------- | --------- | -----------
client_id | string | The unique identifier of the Saasli environment the request is destined for.
sf_account_field_id | string | The API name of the field on the Contact's Account object that holds the identifer. 
sf_field_id | string | The Salesforce API name of the field that uniquely identifies the object that triggered the event.
sf_account_field_value | string | The Id of the Contact's Account stored in the field specified by sf_account_field_id
sf_field_value | string | The id value stored in the field specified by sf_field_id.

<aside class="warning">
Within the Contact Object you may specify as many field values so long as the key matches the field's Salesforce API name and the value data type is the same as it is within Salesforce.
</aside>
<aside class="warning">
The only required field on the Contact object is LastName. If one isn't specified, the newly created contact will have the last name 'Unspecified'
</aside>



## /Contacts

```shell
curl --request POST \
  --url '' \
  --header 'content-type: application/json' \
  --header 'x-api-key: 1234567890ABCDEFGHI' \
  --data '{\n    "client_id" : "ABCDEFG1234567",\n    "sf_field_id" : "unique_field__c",\n    "contacts" : [\n        {\n            "sf_field_value" : "ABC123456",\n            "Name" : "Logged In",\n            "Company" : "ACME",\n            "Custom_Field_API_Name__c" : "Value"\n        }\n    ]\n}'
  ```

This endpoint creates, or updates, multiple Contacts within Salesforce. If a Contact cannot be found in Salesforce that matches the idenifier you specify (sf_field_id), a new Contact will be created with all the attributes defined in the "contact" object in the body of the request. If a Contact is found in Salesforce that does match the identifier, that Contact will be updated with all the attributes defined in the "contact" object.

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
    "sf_account_field_id" : "Id",
    "sf_field_id" : "unique_field__c",
    "contacts" : [
        {
            "sf_account_field_value" : "00158000006mkd1AAA",
            "sf_field_value" : "ABC123456",
            "Name" : "Logged In",
            "Company" : "ACME",
            "Custom_Field_API_Name__c" : "Value"
        }
    ]
}
```

### Body

Name | Data Type | Description
--------- | --------- | -----------
client_id | string | The unique identifier of the Saasli environment the request is destined for.
sf_account_field_id | string | The API name of the field on the Contact's Account object that holds the identifer. 
sf_field_id | string | The Salesforce API name of the field that uniquely identifies the object that triggered the event.
sf_account_field_value | string | The Id of the Contact's Account stored in the field specified by sf_account_field_id
sf_field_value | string | The id value stored in the field specified by sf_field_id.

<aside class="notice">
Within the Contact Object you may specify as many field values so long as the key matches the field's Salesforce API name and the value data type is the same as it is within Salesforce.
</aside>
<aside class="notice">
The only required field on the Contact object is LastName. If one isn't specified, the newly created contact will have the last name 'Unspecified'
</aside>
