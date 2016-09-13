# Events

## /Event

```shell
curl --request POST \
  --url '' \
  --header 'content-type: application/json' \
  --header 'x-api-key: 1234567890ABCDEFGHI' \
  --data '{\n    "client_id" : "ABCDEFG1234567",\n    "sf_object_id" : "Contact",\n    "sf_field_id" : "unique_field__c",\n    "sf_field_value" : "ABC123456",\n    "event" : {\n        "name" : "Logged In",\n        "logged_at" : 1451606400\n    }\n}'
```

This endpoint logs a single event against a single Salesforce object.

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
    "sf_object_id" : "Contact",
    "sf_field_id" : "unique_field__c",
    "sf_field_value" : "ABC123456",
    "event" : {
        "name" : "Logged In",
        "logged_at" : 1451606400
    }
}
```

### Body

Name | Data Type | Description
--------- | --------- | -----------
client_id | string | The unique identifier of the Saasli environment the request is destined for.
sf_object_id | string | The Salesforce API name of the object responsible for the event.
sf_field_id | string | The Salesforce API name of the field that uniquely identifies the object that triggered the event.
sf_field_value | string | The id value stored in the field specified by sf_field_id.
name | string | The name of the event that was performed by the object specified.
logged_at | number | The UNIX timestamp of when said event was performed.


## /Events

```shell
curl --request POST \
  --url '' \
  --header 'content-type: application/json' \
  --header 'x-api-key: 1234567890ABCDEFGHI' \
  --data '{\n    "client_id" : "ABCDEFG1234567",\n    "sf_object_id" : "Contact",\n    "sf_field_id" : "unique_field__c",\n    "events" : [\n        {\n            "sf_field_value" : "ABC123456",\n            "event" : {\n                "name" : "Logged In",\n                "logged_at" : 1451606400\n            }\n        }\n    ]\n}'
```

This endpoint logs multiple events against multiple Salesforce objects.

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
    "sf_object_id" : "Contact",
    "sf_field_id" : "unique_field__c",
    "events" : [
        {
            "sf_field_value" : "ABC123456",
            "event" : {
                "name" : "Logged In",
                "logged_at" : 1451606400
            }
        }
    ]
}
```

### Body

Name | Data Type | Description
--------- | --------- | -----------
client_id | string | The unique identifier of the Saasli environment the request is destined for.
sf_object_id | string | The object within Salesforce that is responsible for the event.
sf_field_id | string | The Salesforce API name of the field that uniquely identifies the object that triggered the event.
sf_field_value | string | The id value stored in the field specified by sf_field_id.
name | string | The name of the event that was performed by the object specified.
logged_at | number | The UNIX timestamp of when said event was performed.

