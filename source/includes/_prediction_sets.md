
# Prediction Sets

The Prediction Sets API provides a stream of individual-level forecasts submitted by users in the HFC benchmark condition. Each prediction set will contain one prediction for each answer in the question.

If you want to connect all forecasts made by a given forecaster, you can do so using the `membership_guid`. This field is a masked ID that uniquely identifies a given forecaster. For example, if John Doe has a `membership_guid=cc4c30df5539f534690f0a36209738ce78a04180`, then all of John Doe's forecasts will contain that same value.

## Prediction Sets List

> Request:

```shell
curl "https://api.gfc-staging.com/api/v1/control/prediction_sets" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Response:

```json
{
  "prediction_sets": [
    {
      "id": 264,
      "type": "Forecast::OpinionPoolPredictionSet",
      "question_id": 10,
      "created_at": "2018-01-26T01:34:25.519Z",
      "updated_at": "2018-01-26T01:34:25.519Z",
      "membership_guid": "cc4c30df5539f534690f0a36209738ce78a04180",
      "question_name": "Will Kim Jong Un, Supreme Leader of North Korea, receive a haircut on 27 January 2018?",
      "discover_question_id": 30,
      "rationale": "no way",
      "comment_id": 2,
      "predictions": [
        {
          "id": 586,
          "type": "Forecast::Prediction",
          "answer_id": 20,
          "discover_answer_id": 65,
          "membership_guid": "cc4c30df5539f534690f0a36209738ce78a04180",
          "created_at": "2018-01-26T01:34:25.530Z",
          "updated_at": "2018-01-26T01:34:25.530Z",
          "made_after_correctness_known": false,
          "forecasted_probability": 0.05,
          "starting_probability": 0.5,
          "final_probability": 0.05,
          "answer_name": "Yes"
        }
      ]
    },
    {
      "id": 263,
      "type": "Forecast::OpinionPoolPredictionSet",
      "question_id": 15,
      "created_at": "2018-01-26T01:33:56.946Z",
      "updated_at": "2018-01-26T01:33:56.946Z",
      "membership_guid": "6fb38cdbc0340cc7dba954afaefc70b0869f91bb",
      "question_name": "How many total civilian deaths for January 2018 will the Syrian Network for Human Rights (SNHR) report?",
      "discover_question_id": 29,
      "rationale": "sounds right",
      "comment_id": 3,
      "predictions": [
        {
          "id": 583,
          "type": "Forecast::Prediction",
          "answer_id": 35,
          "discover_answer_id": 62,
          "membership_guid": "6fb38cdbc0340cc7dba954afaefc70b0869f91bb",
          "created_at": "2018-01-26T01:33:56.957Z",
          "updated_at": "2018-01-26T01:33:56.957Z",
          "made_after_correctness_known": false,
          "forecasted_probability": 0.25,
          "starting_probability": 0.3333,
          "final_probability": 0.25,
          "answer_name": "Less than 10"
        },
        {
          "id": 584,
          "type": "Forecast::Prediction",
          "answer_id": 34,
          "discover_answer_id": 63,
          "membership_guid": "6fb38cdbc0340cc7dba954afaefc70b0869f91bb",
          "created_at": "2018-01-26T01:33:56.962Z",
          "updated_at": "2018-01-26T01:33:56.962Z",
          "made_after_correctness_known": false,
          "forecasted_probability": 0.45,
          "starting_probability": 0.3333,
          "final_probability": 0.45,
          "answer_name": "Between 10 and 20, inclusive"
        },
        {
          "id": 585,
          "type": "Forecast::Prediction",
          "answer_id": 33,
          "discover_answer_id": 64,
          "membership_guid": "6fb38cdbc0340cc7dba954afaefc70b0869f91bb",
          "created_at": "2018-01-26T01:33:56.967Z",
          "updated_at": "2018-01-26T01:33:56.967Z",
          "made_after_correctness_known": false,
          "forecasted_probability": 0.3,
          "starting_probability": 0.3333,
          "final_probability": 0.3,
          "answer_name": "More than 20"
        }
      ]
    }
  ]
}
```

### HTTP Request


`GET https://api.gfc-staging.com/api/v1/control/prediction_sets`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 0 | Pagination page number
question_id | none | Returns predictions for a single question
created_before | none | Returns only prediction sets created before the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
created_after | none | Returns only prediction sets created after the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
updated_before | none | Returns only prediction sets updated before the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
updated_after | none | Returns only prediction sets updated after the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)


### Attribute Descriptions

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The id of the prediction set
membership_guid | string | A masked ID that uniquely identifies the user who made the forecast
question_id | integer | The id of the question that this prediction set belongs to
discover_question_id | integer | The [discover question id](#question-id-vs-discover-question-id) of the question that this prediction set belongs to
rationale | string | The text of the rationale (if any) that the user submitted with the forecast
predictions.id | integer | The id of the prediction
predictions.answer_id | integer | The id of the answer this prediction belongs to
predictions.made_after_correctness_known | boolean | Whether or not the prediction was submitted after the "correctness" of the answer was already known
predictions.forecasted_probability | float | The probability estimate that the user submitted with the forecast
predictions.starting_probability | float | The consensus probability of the answer prior to incorporating this forecast
predictions.final_probability | float | The consensus probability of the answer prior to incorporating this forecast
