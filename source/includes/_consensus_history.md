# Consensus History

## Consensus History List

The Consensus History API provides a stream of aggregate forecasts derived from forecasts submitted in the HFC benchmark condition. Each time a user submits a forecast in the benchmark condition, the consensus forecasts for that question's answers are recalculated. This endpoint provides a historical record of each consensus forecast change.

Within HFC, the consensus is calculated using an aggregation algorithm called logit. The logit aggregation method is an extremizing method that uses a weighted geometric mean to aggregate forecasts. Forecaster weights are calculated based on 3 factors: historical accuracy, the frequency with which the forecaster updates his or her forecasts, and whether the forecaster completed a training course.

When using this API, you should always utilize the `created_after` parameter to pull only those records that have been created since you last accessed the API. **Do not attempt to pull** every record/page of the history.

Prior to question/answer resolution, the most recent (as determined by `consensus_at`) record can be considered the current consensus for that answer.

### Value vs. Normalized Value

Each record contains two value fields: `value` and `normalized_value`. The `value` field is the raw output from the aggregation algorithm, while the `normalized_value` is the `value` field normalized to ensure the answer options in a question sum to 100%.

### Decay & Weighting

Records contain parameters indicating decay and weighting settings that were used to calculate the consensus. Decay settings generally work by subsetting the individual-level forecasts that are fed to the aggregation algorithm. Weighting applies different weights to different forecasters when calculating the consensus (e.g. more accurate forecasters may have their opinions weighted more heavily).


> Request:

```shell
curl "https://api.gfc-staging.com/aggregation/api/v1/control/consensus_histories" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Response:

```json
{
  "consensus_histories": [
    {
      "id": 209,
      "answer_id": 120,
      "discover_answer_id": 66,
      "question_id": 50,
      "discover_question_id": 31,
      "prediction_set_id": 265,
      "consensus_at": "2018-01-26T01:34:39.261Z",
      "strategy": "Aggregation::Strategies::WeightedVoting",
      "decay_method": "Aggregation::Decay::NRecent",
      "decay_args": {
        "number": 10
      },
      "method_name": "21-WeightedVoting-NRecent",
      "weighting_settings": {
        "count_of_closed_questions_answered_requirement": 35,
        "percentage_of_closed_questions_answered_requirement": 0.5,
        "minimum_closed_questions_to_enable_accuracy_weighting": 10
      },
      "created_at": "2018-01-26T01:34:44.100Z",
      "updated_at": "2018-01-26T01:34:44.100Z",
      "value": 0.0,
      "normalized_value": 0.0
    },
    {
      "id": 208,
      "answer_id": 120,
      "discover_answer_id": 66,
      "question_id": 50,
      "discover_question_id": 31,
      "prediction_set_id": 265,
      "consensus_at": "2018-01-26T01:34:39.261Z",
      "strategy": "Aggregation::Strategies::L2e",
      "decay_method": "Aggregation::Decay::NRecent",
      "decay_args": {
        "number": 10
      },
      "method_name": "20-L2E",
      "weighting_settings": {
        "count_of_closed_questions_answered_requirement": 35,
        "percentage_of_closed_questions_answered_requirement": 0.5,
        "minimum_closed_questions_to_enable_accuracy_weighting": 10
      },
      "created_at": "2018-01-26T01:34:44.044Z",
      "updated_at": "2018-01-26T01:34:44.044Z",
      "value": 0.35,
      "normalized_value": 0.35
    }
  ]
}
```

### HTTP Request

`GET https://api.gfc-staging.com/aggregation/api/v1/control/consensus_histories`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 0 | Pagination page number
created_before | none | Returns only history records created before the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
created_after | none | Returns only history records created after the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
updated_before | none | Returns only history records updated before the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
updated_after | none | Returns only history records updated after the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)

### Response Attribute Descriptions

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The id of the consensus history record
answer_id | integer | The answer that this record pertains to
question_id | integer | The [question id](#question-id-vs-discover-question-id) that this record pertains to
discover_question_id | integer | The [discover question id](#question-id-vs-discover-question-id) that this record pertains to
discover_answer_id | integer | The [discover answer id](#question-id-vs-discover-question-id) that this record pertains to
prediction_set_id | integer | The prediction set that caused the consensus change
consensus_at | datetime | The time at which this was the consensus for the answer
strategy | string | The aggregation algorithm used to calculate the value
decay_method | string | The decay method, if any, used to decay forecasts included in the calculation
decay_args | integer | Parameters/configuration fed to the decay method, if any
created_at | datetime | The time at which this consensus history record was created
updated_at | datetime | The time at which this consensus history record was last updated
value | integer | The raw output value from the aggregation algorithm
normalized_value | integer | The `value` field normalized to ensure the answer options for the question sum to 1.0
