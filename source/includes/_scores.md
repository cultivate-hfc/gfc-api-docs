
# Scores

## Scores List

This API returns a list of score records for hybrid forecasting methods. There are four types of score records: `ComponentBrierScore`, `AnswerBrierScore`, `QuestionBrierScore`, `SiteBrierScore`.

Type | Description
---- | -----------
ComponentBrierScore | Represents the score for the forecasting method for a single day. That day is defined by the `period_started_at` and `period_ended_at` fields.
AnswerBrierScore | Represents the overall score for the forecasting method for a single answer.
QuestionBrierScore | Represents the overall score for the forecasting method for a single question.
SiteBrierScore | Represents the overall score across all questions for the forecasting method.


> Request:

```shell
curl "https://yoursite.hfc-staging.com/api/v1/audit_trail/scores" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Response:

```json
{
  "scores": [
    {
      "id": 907,
      "type": "Forecast::ComponentBrierScore",
      "value": "0.25",
      "scoreable_id": 567,
      "scoreable_type": "Forecast::Question",
      "period_started_at": "2018-04-10T00:00:00.000Z",
      "period_ended_at": "2018-04-10T23:59:59.999Z",
      "created_at": "2018-04-12T14:32:32.802Z",
      "updated_at": "2018-04-12T14:32:32.802Z",
      "ordinal_scoring_enabled": false,
      "forecasted_probability": "0.33",
      "forecast_type": "submitted",
      "discover_question_id": null,
      "prediction_made_by_method_name": "My-Aggregation-Method-1"
    },
    {
      "id": 909,
      "type": "Forecast::AnswerBrierScore",
      "value": "0.25",
      "scoreable_id": 206,
      "scoreable_type": "Forecast::Answer",
      "period_started_at": null,
      "period_ended_at": null,
      "created_at": "2018-04-03T14:32:32.984Z",
      "updated_at": "2018-04-12T13:32:34.405Z",
      "ordinal_scoring_enabled": false,
      "forecasted_probability": null,
      "forecast_type": null,
      "discover_answer_id": null,
      "prediction_made_by_method_name": "My-Aggregation-Method-1"
    },
    {
      "id": 912,
      "type": "Forecast::QuestionBrierScore",
      "value": "0.25",
      "scoreable_id": 572,
      "scoreable_type": "Forecast::Question",
      "period_started_at": null,
      "period_ended_at": null,
      "created_at": "2018-04-06T14:32:33.307Z",
      "updated_at": "2018-04-12T14:02:34.416Z",
      "ordinal_scoring_enabled": false,
      "forecasted_probability": null,
      "forecast_type": null,
      "discover_question_id": null,
      "prediction_made_by_method_name": "My-Aggregation-Method-1"
    },
    {
      "id": 917,
      "type": "Forecast::SiteBrierScore",
      "value": "0.25",
      "scoreable_id": 1401,
      "scoreable_type": "Ident::Site",
      "period_started_at": null,
      "period_ended_at": null,
      "created_at": "2018-04-12T13:32:33.844Z",
      "updated_at": "2018-04-12T14:32:33.897Z",
      "ordinal_scoring_enabled": false,
      "forecasted_probability": null,
      "forecast_type": null,
      "prediction_made_by_method_name": "My-Aggregation-Method-1"
    }
  ]
}
```

### HTTP Request

`GET https://yoursite.hfc-staging.com/api/v1/audit_trail/scores`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 0 | Pagination page number
score_type | none | Returns scores of a specific type. Possible values: `answer`, `question`, `site`
scoreable_id | none | Filters scores to include only scores for a single scoreable. This can be the id of an `answer`, `question`, or `site` record. If a value is passed for this parameter, the `score_type` record must also be set. So if you wanted scores for just a single question, you would pass `score_type=question&scoreable_id=123`
created_before | none | Returns only scores created before the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
created_after | none | Returns only scores created after the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
updated_before | none | Returns only scores updated before the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
updated_after | none | Returns only scores updated after the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)


### Attribute Descriptions

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The id of the score
type | string | The type of score
value | float | The actual score value
scoreable_id | integer | The id of the record receiving being scored. This can be an answer, question, or site. Combine with `scoreable_type` to determine the record being scored.
scoreable_type | string | The type of record being scored.
period_started_at | date | The start date of the time period being scored. Only applicable to `ComponentBrierScore`
period_ended_at | date | The end date of the time period being scored. Only applicable to `ComponentBrierScore`
ordinal_scoring_enabled | boolean | Ordinal scoring can be enabled for questions where certain answers are "closer" to being correct than others (e.g. when the answers are buckets of numbers). This flag indicates whether ordinal scoring was enabled for this score.
forecasted_probability | float | The method's forecast for this period/day. Only applicable to `ComponentBrierScore`
forecast_type | string | The manner in which this forecast was generated. Options are `submitted` (directly submitted by the method), `carryover` (forecast was carried over from a previous day), and `uniform_distribution` (equal distribution to given all answers since the method had not yet submitted any forecasts on the question/answer).
prediction_made_by_method_name | type | The method name of the forecasting method that generated this score.
