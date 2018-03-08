
# Users

## Me

Each user can hit the "me" endpoint to get back information about him/herself and his/her memberships.

> Request:

```shell
curl "https://yoursite.cultivateforecasts.com/api/v1/me" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Response:

```json
{
  "id": 1,
  "email": "user@example.com",
  "created_at": "2016-03-22T19:09:18.251Z",
  "updated_at": "2016-03-22T19:09:23.610Z",
  "username": "superman",
  "first_name": "Clark",
  "last_name": "Kent",
  "facebook_url": "http://www.facebook.com/superman",
  "twitter_url": "http://www.twitter.com/superman",
  "linkedin_url": "http://www.linkedin.com/superman",
  "blog_url": "http://www.blog.com/superman",
  "last_prediction_at": "2016-03-22T19:09:23.609Z",
  "description": "He's a superhero",
  "interface_mode": "simple_interface",
  "memberships": [
    {
      "id": 1,
      "site_id": 1,
      "user_id": 1,
      "created_at": "2016-03-22T19:09:18.397Z",
      "updated_at": "2016-03-22T19:09:22.386Z",
      "level": 1,
      "avatar": "ident/default_avatars/level-1-1.png",
      "last_pageview_at": "2016-03-22T19:09:18.336Z",
      "featured": false,
      "role": "admin",
      "balance": 14900,
      "available_balance": 14900,
      "max_spend": 1490,
      "avatar_url": "http://home.fof.dev:3000/assets/ident/default_avatars/level-1-1-761e8eeca490d58a1f87dcba4f594064e92c579857cb9a4f8e71bf4427eff3d0.png",
      "site": {
        "id": 1,
        "subdomain": "home",
        "name": "Site Name",
        "created_at": "2016-03-22T19:09:18.325Z",
        "updated_at": "2016-03-22T19:09:18.325Z",
        "avatar_style": "uses_level_avatars",
        "custom_domain": null,
        "allows_top_level_comments": true,
        "hides_empty_rationales_from_feed": false,
        "allows_interface_toggling": true,
        "clinkle_leaderboard_disabled": false,
        "brier_leaderboard_disabled": false,
        "mandatory_rationales": false
      }
    }
  ]
}
```

### HTTP Request

`GET https://yoursite.cultivateforecasts.com/api/v1/me`

### Query Parameters

None.

## Creation

Use this endpoint to create new user accounts. Only certain users have permission to access this endpoint.

> Request:

```shell
curl -X "POST" "https://yoursite.cultivateforecasts.com/api/v1/users/" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75" \
  -H "Content-Type: application/json" \
  -H "Accept: application/json" \
  -d "{\"user\":{\"email\":\"slartibartfast@emaildomain.org\",\"username\":\"slartibartfast77\",\"password\":\"someamazingpassword\",\"first_name\":\"Slarti\",\"last_name\":\"bartfast\",\"description\":\"Indescribable\",\"interface_mode\":\"simple_interface\"}}"
```

> Request body example:

```json
{
  "user": {
    "email": "slartibartfast@emaildomain.org",
    "username": "slartibartfast77",
    "password": "slartibartfast77",
    "first_name": "Slarti",
    "last_name": "bartfast",
    "description": "Indescribable",
    "interface_mode": "simple_interface"
  }
}
```

### HTTP Request

`POST https://yoursite.cultivateforecasts.com/api/v1/users`


### User Parameters

Parameter | Required? | Description | Requirements
--------- | --------- | ----------- | ------------
email | Yes | The user's email address | Users must have unique email addresses
username | Yes | | Allowed characters: letters, numbers, hyphens and underscores
password | Yes | | Must be at least 8 characters long
first_name | No | |
last_name | No | |
description | No | |
interface_mode | No | Determines which forecasting interface the user will see on the website | Options are "simple_interface" and "advanced_interface". "simple_interface" is selected by default.