# Question Aggregate Predictions

## Questions Index

Provides predictions answers calculated using different aggregation methods

> Request:

```shell
curl "https://yoursite.cultivateforecasts.com/aggregation/api/v1/questions" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Response:

```json
{
  "questions": [
    {
      "id": 40,
      "name": "question-name-1",
      "answers": [
        {
          "id": 120,
          "name": "answer-name-3",
          "strategies": [
            {
              "method": "Mean",
              "value": "0.4"
            },
            {
              "method": "WeightedMean",
              "value": "0.4"
            },
            {
              "method": "Median",
              "value": "0.2"
            },
            {
              "method": "WeightedMedian",
              "value": "0.2"
            },
            {
              "method": "Voting",
              "value": "0.333333"
            },
            {
              "method": "WeightedVoting",
              "value": 0.333333
            },
            {
              "method": "Logit",
              "value": "1.040042"
            },
            {
              "method": "L2e",
              "value": 0.801018
            }
          ]
        },
        {
          "id": 119,
          "name": "answer-name-2",
          "strategies": [
            {
              "method": "Mean",
              "value": "0.333333"
            },
            {
              "method": "WeightedMean",
              "value": "0.333333"
            },
            {
              "method": "Median",
              "value": "0.2"
            },
            {
              "method": "WeightedMedian",
              "value": "0.2"
            },
            {
              "method": "Voting",
              "value": "0.333333"
            },
            {
              "method": "WeightedVoting",
              "value": 0.333333},
            {
              "method": "Logit",
              "value": "0.956466"
            },
            {
              "method": "L2e",
              "value": 0.633632
            }
          ]
        },
        {
          "id": 118,
          "name": "answer-name-1",
          "strategies": [
            {
              "method": "Mean",
              "value": "0.366667"
            },
            {
              "method": "WeightedMean",
              "value": "0.366667"
            },
            {
              "method": "Median",
              "value": "0.2"},
            {
              "method": "WeightedMedian",
              "value": "0.2"},
            {
              "method": "Voting",
              "value": "0.333333"},
            {
              "method": "WeightedVoting",
              "value": 0.333333},
            {
              "method": "Logit",
              "value": "1.0"},
            {
              "method": "L2e",
              "value": 0.717251
            }
          ]
        }
      ]
    }
  ]
}
```

### HTTP Request

`GET https://yoursite.cultivateforecasts.com/aggregation/api/v1/questions`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 0 | Pagination page number

