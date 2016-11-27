
# Aggregate Forecasts

## Aggregate Forecast Creation

Only administrators can access this API.

> Request:

```shell
curl -X "POST" "https://yoursite.cultivateforecasts.com/api/v1/aggregate_forecasts" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75" \
  -H "Content-Type: application/json" \
  -H "Accept: application/json" \
	-d "{\"aggregate_forecast\":{\"value\":0.2423,\"method_name\":\"red\",\"forecast_at\":\"2016-10-10T14:15:19-05:00\",\"question_id\":5,\"answer_id\":15}}"
```

> Request body example:

```json
{
  "aggregate_forecast": {
    "value" : 0.65724314,
    "question_id" : 5,
    "answer_id" : 15,
    "method_name" : "red",
    "forecast_at" : "2016-10-10T14:15:19-05:00"
  }
}
```


> Response:

The response contains the newly created earned badge.

```json
{
  "id": 5,
  "badge_id": 5,
  "membership_id": 23,
  "created_at": "2016-04-19T15:09:56.538Z",
  "updated_at": "2016-04-19T15:09:56.538Z",
  "featured": false
}
```

### HTTP Request

`POST https://yoursite.cultivateforecasts.com/api/v1/aggregate_forecasts`


### Aggregate Forecast Parameters

Parameter | Required? | Description
--------- | --------- | -----------
value | Yes | Contains the value of the forecast. Must be a number between 1 and 0.
question_id | Yes | The question id associated with this forecast
answer_id | Yes | The answer id associated with this forecast
method_name | Yes | A string identifying the method you're using to generate this forecast. Can be any string.
forecast_at | Yes | The timestamp as of which this forecast is valid. Must be in iso8601 format.
