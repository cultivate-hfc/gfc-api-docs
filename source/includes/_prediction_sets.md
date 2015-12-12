
# Prediction Sets

## Prediction Sets List

> Request:

```shell
curl "https://yoursite.cultivateforecasts.com/api/v1/prediction_sets" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Response:

```json
{
  "prediction_sets": [
    {
      "id": 1,
      "membership_id": 2,
      "question_id": 1,
      "created_at": "2015-08-04T00:21:37.141Z",
      "updated_at": "2015-08-04T00:21:37.141Z",
      "comment_id": 123,
      "rationale": "0 - http://www.flyoverworks.com I live in the American Gardens Building on W. 81st Street on the 11th floor. My name is Patrick Bateman. I'm 27 years old. I believe in taking care of myself and a balanced diet and rigorous exercise routine. In the morning if my face is a little puffy I'll put on an ice pack while doing stomach crunches.",
      "predictions": [
        {
          "id": 1,
          "type": "Forecast::PM::LMSR::Trade",
          "answer_id": 1,
          "membership_id": 2,
          "paid": "2517.6",
          "quantity": 69,
          "forecasted_probability": "0.5",
          "starting_probability": "0.3333",
          "final_probability": "0.5",
          "filled_at": null,
          "refunded_at": null,
          "created_at": "2015-08-04T00:21:36.913Z",
          "updated_at": "2015-08-04T00:21:37.147Z",
          "confidence_level": "confidence_medium",
          "made_after_correctness_known": false
        }
      ]
    },
    {
      "id": 50,
      "membership_id": 5,
      "question_id": 2,
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
          "refunded_at": null,
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
          "refunded_at": null,
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
          "refunded_at": null,
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

`GET https://yoursite.cultivateforecasts.com/api/v1/prediction_sets`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 0 | Pagination page number
membership_id | none | Returns predictions for a single membership id
question_id | none | Returns predictions for a single membership id
filter | none | Filters the question list. Possible values: `comments_with_links`, `comments_following`
created_before | none | Returns only prediction sets created before the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
created_after | none | Returns only prediction sets created after the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
