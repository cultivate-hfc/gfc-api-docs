
# Stars

## Stars List

If the user issuing a request to this endpoint is not an administrator, then a membership_id is required.

> Request:

```shell
curl "https://api.gfc-staging.com/api/v1/stars" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Response:

```json
{
  "stars": [
    {
      "id": 1,
      "membership_id": 1,
      "starrable_id": 6,
      "starrable_type": "Forecast::Question",
      "created_at": "2015-08-07T16:49:27.682Z",
      "updated_at": "2015-08-07T16:49:27.682Z"
    },
    {
      "id": 2,
      "membership_id": 1,
      "starrable_id": 5,
      "starrable_type": "Ident::Membership",
      "created_at": "2015-08-07T16:50:29.204Z",
      "updated_at": "2015-08-07T16:50:29.204Z"
    },
    {
      "id": 3,
      "membership_id": 1,
      "starrable_id": 1,
      "starrable_type": "Forecast::Challenge",
      "created_at": "2015-08-07T16:53:23.849Z",
      "updated_at": "2015-08-07T16:53:23.849Z"
    }
  ]
}
```

### HTTP Request

`GET https://api.gfc-staging.com/api/v1/stars`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 0 | Pagination page number
membership_id | none | Returns stars for a single membership id
filter | none | Filters the list of stars. Possible values: `following`, `followers`. To use a filter, a `membership_id` is required.
