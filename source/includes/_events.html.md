# Event Endpoints

## /Event

```shell
curl --request POST \
  --url '' \
  --header 'content-type: application/json' \
  --header 'x-api-key: 1234567890ABCDEFGHI' \
  --data '{\n    "client_id" : "ABCDEFG1234567",\n    "sf_object_id" : "Contact",\n    "sf_field_id" : "unique_field__c",\n    "sf_field_value" : "ABC123456",\n    "event" : {\n        "event_name" : "Logged In",\n        "event_timestamp" : 1451606400\n    }\n}'
```

This endpoint logs a single event against a single Salesforce object (either an Account or a Contact).

### HTTP Request

`POST https://api.saasli.com/v1/event`

### Headers

Name | Value | Required?
--------- | ------- | --------- 
*Content-Type* | application/json | Yes
*x-api-key* |  1234567890ABCDEFGHI | Yes

> Sample Body

```json
{
    "client_id" : "ABCDEFG1234567",
    "sf_object_id" : "Contact",
    "sf_field_id" : "unique_field__c",
    "sf_field_value" : "ABC123456",
    "event" : {
        "event_name" : "Logged In",
        "event_timestamp" : 1451606400
    }
}
```

### Body

Name | Data Type | Description | Required?
--------- | --------- | ----------- | --------- 
*client_id* | string | The unique identifier of the Saasli environment the request is destined for. This will be provisioned to you. | Yes
*sf_object_id* | string | This must be either 'Account' or 'Contact'. This specifies the Salesforce object that triggered the event. | Yes
*sf_field_id* | string | The API name of the Salesforce field that uniquely identifies the Account or Contact that triggered the event. | Yes
*sf_field_value* | string | The value stored by the identifying Salesforce field, *sf_field_id*. | Yes
*event_name* | string | The name of the event that was performed by the specified Account or Contact. | Yes
*event_timestamp* | number | The UNIX timestamp that specifies the time at which the event was performed. | Yes


## /Events

```shell
curl --request POST \
  --url '' \
  --header 'content-type: application/json' \
  --header 'x-api-key: 1234567890ABCDEFGHI' \
  --data '{\n    "client_id" : "ABCDEFG1234567",\n    "sf_object_id" : "Contact",\n    "sf_field_id" : "unique_field__c",\n    "events" : [\n        {\n            "sf_field_value" : "ABC123456",\n            "event" : {\n                "event_name" : "Logged In",\n                "event_timestamp" : 1451606400\n            }\n        }\n    ]\n}'
```

This endpoint logs multiple events against multiple Salesforce objects (either Accounts or Contacts).

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
    "sf_object_id" : "Account",
    "sf_field_id" : "Name",
    "sf_lookup_id" : "Account__c"
    "events" : [
        {
            "sf_field_value" : "Acme 2",
            "event" : {
                "event_name" : "Logged In",
                "event_timestamp" : 1451606400
            }
        },
        {
            "sf_field_value" : "New Account",
            "event" : {
                "event_id" : 123,
                "event_name" : "Logged Out",
                "event_timestamp" : 1451616400,
                "event_values" : {
                  "Product__c" : "Ford"
                }
            }
        },
        {
            "sf_field_value" : "Acme 2",
            "event" : {
                "event_name" : "Try New Event Name",
                "event_timestamp" : 1451606400,
                "event_values" : {
                  "Product__c" : "Chevy"
                }
            }
        }
    ]
}
```

### Body

Name | Data Type | Description | Required?
--------- | --------- | ----------- | --------- 
*client_id* | string | The unique identifier of the Saasli environment the request is destined for. This will be provisioned to you. | Yes
*sf_object_id* | string | This must be either 'Account' or 'Contact'. This specifies the Salesforce object that triggered the event. | Yes
*sf_field_id* | string | The API name of the Salesforce field that uniquely identifies the Account or Contact that triggered the event. | Yes
*sf_lookup_id* | string | The API name of the lookup field on the events object that will reference the triggering object. | Yes
*sf_field_value* | string | The value stored by the identifying Salesforce field, *sf_field_id*. | Yes
*event_name* | string | The name of the event that was performed by the specified Account or Contact. | Yes
*event_timestamp* | number | The UNIX timestamp that specifies the time at which the event was performed. | Yes
*event_id* | string | A unique id of the event occurence. Will be generated automatically if this is omitted. Useful for deduplication of events as any duplicate ids will be 'upserted'. | No
*event_values* | object | Field API Name to value mappings that should also be added to the record. Useful if storing aggregate information. The data type must match the type defined in Salesforce. | No

