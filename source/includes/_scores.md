
# Scores

## Scores List

This API returns a list of score records. There are four types of score records: `AnswerBrierScore`, `QuestionBrierScore`, `ChallengeBrierScore`, and `SiteBrierScore`.

If a given record has a membership_id value, that indicates that it is a score for a specific membership. If the membership_id is null, that indicates that it represents the site-wide score. For example, a if a score with type `Forecast::QuestionBrierScore` has a null membership_id, that record is the site-wide consensus' score for that particular question.


> Request:

```shell
curl "https://yoursite.cultivateforecasts.com/api/v1/scores" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Response:

```json
{
  "scores": [
    {
      "id": 6207,
      "type": "Forecast::AnswerBrierScore",
      "value": "0.25",
      "scoreable_id": 4080,
      "scoreable_type": "Forecast::Answer",
      "membership_id": null,
      "period_started_at": null,
      "period_ended_at": null,
      "created_at": "2016-09-19T21:34:21.400Z",
      "updated_at": "2016-09-29T21:34:21.808Z",
      "ordinal_scoring_enabled": false,
      "use_price": false,
      "scoring_strategy_id": 484,
      "relative_brier_score": null,
      "median_brier_score_for_relative": null,
      "participation_rate": null,
      "prediction_made_by_id": null,
      "prediction_made_by_type": null
    },
    {
      "id": 6210,
      "type": "Forecast::QuestionBrierScore",
      "value": "0.25",
      "scoreable_id": 2554,
      "scoreable_type": "Forecast::Question",
      "membership_id": 8573,
      "period_started_at": null,
      "period_ended_at": null,
      "created_at": "2016-09-23T21:34:21.946Z",
      "updated_at": "2016-09-29T21:34:21.999Z",
      "ordinal_scoring_enabled": false,
      "use_price": false,
      "scoring_strategy_id": 484,
      "relative_brier_score": null,
      "median_brier_score_for_relative": null,
      "participation_rate": null,
      "prediction_made_by_id": null,
      "prediction_made_by_type": null
    },
    {
      "id": 6212,
      "type": "Forecast::ChallengeBrierScore",
      "value": "0.25",
      "scoreable_id": 406,
      "scoreable_type": "Forecast::Challenge",
      "membership_id": 8573,
      "period_started_at": null,
      "period_ended_at": null,
      "created_at": "2016-09-27T21:34:22.093Z",
      "updated_at": "2016-09-29T21:34:22.140Z",
      "ordinal_scoring_enabled": false,
      "use_price": false,
      "scoring_strategy_id": 484,
      "relative_brier_score": null,
      "median_brier_score_for_relative": null,
      "participation_rate": null,
      "prediction_made_by_id": null,
      "prediction_made_by_type": null
    },
    {
      "id": 6213,
      "type": "Forecast::SiteBrierScore",
      "value": "0.25",
      "scoreable_id": 5036,
      "scoreable_type": "Ident::Site",
      "membership_id": null,
      "period_started_at": null,
      "period_ended_at": null,
      "created_at": "2016-09-28T21:34:22.143Z",
      "updated_at": "2016-09-29T21:34:22.187Z",
      "ordinal_scoring_enabled": false,
      "use_price": false,
      "scoring_strategy_id": 484,
      "relative_brier_score": null,
      "median_brier_score_for_relative": null,
      "participation_rate": null,
      "prediction_made_by_id": null,
      "prediction_made_by_type": null
    }
  ]
}
```

### HTTP Request

`GET https://yoursite.cultivateforecasts.com/api/v1/scores`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 0 | Pagination page number
score_type | none | Returns scores of a specific type. Possible values: `answer`, `question`, `challenge`, `site`
with_membership_id | none | If the value of this parameter is `true`, only scores with a membership_id set will be returned
without_membership_id | none | If the value of this parameter is `true`, only scores without a membership_id set will be returned
scoreable_id | none | Filters scores to include only scores for a single scoreable. This can be the id of an `answer`, `question`, `challenge`, or `site` record. If a value is passed for this parameter, the `score_type` record must also be set. So if you wanted scores for just a single question, you would pass `score_type=question&scoreable_id=123`
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
scoreable_id | integer | The id of the record receiving the score. A "scoreable" is something that can receive a score in the system. This can be a membership, answer, question, challenge, or site. Combine with `scoreable_type` to determine the record receiving the score.
scoreable_type | string | The type of record receiving the score
period_started_at | date | The start date of the time period being scored
period_ended_at | date | The end date of the time period being scored
ordinal_scoring_enabled | boolean | Ordinal scoring can be enabled for questions where certain answers are "closer" to being correct than others (e.g. when the answers are buckets of numbers). This flag indicates whether ordinal scoring was enabled for this score.
use_price | boolean | A true value indicates that the stock price was used to generate this score (only applicable to prediction markets)
scoring_strategy_id | integer | A scoring strategy defines a set of settings used for scoring forecasts. This indicates the id of the strategy used to generate this score
relative_brier_score | float | The relative brier score
median_brier_score_for_relative | float | The median brier score for all forecasters in this answer+period combination, which is used to compute a relative brier score
participation_rate | float | The percentage of the days that the question ran in which the user was participating
prediction_made_by_id | integer | The id of the record that submitted the forecast that generated this score. Typically a membership, but can also be a team or an external predictor
prediction_made_by_type | type | The type of the record that submitted the forecast that generated this score.
