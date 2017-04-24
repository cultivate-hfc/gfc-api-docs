
# Badges

## Badges List

Shows a list of badges that exist on the site.

> Request:

```shell
curl "https://yoursite.cultivateforecasts.com/api/v1/badges" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Response:

```json
{
  "badges": [
    {
      "id": 1,
      "site_id": 1,
      "name": "Badge name",
      "description": "A description of the badge",
      "image_url": "/uploads/social/badge/image/1/01.png",
      "created_at": "2016-04-18T17:20:51.886Z",
      "updated_at": "2016-04-19T14:39:14.977Z"
    },
    {
      "id": 2,
      "site_id": 1,
      "name": "badge2",
      "description": "another bdage",
      "image_url": "/uploads/social/badge/image/2/badge-image.JPG",
      "created_at": "2016-04-18T17:21:11.025Z",
      "updated_at": "2016-04-18T17:21:11.025Z"
    },
    {
      "id": 3,
      "site_id": 1,
      "name": "A third badge",
      "description": "Third badge description",
      "image_url": "/uploads/social/badge/image/3/badge3.jpg",
      "created_at": "2016-04-18T19:39:43.768Z",
      "updated_at": "2016-04-18T19:39:43.768Z"
    }
  ]
}
```

### HTTP Request

`GET https://yoursite.cultivateforecasts.com/api/v1/badges`

### Query Parameters

None.

### Attribute Descriptions

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The id of the badge
site_id | integer | The id of the site this badge belongs to
name | string | The name of the badge
description | string | The description of the badge
image_url | string | URL for the image associated with this badge
