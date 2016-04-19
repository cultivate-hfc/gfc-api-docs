
# Earned Badges

## Earned Badge Creation

Creating an "earned badge" model is equivalent to awarding a badge to a given user.

Only administrators can access this API.

> Request:

```shell
curl -X "POST" "https://yoursite.cultivateforecasts.com/api/v1/earned_badges" \
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

`POST https://yoursite.cultivateforecasts.com/api/v1/earned_badges`


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
curl -X "DELETE" "https://yoursite.cultivateforecasts.com/api/v1/earned_badges/32" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75" \
  -H "Accept: application/json"
```

### HTTP Request

`DELETE https://yoursite.cultivateforecasts.com/api/v1/earned_badges/:id`


### Earned Badge Parameters

None
