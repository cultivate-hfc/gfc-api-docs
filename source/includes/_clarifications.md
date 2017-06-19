
# Clarifications

## Clarifications List

This API returns a list of question clarifications. These are used to officially clarify questions about a question and its resolution criteria.


> Request:

```shell
curl "https://yoursite.hfc-staging.com/api/v1/clarifications" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Response:

```json
{
  "clarifications": [
    {
      "id": 27,
      "question_id": 17,
      "content": "clarification-content-2",
      "created_at": "2016-11-20T22:22:52.724Z",
      "updated_at": "2016-11-27T22:22:52.734Z"
    },
    {
      "id": 28,
      "question_id": 17,
      "content": "clarification-content-3",
      "created_at": "2016-11-26T22:22:52.736Z",
      "updated_at": "2016-11-27T22:22:52.744Z"
    }
  ]
}
```

### HTTP Request

`GET https://yoursite.hfc-staging.com/api/v1/clarifications`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 0 | Pagination page number

### Attribute Descriptions

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The id of the clarification
question_id | integer | The id of the question that is being clarified
content | string | The actual text of the clarification
