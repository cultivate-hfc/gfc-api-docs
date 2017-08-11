---
title: Cultivate Forecasts API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>

includes:
- push_apis
- clarifications
- consensus_history
- external_predictions
- fundamental_activity_units
- memberships
- prediction_sets
- questions

search: true
---


# Getting Started

Each performer will be assigned a subdomain for use in HFC. Throughout the API documentation, you'll see URL's in the format of `https://yoursite.hfc-staging.com`. Once you have your subdomain, you should replace `yoursite` with your assigned subdomain. Contact Cultivate Labs at [techsupport@hybridforecasting.com](mailto:techsupport@hybridforecasting.com) to obtain your assigned subdomain.

# Environments

## Primary Environments

Cultivate Labs will be hosting two primary environments: a staging environment and a production environment. The staging environment should be used during development and testing of your system and the production environment should be used during live forecasting.

Environment | Domain
--------- | -----------
Staging | https://yoursite.hfc-staging.com
Production | https://yoursite.hybridforecasting.com

## T&E-furnished Data Stream Environments

In addition to these two primary environments, the T&E team is providing a stream of [individual-level forecasts](#prediction-sets) and [aggregate "crowd" forecasts](#aggregate-predictions) that are derived from two additional environments. During phase 1a, the data streams will be derived from an “HFC Challenge” hosted on the Good Judgment Open (GJO) platform. During phase 1b-4, the same streams will be derived from the benchmark condition The domain used for accessing both of these API’s will be dependent on which source is currently furnishing the data (and is different from the Performer-specific subdomain used for other API’s). During Phase 1a, https://www.gjopen.com should be used as the domain. During Phase 1b-4, https://control.hybridforecasting.com should be used.

Phase | Domain
--------- | -----------
Phase 1a | https://www.gjopen.com
Phase 1b-4 | https://control.hybridforecasting.com

# Authentication

Authentication in the Cultivate Forecasts API is done via OAuth. To obtain an oauth token, contact [techsupport@hybridforecasting.com](mailto:techsupport@hybridforecasting.com).

All requests to the various APIs should include your token as part of an authorization header. You can see an example curl request to the right.

```shell
curl "https://yoursite.hfc-staging.com/api/v1/me" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```
