
# Questions

## Questions List

> Request:

```shell
curl "https://yoursite.cultivateforecasts.com/api/v1/questions" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Response:

```json
{
  "questions": [
    {
      "id": 5,
      "name": "question-2",
      "type": "Forecast::Question",
      "site_id": 1,
      "membership_id": 1,
      "ends_at": "2015-09-15T00:21:35.906Z",
      "image": "MyString",
      "description": "question-desc-5",
      "published_at": null,
      "starts_at": null,
      "resolved_at": null,
      "predictions_count": 0,
      "comments_count": 0,
      "brier_score": "9.99",
      "created_at": "2015-08-04T00:21:35.910Z",
      "updated_at": "2015-08-04T00:21:35.910Z",
      "active?": true,
      "resolved?": false,
      "use_ordinal_scoring": false,
      "answers": [
        {
          "created_at": "2015-08-04T00:21:35.918Z",
          "description": "answer-desc-11",
          "ends_at": "2016-02-04T00:21:35.916Z",
          "id": 11,
          "membership_id": 1,
          "name": "answer-name-11",
          "outstanding": 0,
          "positions_count": null,
          "predictions_count": 0,
          "probability": "0.3333",
          "probability_formatted": "33.33%",
          "question_id": 5,
          "refunded_at": null,
          "refunded_by_id": null,
          "resolved_at": null,
          "resolved_by_id": null,
          "resolved_in_past_at": null,
          "status": null,
          "symbol": "A11",
          "type": null,
          "updated_at": "2015-08-04T00:21:35.918Z"
        },
        {
          "created_at": "2015-08-04T00:21:35.927Z",
          "description": "answer-desc-12",
          "ends_at": "2016-02-04T00:21:35.925Z",
          "id": 12,
          "membership_id": 1,
          "name": "answer-name-12",
          "outstanding": 0,
          "positions_count": null,
          "predictions_count": 0,
          "probability": "0.3333",
          "probability_formatted": "33.33%",
          "question_id": 5,
          "refunded_at": null,
          "refunded_by_id": null,
          "resolved_at": null,
          "resolved_by_id": null,
          "resolved_in_past_at": null,
          "status": null,
          "symbol": "A12",
          "type": null,
          "updated_at": "2015-08-04T00:21:35.927Z"
        },
        {
          "created_at": "2015-08-04T00:21:35.933Z",
          "description": "answer-desc-13",
          "ends_at": "2016-02-04T00:21:35.931Z",
          "id": 13,
          "membership_id": 1,
          "name": "answer-name-13",
          "outstanding": 0,
          "positions_count": null,
          "predictions_count": 0,
          "probability": "0.3333",
          "probability_formatted": "33.33%",
          "question_id": 5,
          "refunded_at": null,
          "refunded_by_id": null,
          "resolved_at": null,
          "resolved_by_id": null,
          "resolved_in_past_at": null,
          "status": null,
          "symbol": "A13",
          "type": null,
          "updated_at": "2015-08-04T00:21:35.933Z"
        }
      ]
    },
    {
      "id": 6,
      "name": "binary_question-2",
      "type": "Forecast::Binary::Question",
      "site_id": 1,
      "membership_id": 1,
      "ends_at": "2015-09-15T00:21:35.945Z",
      "image": "MyString",
      "description": "question-desc-6",
      "published_at": null,
      "starts_at": null,
      "resolved_at": null,
      "predictions_count": 0,
      "comments_count": 0,
      "brier_score": "9.99",
      "created_at": "2015-08-04T00:21:35.953Z",
      "updated_at": "2015-08-04T00:21:35.953Z",
      "active?": true,
      "resolved?": false,
      "use_ordinal_scoring": false,
      "answers": [
        {
          "created_at": "2015-08-04T00:21:35.965Z",
          "description": "answer-desc-14",
          "ends_at": "2016-02-04T00:21:35.962Z",
          "id": 14,
          "membership_id": 1,
          "name": "answer-name-14",
          "outstanding": 0,
          "positions_count": null,
          "predictions_count": 0,
          "probability": "0.5",
          "probability_formatted": "50.00%",
          "question_id": 6,
          "refunded_at": null,
          "refunded_by_id": null,
          "resolved_at": null,
          "resolved_by_id": null,
          "resolved_in_past_at": null,
          "status": null,
          "symbol": "A14",
          "type": "Forecast::Binary::Answer",
          "updated_at": "2015-08-04T00:21:35.965Z"
        }
      ]
    }
  ]
}
```

### HTTP Request

`GET https://yoursite.cultivateforecasts.com/api/v1/questions`

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

