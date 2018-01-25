## Push APIs

The challenge platform provides push-based APIs for [question](#questions) creation, update, resolution, and [clarification](#clarifications).

For each of these APIs, the platform will make an HTTP POST request to a URL that you specify. The body of the request will contain JSON matching that from the API documentation for each of those models (e.g. a question creation post-hook will contain the question JSON shown [here](#questions)).

To set up a post-hook for any of these APIs, visit:

Environment | URL
--------- | -----------
Staging | [https://api.gfc-staging.com/api_management/api_post_hooks](https://api.gfc-staging.com/api_management/api_post_hooks)
Production | [https://api.iarpagfchallenge.com/api_management/api_post_hooks](https://api.iarpagfchallenge.com/api_management/api_post_hooks)
