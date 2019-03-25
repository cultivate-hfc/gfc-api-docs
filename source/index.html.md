---
title: Cultivate Forecasts API Reference

language_tabs:
  - shell

includes:
- training_data
- pagination
- consensus_history
- external_prediction_sets
- prediction_sets
- questions

search: true
---

# Getting Started

## Environments

[Cultivate Labs](https://www.cultivatelabs.com/) will be hosting two environments for the GFC: a staging environment and a production environment. The staging environment should be used during development and testing of your system and the production environment should be used during live forecasting.

Note that you will need to register for accounts and generate/use separate oauth tokens for each environment.

Environment | Domain
--------- | -----------
Staging | https://api.gfc-staging.com
Production | https://api.iarpagfchallenge.com


## Registration

You can register for your GFC API account at:

Environment | URL
--------- | -----------
Staging | [https://www.gfc-staging.com/users/sign_up](https://www.gfc-staging.com/users/sign_up)
Production | [https://www.iarpagfchallenge.com/users/sign_up](https://www.iarpagfchallenge.com/users/sign_up)


Once you have registered, you can generate & view API tokens by going to:

Environment | URL
--------- | -----------
Staging | [https://api.gfc-staging.com/api_management/oauth_tokens](https://api.gfc-staging.com/api_management/oauth_tokens)
Production | [https://api.iarpagfchallenge.com/api_management/oauth_tokens](https://api.iarpagfchallenge.com/api_management/oauth_tokens)



## Forecast Streams

The GFC team is providing a stream of [individual-level forecasts](#prediction-sets) and [aggregate "crowd" forecasts](#consensus-history) that are derived from the HFC benchmark condition. The [individual-level forecast stream](#prediction-sets) contains forecasts submitted by human participants, while the [aggregate forecast stream](#consensus-history) contains a consensus forecast computed by aggregating those individual-level forecasts.


## Authentication

Authentication is done via OAuth. To obtain an oauth token, you can visit [https://api.iarpagfchallenge.com/api_management/oauth_tokens](https://api.iarpagfchallenge.com/api_management/oauth_tokens) (make sure you are logged in first).

All requests to the various APIs should include your token as part of an authorization header. You can see an example curl request to the right (**you will need to replace the oauth token with your token**).

```shell
curl "https://api.gfc-staging.com/api/v1/questions" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```
