
# External Predictions

## External Predictions Creation

This API is for submitting forecasts generated outside of Cultivate Forecasts, which will then be scored when the question/answer resolves.

Only administrators can access this API.

> Request:

```shell
curl -X "POST" "https://yoursite.cultivateforecasts.com/api/v1/external_predictions" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75" \
  -H "Content-Type: application/json" \
  -H "Accept: application/json" \
	-d "{\"external_prediction\":{\"value\":0.65724314,\"external_predictor_attributes\": {\"method_name\":\"red\"},\"question_id\":5,\"answer_id\":15}}"
```

> Request body example:

```json
{
  "external_prediction": {
    "value": 0.65724314,
    "question_id": 5,
    "answer_id": 15,
    "external_predictor_attributes": {
      "method_name": "red"
    }
  }
}
```


> Response:

The response contains the newly created prediction.

```json
{
  "id": 66,
  "question_id": 5,
  "answer_id": 15,
  "site_id": 153,
  "membership_id": 242,
  "method_name": "red",
  "created_at": "2017-01-17T12:00:01.299Z",
  "updated_at": "2017-01-17T12:00:01.299Z",
  "value": 0.65724314,
  "forecast_at": "2017-01-17T12:00:00Z"
}
```

### HTTP Request

`POST https://yoursite.cultivateforecasts.com/api/v1/external_predictions`


### Query Parameters

Parameter | Required? | Description
--------- | --------- | -----------
value | Yes | Contains the value of the forecast. Must be a number between 1 and 0.
question_id | Yes | The question id associated with this forecast
answer_id | Yes | The answer id associated with this forecast
external_predictor_attributes[method_name] | Yes | A string identifying the method you're using to generate this forecast. Can be any string.


### Attribute Descriptions

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The id of the external prediction
question_id | integer | The question id associated with this forecast
answer_id | integer | The answer id associated with this forecast
method_name | string | The name of the method used to generate the forecast
value | float | Contains the forecasted probability
forecast_at | date | The auto-generated timestamp of when this forecast was submitted. This timestamp is used for scoring forecasts.
site_id | string | The site id associated with this forecast
membership_id | string | The id of the membership that submitted this forecast
