
# Questions

## Questions List

> Request:

```shell
curl "https://api.gfc-staging.com/api/v1/questions" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Response:

```json
{
  "questions": [
    {
      "id": 5,
      "discover_question_id": 123,
      "name": "question-2",
      "type": "Forecast::Question",
      "ends_at": "2015-09-15T00:21:35.906Z",
      "description": "question-desc-5",
      "published_at": null,
      "starts_at": null,
      "resolved_at": null,
      "voided_at": null,
      "comments_count": 0,
      "created_at": "2015-08-04T00:21:35.910Z",
      "updated_at": "2015-08-04T00:21:35.910Z",
      "active?": true,
      "resolved?": false,
      "use_ordinal_scoring": false,
      "metadata": {
        "Topic": "Cyber attacks",
        "Domain": "Natural sciences/Climate",
        "Region": "North America",
        "Country - Primary": "USA",
        "Country - Secondary": "France",
        "IFP Generation Method": "Geopolitical Grab Bag"
      },
      "answers": [
        {
          "created_at": "2015-08-04T00:21:35.918Z",
          "ends_at": "2016-02-04T00:21:35.916Z",
          "id": 11,
          "discover_answer_id": 423,
          "name": "answer-name-11",
          "probability": "0.3333",
          "probability_formatted": "33.33%",
          "question_id": 5,
          "resolved_at": null,
          "resolved_by_id": null,
          "correctness_known_at": null,
          "type": null,
          "updated_at": "2015-08-04T00:21:35.918Z"
        },
        {
          "created_at": "2015-08-04T00:21:35.927Z",
          "ends_at": "2016-02-04T00:21:35.925Z",
          "id": 12,
          "discover_answer_id": 424,
          "name": "answer-name-12",
          "probability": "0.3333",
          "probability_formatted": "33.33%",
          "question_id": 5,
          "resolved_at": null,
          "resolved_by_id": null,
          "correctness_known_at": null,
          "type": null,
          "updated_at": "2015-08-04T00:21:35.927Z"
        },
        {
          "created_at": "2015-08-04T00:21:35.933Z",
          "ends_at": "2016-02-04T00:21:35.931Z",
          "id": 13,
          "discover_answer_id": 425,
          "name": "answer-name-13",
          "probability": "0.3333",
          "probability_formatted": "33.33%",
          "question_id": 5,
          "resolved_at": null,
          "resolved_by_id": null,
          "correctness_known_at": null,
          "type": null,
          "updated_at": "2015-08-04T00:21:35.933Z"
        }
      ],
      "clarifications":[{
        "id":4,
        "question_id":5,
        "content":"clarification-content-1",
        "created_at":"2018-01-15T21:45:32.495Z",
        "updated_at":"2018-01-15T21:45:32.495Z"
      }]
    },
    {
      "id": 6,
      "discover_question_id": 31,
      "name": "binary_question-2",
      "type": "Forecast::Binary::Question",
      "ends_at": "2015-09-15T00:21:35.945Z",
      "description": "question-desc-6",
      "published_at": null,
      "starts_at": null,
      "resolved_at": null,
      "voided_at": null,
      "comments_count": 0,
      "created_at": "2015-08-04T00:21:35.953Z",
      "updated_at": "2015-08-04T00:21:35.953Z",
      "active?": true,
      "resolved?": false,
      "use_ordinal_scoring": false,
      "metadata": {
        "Topic": "Cyber attacks",
        "Domain": "Natural sciences/Climate",
        "Region": "North America",
        "Country - Primary": "USA",
        "Country - Secondary": "France",
        "IFP Generation Method": "Geopolitical Grab Bag"
      },
      "answers": [
        {
          "created_at": "2015-08-04T00:21:35.965Z",
          "ends_at": "2016-02-04T00:21:35.962Z",
          "id": 14,
          "discover_answer_id": 429,
          "name": "answer-name-14",
          "probability": "0.5",
          "probability_formatted": "50.00%",
          "question_id": 6,
          "resolved_at": null,
          "resolved_by_id": null,
          "correctness_known_at": null,
          "type": "Forecast::Binary::Answer",
          "updated_at": "2015-08-04T00:21:35.965Z"
        }
      ]
    }
  ]
}
```

### HTTP Request

`GET https://api.gfc-staging.com/api/v1/questions`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 0 | Pagination page number
status | active | A question status filter to apply to the question list. Possible values: `active`, `closed`, `all`. By default, active questions are returned. To include all questions, you should pass `all` for this value.
sort | published_at | Sort order for the questions. Possible values: `published_at`, `ends_at`, `resolved_at`, `prediction_sets_count`
created_before | none | Returns only questions created before the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
created_after | none | Returns only questions created after the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
updated_before | none | Returns only questions updated before the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
updated_after | none | Returns only questions updated after the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)

### Question Attributes

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The [id of the question](#question-id-vs-discover-question-id)
discover_question_id | integer | The [id of the discover question](#question-id-vs-discover-question-id)  used to generate/publish this question, if collaborative question generation (Discover) is being used
name | string | The question content
type | string | The internal question type (e.g. prediction market, binary prediction market, opinion pool)
ends_at | datetime | The date & time that this question stops accepting forecasts
description | string | The description & background information for the question
published_at | datetime | The date & time that this question was published
starts_at | datetime | The date & time that this question started accepting forecasts
resolved_at | datetime | The date & time that this question was resolved
voided_at | datetime | The date & time that this question was voided. Blank if the question has not been voided. A voided question will not be resolved or scored.
predictions_count | integer | The number of predictions that have been made in this question
comments_count | integer | The number of comments that have been made in this question  
created_at | datetime | The date & time that this question was created
updated_at | datetime | The date & time that this question was last updated
active | boolean | Whether or not this question is currently active for forecasting
resolved | boolean | Whether or not this question has been resolved
use_ordinal_scoring | boolean | Whether or not this question uses ordinal scoring for calculating Brier scores
clarifications | array | An array of clarifications issued for the question. Used to clarify things like resolution criteria for the question.

### Answer Attributes

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The id of the answer
discover_answer_id | integer | The id of the discover answer used to generate/publish this question, if collaborative question generation (Discover) is being used
created_at | datetime | The date & time that this answer was created
updated_at | datetime | The date & time that this answer was last updated
ends_at | datetime | The date & time that this answer stops accepting forecasts
name | string | The answer content
probability | float | The current consensus probability for this answer
probability_formatted | string | The current consensus probability for this answer, formatted as a percentage
question_id | integer | The id of the question that this answer belongs to
resolved_at | datetime | The date & time that this answer was resolved
resolved_by_id | integer | The memebership_id of the membership who resolved this answer
correctness_known_at | datetime | The date & time that the correctness of this answer was known. If an administrator sets this value when resolving the answer, all forecasts made after it will be invalidated.
type | string | The internal answer type (e.g. prediction market stock, opinion pool answer)
