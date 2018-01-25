# Consensus History

## Consensus History List

The Consensus History API provides a stream of aggregate forecasts derived from forecasts submitted in the HFC benchmark condition. Each time a user submits a forecast in the benchmark condition, the consensus forecasts for that question's answers are recalculated. This endpoint provides a historical record of each consensus forecast change.

Within HFC, the consensus is calculated using 5 different aggregation algorithms: mean, median, voting, logit, and l2e. There are 25 variants of those 5 algorithms being calculated, so each time a forecast is submitted, 25 new consensus history records are created.

When using this API, you should always utilize the `created_after` parameter to pull only those records that have been created since you last accessed the API. **Do not attempt to pull** every record/page of the history.

Prior to question/answer resolution, the most recent (as determined by `consensus_at`) record can be considered the current consensus for that answer.

### Value vs. Normalized Value

Each record contains two value fields: `value` and `normalized_value`. The `value` field is the raw output from the aggregation algorithm, while the `normalized_value` is the `value` field normalized to ensure the answer options in a question sum to 100%.

### Decay & Weighting

A record may also contain parameters indicating decay and weighting settings that were used to calculate the consensus. Decay settings generally work by subsetting the individual-level forecasts that are fed to the aggregation algorithm. Weighting applies different weights to different forecasters when calculating the consensus (e.g. more accurate forecasters may have their opinions weighted more heavily).


> Request:

```shell
curl "https://control.cultivateforecasts.com/aggregation/api/v1/consensus_histories" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Response:

```json
{
  "consensus_histories": [
    {
      "id": 56,
      "answer_id": 8,
      "question_id": 24,
      "discover_question_id": 7,
      "discover_answer_id": 72,
      "prediction_set_id": 3,
      "consensus_at": "2017-08-09T14:38:00.770Z",
      "strategy": "Aggregation::Strategies::WeightedVoting",
      "decay_method": "Aggregation::Decay::PercentRecent",
      "decay_args": {
        "percent": 0.32
      },
      "created_at": "2017-08-11T14:38:01.370Z",
      "updated_at": "2017-08-11T14:38:01.370Z",
      "value": 0.3333,
      "normalized_value": 0.1111037
    },
    {
      "id": 55,
      "answer_id": 8,
      "question_id": 24,
      "discover_question_id": 7,
      "discover_answer_id": 72,
      "prediction_set_id": 3,
      "consensus_at": "2017-08-09T14:38:00.770Z",
      "strategy": "Aggregation::Strategies::WeightedMedian",
      "decay_method": "Aggregation::Decay::PercentRecent",
      "decay_args": {
        "percent": 0.684
      },
      "created_at": "2017-08-11T14:38:01.367Z",
      "updated_at": "2017-08-11T14:38:01.367Z",
      "value": 0.3333,
      "normalized_value": 0.1111037
    },
    {
      "id": 54,
      "answer_id": 8,
      "question_id": 24,
      "discover_question_id": 7,
      "discover_answer_id": 72,
      "prediction_set_id": 3,
      "consensus_at": "2017-08-09T14:38:00.770Z",
      "strategy": "Aggregation::Strategies::WeightedMean",
      "decay_method": "Aggregation::Decay::PercentRecent",
      "decay_args": {
        "percent": 0.684
      },
      "created_at": "2017-08-11T14:38:01.364Z",
      "updated_at": "2017-08-11T14:38:01.364Z",
      "value": 0.3333,
      "normalized_value": 0.1111037
    },
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

### Attribute Descriptions

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
