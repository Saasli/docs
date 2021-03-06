#Contact Endpoints

## /Contact

```shell
curl --request POST \
  --url '' \
  --header 'content-type: application/json' \
  --header 'x-api-key: 1234567890ABCDEFGHI' \
  --data '{\n    "client_id" : "ABCDEFG1234567",\n    "sf_account_field_id" : "Id",\n    "sf_field_id" : "unique_field__c",\n    "contact" : {\n        "sf_account_field_value" : "00158000006mkd1AAA",\n        "sf_field_value" : "ABC123456",\n        "LastName" : "Jones",\n\n        "Name" : "Sam",\n        "Phone" : "+1 123 123 1234",\n        "Custom_Field_API_Name__c" : "Value"\n    }\n}'
```

This endpoint creates, or updates, a Contact within Salesforce.

If a Contact cannot be found in Salesforce that matches the idenifier you specify (*sf_field_id*), a new Contact will be created with all the attributes defined in the *contact* object in the body of the request.

If a Contact is found in Salesforce that matches the identifier, that Contact will be updated with all the attributes defined in the *contact* object in the body of the request.

### HTTP Request

`POST https://api.saasli.com/v1/contact/{account_id_field}/{contact_id_field}`

### Headers

Name | Value | Required?
--------- | ------- | --------- 
*Content-Type* | application/json | Yes
*x-api-key* |  1234567890ABCDEFGHI | Yes

### URL Parameters

Name | Description | Required?
--------- | ------- | --------- 
*account_id_field* | The full API name of the Salesforce field that will be used to identify the account. That field must also exist in the account object defined in the body | Yes
*contact_id_field* | The full API name of the Salesforce field that will be used to identify the contact. That field must also exist in the contact object defined in the body | Yes

> Sample Body

```json
{
    "client_id" : "ad2d965b-57d9-4943-a879-c2a33d9a857b",
    "contact" : {
        "LastName" : "Jones",
        "FirstName" : "Sam",
        "Phone" : "+1 123 123 1234",
        "Custom_Field_API_Name__c" : "Value"
        etc.
    }
}
```


### Body

Name | Data Type | Description | Required?
--------- | --------- | ----------- | --------- 
*client_id* | string | The unique identifier of the Saasli environment the request is destined for. This will be provisioned to you. | Yes
*contact* | object | A key/value representation of the Salesforce field API name and it's desired value. | Yes
*LastName* | string | The last name of the contact. This is a required Salesforce field. | Yes


<aside class="notice">
You may specify as many Salesforce Contact field API names, and their corresponding values, as you would like in the <i>contact</i> object in the body of the request, except for the record id field: <i>Id</i>.
</aside>
<aside class="warning">
<i>LastName</i> is a required Salesforce Contact field. If one isn't specified, the request will return an error.
<!--If one isn't specified, the newly created contact will have the last name 'Unspecified'.-->
</aside>



## /Contacts

```shell
curl --request POST \
  --url https://hjfielpxwj.execute-api.us-east-1.amazonaws.com/dev/contact/Id/Phone \
  --header 'cache-control: no-cache' \
  --header 'content-type: application/json' \
  --data '{\n    "client_id" : "saasli",\n    "account" : {\n     "Id" : "0011a00000CXH5xAAH" \n    },\n    "contact" : {\n        "LastName" : "Waites",\n        "FirstName" : "Tom",\n        "Phone" : "+1 123 123 1234"\n    }\n}'
 ```

This endpoint creates, or updates, multiple Contacts within Salesforce.

If a Contact cannot be found in Salesforce that matches the idenifier you specify (*contact_id_field*), a new Contact will be created with all the attributes defined in the *contacts* object in the body of the request.

If a Contact is found in Salesforce that matches the identifier, that Contact will be updated with all the attributes defined in the *contacts* object in the body of the request.

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
    "sf_account_field_id" : "Id",
    "sf_field_id" : "unique_field__c",
    "contacts" : [
        {
            "sf_account_field_value" : "00158000006mkd1AAA",
            "sf_field_value" : "ABC123456",
            "LastName" : "Jones",

            "FirstName" : "Sam",
            "Phone" : "+1 123 123 1234",
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
*sf_account_field_id* | string | The API name of the Salesforce Account field that uniquely identifies the Account of the Contact. | Yes
*sf_field_id* | string | The API name of the Salesforce Contact field that uniquely identifies the Contact. | Yes
*contacts* | object | The object in the request that contains the array of contact data. | Yes
*sf_account_field_value* | string | The value stored by the identifying Salesforce Account field, *sf_account_field_id*. | Yes
*sf_field_value* | string | The value stored by the identifying Salesforce Contact field, *sf_field_id*. | Yes
*LastName* | string | The last name of the contact. This is a required Salesforce field. | Yes

<aside class="notice">
You may specify as many Salesforce Contact field API names, and their corresponding values, as you would like in the <i>contacts</i> object in the body of the request, except for the record id field: <i>Id</i>.
</aside>
<aside class="warning">
<i>LastName</i> is a required Salesforce Contact field. If one isn't specified, the request will return an error.
<!--If one isn't specified, the newly created contact will have the last name 'Unspecified'.-->
</aside>
<aside class="warning">
An <i>account_id_field</i>, and its associated value within the <i>account</i> object, <b>must</b> be provided. If either of the two are not specified, the request will return an error.
</aside>
