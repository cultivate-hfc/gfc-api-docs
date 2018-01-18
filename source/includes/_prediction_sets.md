
# Prediction Sets

A prediction set is the primary model for storing forecasts within Cultivate Forecasts. A prediction set will contain one prediction for each answer in the question.

This endpoint provides a stream of individual-level forecasts from the HFC benchmark condition.

## Prediction Sets List

> Request:

```shell
curl "https://control.gfc-staging.com/api/v1/prediction_sets" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Response:

```json
{
  "prediction_sets": [
    {
      "id": 50,
      "membership_id": 5,
      "question_id": 2,
      "discover_question_id": 20,
      "created_at": "2015-08-04T00:21:40.730Z",
      "updated_at": "2015-08-04T00:21:40.730Z",
      "comment_id": 123,
      "rationale": "7 -  Well, we have to end apartheid for one. And slow down the nuclear arms race, stop terrorism and world hunger. We have to provide food and shelter for the homeless, and oppose racial discrimination and promote civil rights, while also promoting equal rights for women.",
      "predictions": [
        {
          "id": 64,
          "type": null,
          "answer_id": 4,
          "membership_id": 5,
          "paid": null,
          "quantity": null,
          "forecasted_probability": "0.3333",
          "starting_probability": "0.3333",
          "final_probability": "0.3333",
          "filled_at": null,
          "created_at": "2015-08-04T00:21:40.733Z",
          "updated_at": "2015-08-04T00:21:40.733Z",
          "confidence_level": null,
          "made_after_correctness_known": false
        },
        {
          "id": 65,
          "type": null,
          "answer_id": 5,
          "membership_id": 5,
          "paid": null,
          "quantity": null,
          "forecasted_probability": "0.3333",
          "starting_probability": "0.3333",
          "final_probability": "0.3333",
          "filled_at": null,
          "created_at": "2015-08-04T00:21:40.741Z",
          "updated_at": "2015-08-04T00:21:40.741Z",
          "confidence_level": null,
          "made_after_correctness_known": false
        },
        {
          "id": 66,
          "type": null,
          "answer_id": 6,
          "membership_id": 5,
          "paid": null,
          "quantity": null,
          "forecasted_probability": "0.3333",
          "starting_probability": "0.3333",
          "final_probability": "0.3333",
          "filled_at": null,
          "created_at": "2015-08-04T00:21:40.754Z",
          "updated_at": "2015-08-04T00:21:40.754Z",
          "confidence_level": null,
          "made_after_correctness_known": false
        }
      ]
    }
  ]
}
```

### HTTP Request


`GET https://yoursite.gfc-staging.com/api/v1/control/prediction_sets`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 0 | Pagination page number
membership_id | none | Returns predictions for a single membership
question_id | none | Returns predictions for a single question
filter | none | Filters the question list. Possible values: `comments_with_links`, `comments_following`
created_before | none | Returns only prediction sets created before the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
created_after | none | Returns only prediction sets created after the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
updated_before | none | Returns only prediction sets updated before the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
updated_after | none | Returns only prediction sets updated after the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)


### Attribute Descriptions

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The id of the prediction set
membership_id | integer | The id of the membership that submitted the prediction set
question_id | integer | The id of the question that this prediction set belongs to
discover_question_id | integer | The discover question id of the question that this prediction set belongs to
rationale | string | The text of the rationale (if any) that the user submitted with the forecast
predictions.id | integer | The id of the prediction
predictions.answer_id | integer | The id of the answer this prediction belongs to
predictions.membership_id | integer | The id of the membership that submitted the prediction
predictions.filled_at | date | The timestamp of when the prediction was processed. This timestamp is used for scoring
predictions.made_after_correctness_known | boolean | Whether or not the prediction was submitted after the "correctness" of the answer was already known
predictions.forecasted_probability | float | The probability estimate that the user submitted with the forecast
predictions.starting_probability | float | The consensus probability of the answer prior to incorporating this forecast
predictions.final_probability | float | The consensus probability of the answer prior to incorporating this forecast
