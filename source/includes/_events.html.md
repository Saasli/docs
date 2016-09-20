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

`POST <Endpoint to be provisioned>`

### Headers

Name | Value
--------- | ------- 
*Content-Type* | application/json
*x-api-key* |  1234567890ABCDEFGHI

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

Name | Data Type | Description
--------- | --------- | -----------
*client_id* | string | The unique identifier of the Saasli environment the request is destined for. This will be provisioned to you.
*sf_object_id* | string | This must be either 'Account' or 'Contact'. This specifies the Salesforce object that triggered the event.
*sf_field_id* | string | The API name of the Salesforce field that uniquely identifies the Account or Contact that triggered the event.
*sf_field_value* | string | The value stored by the identifying Salesforce field, *sf_field_id*.
*event_name* | string | The name of the event that was performed by the specified Account or Contact.
*event_timestamp* | number | The UNIX timestamp that specifies the time at which the event was performed.


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

Name | Value
--------- | ------- 
*Content-Type* | application/json
*x-api-key* |  1234567890ABCDEFGHI


> Sample Body

```json
{
    "client_id" : "ABCDEFG1234567",
    "sf_object_id" : "Contact",
    "sf_field_id" : "unique_field__c",
    "events" : [
        {
            "sf_field_value" : "ABC123456",
            "event" : {
                "event_name" : "Logged In",
                "event_timestamp" : 1451606400
            }
        }
    ]
}
```

### Body

Name | Data Type | Description
--------- | --------- | -----------
*client_id* | string | The unique identifier of the Saasli environment the request is destined for. This will be provisioned to you.
*sf_object_id* | string | This must be either 'Account' or 'Contact'. This specifies the Salesforce object that triggered the event.
*sf_field_id* | string | The API name of the Salesforce field that uniquely identifies the Account or Contact that triggered the event.
*sf_field_value* | string | The value stored by the identifying Salesforce field, *sf_field_id*.
*event_name* | string | The name of the event that was performed by the specified Account or Contact.
*event_timestamp* | number | The UNIX timestamp that specifies the time at which the event was performed.