## Questions Creation and Updating

> HTTP Request:

`POST https://yoursite.cultivateforecasts.com/api/v1/questions`
`PATCH https://yoursite.cultivateforecasts.com/api/v1/questions/:id`

> Request body example:

```json
{
  "question": {
    "name": "How many tournaments will Tiger win this year?",
    "description": "This question includes only major tournaments"
    "ends_at": "2017-12-31T23:59:59-06:00"
    "type": "Forecast::PM::LMSR::ExclusiveMarket"
    "answers_attributes": [
      {
        "name": "0",
        "probability_whole_number": 47.5
      },
      {
        "name": "1-5",
        "probability_whole_number": 22.5
      },
      {
        "name": "6 or more",
        "probability_whole_number": 30
      }
    ]
  }
}
```


### Question Parameters

Parameter | Required? | Description
--------- | --------- | -----------
name | Yes | The name of the question
description | Yes | Background information, displays below the question name
links_attributes | No | An array of links to display below the question name. Valid parameters for links are listed below.
starts_at | No | The time at which the question begins accepting forecasts
ends_at | Yes | The time at which the question stops accepting forecasts
type | Yes | Valid question types are listed below -- note that some question types are disabled on some sites
intro | No | An introduction that appears before the question name. eg "Sponsor XYZ presents:"
use_ordinal_scoring | No | An optional scoring setting for questions with sequential answers
rolling_range_count | No | For rolling questions, the number of answers active at a given time
rolling_time_length | No | For rolling questions, the number of time units allotted to each answer (eg 2 for two weeks, 4 for four years)
rolling_time_unit | No | For rolling questions, the unit of time for each answer. Options: "day", "week", "month", "year"
roll_percentage | No | For rolling questions, the percentage of the probability assigned to the last bucket (eg 2020 or later) that will be transfered to the newly created bucket (2021 or later). The remainder will be assigned to the second last bucket (2020)
tag_list | No | An array containing the names of tags to be assigned to this question
challenge_ids | No | An array containing ids of challenges to be assigned to this question
answers_attributes | Yes | An array of answer objects that are part of this question. Valid parameters for answers are listed below.
suspended | No | If selected, the question is suspended and does not accept new forecasts

### Answer Parameters

Parameter | Required? | Description
--------- | --------- | -----------
name | Yes | The name of the answer
probability_whole_number | Yes | The starting probability of the answer
sort_order | No | The order in which this answer is displayed
id | No | The unique id of the answer--use only for updating
discover_answer_id | No | For questions created via Discover, the id of the Discover answer that corresponds to this answer
_destroy | No | Set to "true" to destroy this answer

### Link Parameters

Parameter | Description
--------- | -----------
id | The unique id of the link--use only for updating
url | The url address of this link
description | The text that displays for this link
_destroy | Set to "true" to destroy this link

### Question Types

Question Type | Description
------------- | -----------
"Forecast::Question" | A multi-answer prediction pool
"Forecast::Binary::Question" | A prediction pool with only one answer (eg Yes/No)
"Forecast::RollingQuestion" | A rolling prediction pool, with new answers appearing over time
"Forecast::PM::LMSR::ExclusiveMarket" | A multi-answer prediction market with one correct answer
"Forecast::PM::LMSR::NonExclusiveMarket" | A multi-answer prediction market that allows multiple correct answers
"Forecast::PM::LMSR::BinaryMarket" | A prediction market with only one answer
"Forecast::PM::LMSR::RollingMarket" | A rolling prediction market, with new answers appearing over time
