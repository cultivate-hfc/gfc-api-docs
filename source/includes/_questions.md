
# Questions

## Questions List

> Request:

```shell
curl "https://yoursite.hfc-staging.com/api/v1/questions" \
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
      "site_id": 1,
      "membership_id": 1,
      "ends_at": "2015-09-15T00:21:35.906Z",
      "description": "question-desc-5",
      "published_at": null,
      "starts_at": null,
      "resolved_at": null,
      "predictions_count": 0,
      "comments_count": 0,
      "created_at": "2015-08-04T00:21:35.910Z",
      "updated_at": "2015-08-04T00:21:35.910Z",
      "active?": true,
      "resolved?": false,
      "use_ordinal_scoring": false,
      "answers": [
        {
          "created_at": "2015-08-04T00:21:35.918Z",
          "ends_at": "2016-02-04T00:21:35.916Z",
          "id": 11,
          "discover_answer_id": 423,
          "membership_id": 1,
          "name": "answer-name-11",
          "positions_count": null,
          "predictions_count": 0,
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
          "membership_id": 1,
          "name": "answer-name-12",
          "positions_count": null,
          "predictions_count": 0,
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
          "membership_id": 1,
          "name": "answer-name-13",
          "positions_count": null,
          "predictions_count": 0,
          "probability": "0.3333",
          "probability_formatted": "33.33%",
          "question_id": 5,
          "resolved_at": null,
          "resolved_by_id": null,
          "correctness_known_at": null,
          "type": null,
          "updated_at": "2015-08-04T00:21:35.933Z"
        }
      ]
    },
    {
      "id": 6,
      "discover_question_id": 31,
      "name": "binary_question-2",
      "type": "Forecast::Binary::Question",
      "site_id": 1,
      "membership_id": 1,
      "ends_at": "2015-09-15T00:21:35.945Z",
      "description": "question-desc-6",
      "published_at": null,
      "starts_at": null,
      "resolved_at": null,
      "predictions_count": 0,
      "comments_count": 0,
      "created_at": "2015-08-04T00:21:35.953Z",
      "updated_at": "2015-08-04T00:21:35.953Z",
      "active?": true,
      "resolved?": false,
      "use_ordinal_scoring": false,
      "answers": [
        {
          "created_at": "2015-08-04T00:21:35.965Z",
          "ends_at": "2016-02-04T00:21:35.962Z",
          "id": 14,
          "discover_answer_id": 429,
          "membership_id": 1,
          "name": "answer-name-14",
          "positions_count": null,
          "predictions_count": 0,
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

`GET https://yoursite.hfc-staging.com/api/v1/questions`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 0 | Pagination page number
tags | none | A comma separated list of tags to filter by (e.g. "sports,politics,tech")
challenges | none | A comma separated list of challenge ids to filter by (e.g. "1,5,8"). Will return only questions in those challenges. Operates as a logical AND (ie. if you pass "1,5", it will return only questions that are in both challenges)
filter | none | A filter to apply to the question list. Possible values: `starred`, `featured`. By default, no filter is applied.
status | active | A question status filter to apply to the question list. Possible values: `closed`, `all`. If this value is omitted, only active questions are returned. To include all questions, you should pass `all` for this value.
sort | published_at | Sort order for the questions. Possible values: `published_at`, `ends_at`, `resolved_at`, `prediction_sets_count`
created_before | none | Returns only questions created before the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
created_after | none | Returns only questions created after the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
include_tag_ids | false | Passing "true" for this value will include an array of tag ids for the question.
include_challenge_ids | false | Passing "true" for this value will include an array of challenge ids for the question.

### Question Attributes

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The id of the question
discover_question_id | integer | The id of the discover question used to generate/publish this question, if collaborative question generation (Discover) is being used
name | string | The question content
type | string | The internal question type (e.g. prediction market, binary prediction market, opinion pool)
site_id | integer | The id of the site that this question belongs to
membership_id | integer | The id of the membership who created this question
ends_at | datetime | The date & time that this question stops accepting forecasts
description | string | The description & background information for the question
published_at | datetime | The date & time that this question was published
starts_at | datetime | The date & time that this question started accepting forecasts
resolved_at | datetime | The date & time that this question was resolved
predictions_count | integer | The number of predictions that have been made in this question
comments_count | integer | The number of comments that have been made in this question  
created_at | datetime | The date & time that this question was created
updated_at | datetime | The date & time that this question was last updated
active | boolean | Whether or not this question is currently active for forecasting
resolved | boolean | Whether or not this question has been resolved
use_ordinal_scoring | boolean | Whether or not this question uses ordinal scoring for calculating Brier scores

### Answer Attributes

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The id of the answer
discover_answer_id | integer | The id of the discover answer used to generate/publish this question, if collaborative question generation (Discover) is being used
created_at | datetime | The date & time that this answer was created
updated_at | datetime | The date & time that this answer was last updated
ends_at | datetime | The date & time that this answer stops accepting forecasts
membership_id | integer | The id of the membership who created this answer
name | string | The answer content
positions_count | integer | The number of positions forecasters have taken in this answer
predictions_count | integer | The number of predictions forecasters have made in this answer
probability | float | The current consensus probability for this answer
probability_formatted | string | The current consensus probability for this answer, formatted as a percentage
question_id | integer | The id of the question that this answer belongs to
resolved_at | datetime | The date & time that this answer was resolved
resolved_by_id | integer | The memebership_id of the membership who resolved this answer
correctness_known_at | datetime | The date & time that the correctness of this answer was known. If an administrator sets this value when resolving the answer, all forecasts made after it will be invalidated.
type | string | The internal answer type (e.g. prediction market stock, opinion pool answer)
