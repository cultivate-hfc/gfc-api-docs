---
title: Cultivate Forecasts API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>

includes:
- push_apis
- consensus_history
- external_prediction_sets
- prediction_sets
- questions

search: true
---


# Getting Started

You can register for your GFC API account at `https://www.iarpagfchallenge.com/users/sign_up`. Once you have registered, you can generate & view API tokens by going to `https://discover.iarpagfchallenge.com` and clicking on the "View API Token Management" button.

Upon signup, you will be assigned a domain for using the GFC API. Throughout the API documentation, you'll see URL's in the format of `https://yoursite.gfc-staging.com` You should replace `yoursite` with your assigned subdomain for all API calls. You can see your subdomain at `https://discover.iarpagfchallenge.com`.

## Environments

Cultivate Labs will be hosting two environments: a staging environment and a production environment. The staging environment should be used during development and testing of your system and the production environment should be used during live forecasting.

Environment | Domain
--------- | -----------
Staging | https://yoursite.gfc-staging.com
Production | https://yoursite.iarpagfchallenge.com

## Forecast Streams

The GFC team is providing a stream of [individual-level forecasts](#prediction-sets) and [aggregate "crowd" forecasts](#aggregate-predictions) that are derived from the HFC benchmark condition. The [individual-level forecast stream](#prediction-sets) contains  forecasts submitted by human participants, while the [aggregate forecast stream](#aggregate-predictions) contains a consensus forecast computed by aggregating those individual-level forecasts using to 5 different aggregation formulae: mean, median, voting, logit, and l2e.

## Question ID vs. Discover Question ID

Throughout the GFC API, you will encounter two types of ID's for questions: a question ID and a discover question ID.

Each GFC participant gets a unique question ID for each question. This is known as the question ID and is used as the question ID for submitting forecasts and can be found in the `id` field in the questions API.

Each question within GFC is also assigned a discover question ID. The purpose of this ID is to link questions across participants and forecast streams. For example, if you are looking at records from the Consensus History API, they will have a different question ID than your copy of the question, since they are generated in the benchmark condition. You can tie those records to questions by looking at the Consensus History record's discover question id and comparing it to the discover question id in the questions API.

## Authentication

Authentication is done via OAuth. To obtain an oauth token, you can visit `https://discover.iarpagfchallenge.com` and click on the "View API Token Management" button (make sure you are logged in first).

All requests to the various APIs should include your token as part of an authorization header. You can see an example curl request to the right.

```shell
curl "https://yoursite.gfc-staging.com/api/v1/me" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```
