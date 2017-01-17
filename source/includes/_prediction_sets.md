
# Prediction Sets

## Prediction Set Creation

All predictions are part of a prediction set. In the case of a prediction market, the prediction set will have a single prediction (aka. a trade), while an opinion pool question will have multiple predictions as part of a single prediction set (one for each answer in the question).

This endpoint can be used to submit new prediction sets. All prediction sets require a question id as part of the URL and must include parameters for the prediction set. See below for a list of required parameters. All parameters must be nested under a "prediction_set" key (see example request body below).


> Request:

```shell
curl -X "POST" "https://yoursite.cultivateforecasts.com/api/v1/questions/1/prediction_sets" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75" \
  -H "Content-Type: application/json" \
  -H "Accept: application/json" \
	-d "{\"prediction_set\":{\"rationale\":\"I think this is a great forecast\",\"predictions_attributes\":[{\"spend\":-595.9105910591059,\"forecasted_probability\":0.2,\"answer_id\":78}]}}"
```

> Request body example:

```json
{
  "prediction_set": {
    "rationale": "This is my rationale",
    "predictions_attributes": [
      {
        "spend": -595.91,
        "forecasted_probability": 0.2,
        "answer_id": 78
      }
    ]
  }
}
```


> Response:

The response contains the newly created prediction set and associated prediction(s).

```json
{
  "id": 16,
  "membership_id": 7,
  "membership_username": "superman7",
  "question_id": 36,
  "question_name": "lmsr_exclusive_market-8",
  "created_at": "2016-03-22T21:27:24.419Z",
  "updated_at": "2016-03-22T21:27:24.419Z",
  "rationale": "This is my rationale",
  "comment_id": 16,
  "predictions": [
    {
      "id": 16,
      "type": "Forecast::PM::LMSR::Trade",
      "answer_id": 78,
      "answer_name": "answer-name-78",
      "membership_id": 7,
      "filled_at": "2016-03-22T21:27:24.428Z",
      "refunded_at": null,
      "created_at": "2016-03-22T21:27:24.428Z",
      "updated_at": "2016-03-22T21:27:24.428Z",
      "confidence_level": null,
      "made_after_correctness_known": false,
      "spend": -595.91,
      "quantity": -8.6919,
      "forecasted_probability": 0.2,
      "starting_probability": 0.3333,
      "final_probability": 0.2,
      "starting_price": 0.3333,
      "final_price": 0.2959
    }
  ]
}
```

### HTTP Request

`POST https://yoursite.cultivateforecasts.com/api/v1/question/:question_id/prediction_sets`


### Prediction Set Parameters

Parameter | Required? | Description
--------- | --------- | -----------
rationale | Configurable per site | Contains the rationale/explanation/comment for why the user is making this forecast.
predictions_attributes | Yes | An array of prediction objects that are part of this prediction set. Valid parameters for a prediction are listed below.

### Prediction Parameters

Parameter | Required? | Description
--------- | --------- | -----------
answer_id | Yes | The answer id on which the user is forecasting.
forecasted_probability | Yes | The probability assigned to this answer by the user. Should be a float between 0 and 1.
spend | Only if the question is a prediction market | The amount of clinkles to buy/sell as part of this prediction/trade. A positive value indicates a buy, while a negative value indicates a sell/short.
