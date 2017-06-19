
# Memberships

## Memberships List

Each user in Cultivate Forecasts has a single user record & user_id. However, a user can be a member of multiple sites. A membership record associates a user to a site. This endpoint provides a list of membership records for a given site and embeds the user record within each membership.

This endpoint is only accessible to site administrators.

> Request:

```shell
curl "https://yoursite.cultivateforecasts.com/api/v1/memberships" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
created_before | none | Returns only memberships created before the passed time. Time should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
created_after | none | Returns only memberships created after the passed time. Time should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)

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


### Attribute Descriptions

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The id of the membership
site_id | integer | The id of the site that this membership belongs to
user_id | integer | The id of the user that this membership belongs to
balance | float | The prediction market currency balance of the membership
level | integer | The user's level. Only applicable in sites that use the user leveling system.
avatar_url | string | A URL containing an avatar image for the user
role | string | The role/privileges of the membership. Can be "user" or "admin"
user.id | integer | The id of the user
user.email | string | The email of the user
user.username | string | The username of the user
user.first_name | string | The first name of the user
user.last_name | string | The last name of the user
user.facebook_url | string | The url of the facebook profile of the user
user.twitter_url | string | The url of the twitter profile of the user
user.linkedin_url | string | The url of the linkedin profile of the user
user.blog_url | string | The url of the blog of the user
user.last_pageview_at | date | The timestamp of the user's last pageview
user.last_prediction_at | date | The timestamp of the user's last forecast
user.description | string | The user's self-inputted description
