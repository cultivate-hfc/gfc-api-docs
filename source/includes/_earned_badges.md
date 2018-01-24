
# Earned Badges

## Earned Badge Creation

Creating an "earned badge" model is equivalent to awarding a badge to a given user.

Only administrators can access this API.

> Request:

```shell
curl -X "POST" "https://api.gfc-staging.com/api/v1/earned_badges" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75" \
  -H "Content-Type: application/json" \
  -H "Accept: application/json" \
	-d "{\"earned_badge\":{\"badge_id\":5,\"membership_id\":23}}"
```

> Request body example:

```json
{
  "earned_badge": {
    "badge_id": 5,
    "membership_id": 23
  }
}
```


> Response:

The response contains the newly created earned badge.

```json
{
  "id": 5,
  "badge_id": 5,
  "membership_id": 23,
  "created_at": "2016-04-19T15:09:56.538Z",
  "updated_at": "2016-04-19T15:09:56.538Z",
  "featured": false
}
```

### HTTP Request

`POST https://api.gfc-staging.com/api/v1/earned_badges`


### Earned Badge Parameters

Parameter | Required? | Description
--------- | --------- | -----------
badge_id | Yes | Contains the ID of the badge to award to the membership.
membership_id | Yes | Contains the ID of the membership who should be awarded the badge.





## Earned Badge Deletion

Deleting an "earned badge" model is equivalent to removing a badge from a given user.

Only administrators can access this API.

> Request:

```shell
curl -X "DELETE" "https://api.gfc-staging.com/api/v1/earned_badges/32" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75" \
  -H "Accept: application/json"
```

### HTTP Request

`DELETE https://api.gfc-staging.com/api/v1/earned_badges/:id`


### Earned Badge Parameters

None



## Earned Badges List

This endpoint is only accessible to administrators.

> Request:

```shell
curl "https://api.gfc-staging.com/api/v1/earned_badges" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Response:

```json
{
  "earned_badges": [
    {
      "id": 101,
      "badge_id": 110,
      "membership_id": 2726,
      "created_at": "2016-05-02T16:01:34.951Z",
      "updated_at": "2016-05-02T16:01:34.951Z",
      "featured": false
    },
    {
      "id": 100,
      "badge_id": 109,
      "membership_id": 2724,
      "created_at": "2016-05-02T16:01:34.898Z",
      "updated_at": "2016-05-02T16:01:34.898Z",
      "featured": false
    }
  ]
}
```

### HTTP Request

`GET https://api.gfc-staging.com/api/v1/earned_badges`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 0 | Pagination page number

### Attribute Descriptions

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The id of the earned badge
badge_id | integer | The id of the badge that the user earned
featured | boolean | Users can opt to "feature" some of their badges on their profile. Featured badges are shown on the popover that is displayed when you hover over a user's username in the web interface.
