
# Memberships

## Memberships List

Each user has one account & user_id, but a user can be a member of multiple sites. A membership record associates a user to a site.

This endpoint is only accessible to site administrators.

> Request:

```shell
curl "https://yoursite.cultivateforecasts.com/api/v1/memberships" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Response:

```json
{
  "memberships": [
    {
      "id": 1,
      "site_id": 1,
      "user_id": 1,
      "balance": "10000.0",
      "created_at": "2015-08-04T00:21:34.623Z",
      "updated_at": "2015-08-04T00:21:34.651Z",
      "level": 1,
      "avatar": "ident/default_avatars/level-1-1.png",
      "role": "admin",
      "user": {
        "id": 1,
        "email": "user@example.com",
        "created_at": "2015-08-04T00:21:34.524Z",
        "updated_at": "2015-08-07T00:33:33.969Z",
        "username": "superman",
        "first_name": "Clark",
        "last_name": "Kent",
        "facebook_url": "www.facebook.com/superman",
        "twitter_url": "www.twitter.com/superman",
        "linkedin_url": "www.linkedin.com/superman",
        "blog_url": "www.blog.com/superman",
        "last_pageview_at": "2015-08-07T00:33:33.967Z",
        "last_prediction_at": null,
        "description": "He's a superhero"
      }
    },
    {
      "id": 2,
      "site_id": 1,
      "user_id": 2,
      "balance": "5298.92",
      "created_at": "2015-08-04T00:21:34.948Z",
      "updated_at": "2015-08-04T00:21:37.438Z",
      "level": 0,
      "avatar": "ident/default_avatars/level-0-1.png",
      "role": "user",
      "user": {
        "id": 2,
        "email": "user2@example.com",
        "created_at": "2015-08-04T00:21:34.924Z",
        "updated_at": "2015-08-04T00:21:34.924Z",
        "username": "superman2",
        "first_name": "Clark",
        "last_name": "Kent 2",
        "facebook_url": "www.facebook.com/superman2",
        "twitter_url": "www.twitter.com/superman2",
        "linkedin_url": "www.linkedin.com/superman2",
        "blog_url": "www.blog.com/superman2",
        "last_pageview_at": null,
        "last_prediction_at": null,
        "description": "He's a superhero2"
      }
    }
  ]
}
```

### HTTP Request

`GET https://yoursite.cultivateforecasts.com/api/v1/memberships`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 0 | Pagination page number
include_profile_question_responses | false | Passing "true" for this value will include profile questions and responses for each membership.
