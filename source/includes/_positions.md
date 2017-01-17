
# Positions

## Positions List

This API returns a list of a user's positions. This API is only accessible for the positions owned by the user who owns the oauth token that is included.

Each position record contains information about the most recent forecast made by the user in a given answer. It also includes information about any accumulated shares in prediction market-type questions.

> Request:

```shell
curl "https://yoursite.cultivateforecasts.com/api/v1/positions" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Response:

```json
{
  "positions": [
    {
      "id": 32,
      "answer_name": "answer-name-4",
      "answer_id": 248,
      "created_at": "2017-01-17T20:07:30.360Z",
      "membership_id": 245,
      "question_name": "question-name-2",
      "question_id": 198,
      "resolved_at": null,
      "type": "Forecast::PM::Position",
      "last_prediction_at": "2017-01-10T20:07:30.347Z",
      "updated_at": "2017-01-17T20:07:30.360Z",
      "answer_current_consensus": 0.3333,
      "consensus_at_time_of_last_prediction": 0,
      "gain_loss_cache": 0,
      "latest_prediction_probability": 0,
      "liquidation_value_cache": 0,
      "long_investment": 0,
      "long_quantity": 0,
      "short_investment": 0,
      "short_quantity": 0,
      "net_quantity": 0
    },
    {
      "id": 33,
      "answer_name": "answer-name-6",
      "answer_id": 250,
      "created_at": "2017-01-17T20:07:30.365Z",
      "membership_id": 245,
      "question_name": "question-name-2",
      "question_id": 198,
      "resolved_at": null,
      "type": "Forecast::PM::Position",
      "last_prediction_at": "2017-01-03T20:07:30.363Z",
      "updated_at": "2017-01-17T20:07:30.365Z",
      "answer_current_consensus": 0.3333,
      "consensus_at_time_of_last_prediction": 0,
      "gain_loss_cache": 0,
      "latest_prediction_probability": 0,
      "liquidation_value_cache": 0,
      "long_investment": 0,
      "long_quantity": 0,
      "short_investment": 0,
      "short_quantity": 0,
      "net_quantity": 0
    },
    {
      "id": 31,
      "answer_name": "answer-name-1",
      "answer_id": 245,
      "created_at": "2017-01-17T20:07:30.137Z",
      "membership_id": 245,
      "question_name": "question-name-1",
      "question_id": 197,
      "resolved_at": null,
      "type": null,
      "last_prediction_at": "2016-12-17T20:07:30.116Z",
      "updated_at": "2017-01-17T20:07:30.137Z",
      "answer_current_consensus": 0.333333333,
      "consensus_at_time_of_last_prediction": 0,
      "gain_loss_cache": 0,
      "latest_prediction_probability": 0,
      "liquidation_value_cache": 0,
      "long_investment": 0,
      "long_quantity": 0,
      "short_investment": 0,
      "short_quantity": 0
    }
  ]
}
```

### HTTP Request

`GET https://yoursite.cultivateforecasts.com/api/v1/positions`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 0 | Pagination page number
sort | none | The order in which to sort the positions. Valid values include `question_name` `answer_name`, `answer_current_price`, `quantity`, `total_investment`, `gain_loss`, `liquidation_value`, `answer_last_prediction`. By default, positions are sorted with most recently updated forecasts first.
dir | "desc" | The sort direction to apply to the sort filter. Valid values include `asc` and `desc`
filter | none | A filter to apply to the positions list. Valid values include `closed` (positions in closed/ended questions) and `resolved` (positions in resolved questions). If no filter is passed, only positions in active answers will be included.
