
# Votes

## Votes List

Provides a list of upvotes & downvotes. Votes with a value of 1 are upvotes and votes with a value of -1 are downvotes.

This endpoint is only accessible to site administrators.

> Request:

```shell
curl "https://yoursite.gfc-staging.com/api/v1/votes" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Response:

```json
{
  "votes": [
    {
      "id": 1,
      "comment_id": 24,
      "ident_membership_id": 51,
      "value": 1,
      "created_at": "2015-11-09T17:14:13.229Z"
    },
    {
      "id": 2,
      "comment_id": 27,
      "ident_membership_id": 14,
      "value": -1,
      "created_at": "2015-11-09T19:22:41.984Z"
    }
  ]
}
```

### HTTP Request

`GET https://yoursite.gfc-staging.com/api/v1/votes`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 0 | Pagination page number
