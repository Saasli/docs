#Contact Endpoints

## /Contact

```shell
curl --request POST \
  --url '' \
  --header 'content-type: application/json' \
  --header 'x-api-key: 1234567890ABCDEFGHI' \
  --data '{\n    "client_id" : "ABCDEFG1234567",\n    "sf_field_id" : "unique_field__c",\n    "contact" : {\n        "sf_field_value" : "ABC123456",\n        "Name" : "John Doe",\n        "Custom_Field_API_Name__c" : "Value"\n    }\n}'
```

This endpoint creates, or updates, a Contact within Salesforce.

If a Contact cannot be found in Salesforce that matches the idenifier you specify (sf_field_id), a new Contact will be created with all the attributes defined in the "contact" object in the body of the request.

If a Contact is found in Salesforce that matches the identifier, that Contact will be updated with all the attributes defined in the "contact" object in the body of the request.

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
client_id | string | The unique identifier of the Saasli environment the request is destined for. This will be provisioned to you.
sf_account_field_id | string | The API name of the Salesforce Account field that uniquely identifies the Account of the Contact.
sf_field_id | string | The API name of the Salesforce Contact field that uniquely identifies the Contact.
contact | object | The object that contains the contact data.
sf_account_field_value | string | The value stored by the identifying Salesforce Account field, sf_account_field_id.
sf_field_value | string | The value stored by the identifying Salesforce Contact field, sf_field_id.


<aside class="notice">
You may specify as many Salesforce Contact field API names, and their corresponding values, as you would like in the "contact" object in the body of the request, except for the record id field: Id.
</aside>
<aside class="warning">
The only required field on the Contact object is LastName. If one isn't specified, the request will return an error.
<!--If one isn't specified, the newly created contact will have the last name 'Unspecified'.-->
</aside>
<aside class="warning">
An sf_account_field_id, and its associated value sf_account_field_value, <strong>MUST</strong> be provided.
</aside>



## /Contacts

```shell
curl --request POST \
  --url '' \
  --header 'content-type: application/json' \
  --header 'x-api-key: 1234567890ABCDEFGHI' \
  --data '{\n    "client_id" : "ABCDEFG1234567",\n    "sf_field_id" : "unique_field__c",\n    "contacts" : [\n        {\n            "sf_field_value" : "ABC123456",\n            "Name" : "Logged In",\n            "Company" : "ACME",\n            "Custom_Field_API_Name__c" : "Value"\n        }\n    ]\n}'
  ```

This endpoint creates, or updates, multiple Contacts within Salesforce.

If a Contact cannot be found in Salesforce that matches the idenifier you specify (sf_field_id), a new Contact will be created with all the attributes defined in the "contacts" object in the body of the request.

If a Contact is found in Salesforce that matches the identifier, that Contact will be updated with all the attributes defined in the "contacts" object in the body of the request.

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
client_id | string | The unique identifier of the Saasli environment the request is destined for. This will be provisioned to you.
sf_account_field_id | string | The API name of the Salesforce Account field that uniquely identifies the Account of the Contact.
sf_field_id | string | The API name of the Salesforce Contact field that uniquely identifies the Contact.
contacts | object | The object that contains the array of contact data.
sf_account_field_value | string | The value stored by the identifying Salesforce Account field, sf_account_field_id.
sf_field_value | string | The value stored by the identifying Salesforce Contact field, sf_field_id.

<aside class="notice">
You may specify as many Salesforce Contact field API names, and their corresponding values, as you would like in the "contacts" object in the body of the request, except for the record id field: Id.
</aside>
<aside class="warning">
The only required field on the Contact object is LastName. If one isn't specified, the request will return an error.
<!--If one isn't specified, the newly created contact will have the last name 'Unspecified'.-->
</aside>
<aside class="warning">
An sf_account_field_id, and its associated value sf_account_field_value, <strong>MUST</strong> be provided.
</aside>
</aside>
