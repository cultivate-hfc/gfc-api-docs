
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
	-d "{\"external_prediction\":{\"value\":0.65724314,\"external_predictor_attributes\": {\"method_name\":\"red\"},\"forecast_at\":\"2016-10-10T14:15:19-05:00\",\"question_id\":5,\"answer_id\":15}}"
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
    },
    "forecast_at": "2017-01-17T12:00:00Z"
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


### External Predictions Parameters

Parameter | Required? | Description
--------- | --------- | -----------
value | Yes | Contains the value of the forecast. Must be a number between 1 and 0.
question_id | Yes | The question id associated with this forecast
answer_id | Yes | The answer id associated with this forecast
external_predictor_attributes[method_name] | Yes | A string identifying the method you're using to generate this forecast. Can be any string.
forecast_at | Yes | The timestamp as of when this forecast is valid. Must be in iso8601 format.
