
# Fundamental Activity Units

## Fundamental Activity Unit Creation

This API is to submit information about a fundamental activity unit that has been completed by a participant.

Only site administrators can access this API.

> Request:

```shell
curl -X "POST" "https://yoursite.hfc-staging.com/api/v1/fundamental_activity_units" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75" \
  -H "Content-Type: application/json" \
  -H "Accept: application/json" \
	-d "{\"fundamental_activity_unit\":{\"membership_id\":45,\"question_id\":83, \"fau_type\": \"forecast\",\"performed_at\": \"2017-01-17T12:00:01.299Z\",\"metadata\": {\"foo\":\"bar\"}}}"
```

> Request body example:

```json
{
  "fundamental_activity_unit": {
    "membership_id": 45,
    "question_id": 83,
    "hit_id": "03371126a8e900d73ba1b0acbb539670",
    "performed_at": "2017-01-17T12:00:01.299Z",
    "fau_type": "forecast",
    "metadata": {
      "foo":"bar"
    }
  }
}
```


> Response:

```json
{
  "id": 6,
  "membership_id": 45,
  "question_id": 83,
  "hit_id": "03371126a8e900d73ba1b0acbb539670",
  "performed_at": "2017-01-17T12:00:01.299Z",
  "fau_type": "forecast",
  "metadata": {"foo":"bar"},
  "created_at": "2017-01-17T12:00:01.299Z",
  "updated_at": "2017-01-17T12:00:01.299Z"
}
```

### HTTP Request

`POST https://yoursite.hfc-staging.com/api/v1/fundamental_activity_units`


### Query Parameters

Parameter | Required? | Description
--------- | --------- | -----------
membership_id | Yes | The membership id of the user who performed the action
question_id | No | The question id that this action was performed on. Can be left blank if the FAU pertains to more than one question
hit_id | No | The hit id for the task that the user was completing when he/she performed this FAU
fau_type | Yes | A string describing the type of FAU (e.g. forecast, annotation, rating)
performed_at | Yes | An ISO8601-formatted timestamp of when the FAU was performed
metadata | Yes | A JSON-formatted string describing the action taken by the user


### Attribute Descriptions

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The id of the external prediction
membership_id | integer | The membership id of the user who performed the action
metadata | hash | A JSON-formatted string describing the action taken by the user
question_id | integer | The question id that this action was performed on.
hit_id | string | The hit id for the task that the user was completing when he/she performed this FAU
performed_at | Yes | An ISO8601-formatted timestamp of when the FAU was performed
fau_type | string | A string describing the type of FAU (e.g. forecast, annotation, rating)
