
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
filter | active | A filter to apply to the question list. Possible values: `starred`, `closed`, `all`. By default, only active questions are returned. To include all questions, you should pass `all` for this value.
sort | published_at | Sort order for the questions. Possible values: `published_at`, `ends_at`
created_before | none | Returns only questions created before the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
created_after | none | Returns only questions created after the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
include_tag_ids | false | Passing "true" for this value will include an array of tag ids for the question.
include_challenge_ids | false | Passing "true" for this value will include an array of challenge ids for the question.
