
# External Predictions

## External Predictions Creation

This API is for submitting forecasts generated outside of Cultivate Forecasts, which will then be scored when the question/answer resolves.

Each submission is known as an `ExternalPredictionSet` and each prediction set contains 1 or more predictions. If a question has 3 possible answers, then a prediction set for that question should contain 3 predictions. If a question is a binary question (ie. a Yes/No question), then the prediction set should have a single prediction (and the opposing value is automatically calculated). Other than binary questions, all predictions in a prediction set should sum to 1.0 (ie. in a 3-option question, answer a: 0.2, answer b: 0.3, answer c: 0.5).

Each prediction set should also contain information about the method used to generate it. Each method is tracked by the platform with a model known as an `ExternalPredictor`. You must embed the name of your external predictor within the forecast submission, via the `external_predictor_attributes.method_name` attribute.

Submissions should also contain a `metadata` field. This string should contain JSON-formatted information about how the forecast was generated and any associated parameters that were used to generate it.

Only administrators can access this API.

> Request:

```shell
curl -X "POST" "https://yoursite.cultivateforecasts.com/api/v1/external_prediction_sets" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75" \
  -H "Content-Type: application/json" \
  -H "Accept: application/json" \
	-d "{\"external_prediction_set\":{\"question_id\":123,\"metadata\":\"{'foo': 'bar', 'count': 2}\",\"external_predictor_attributes\":{\"method_name\":\"red\"},\"external_predictions_attributes\":[{\"value\":0.65,\"answer_id\":431},{\"value\":0.34,\"answer_id\":432}]}}"
```

> Request body example:

```json
{
  "external_prediction_set": {
    "question_id": 123,
    "metadata": "{'foo': 'bar', 'count': 2}",
    "external_predictor_attributes": {
      "method_name": "red"
    },
    "external_predictions_attributes": [
      {
        "value": 0.65,
        "answer_id": 431
      },
      {
        "value": 0.35,
        "answer_id": 432
      }
    ]
  }
}
```


> Response:

```json
{
  "id": 1,
  "question_id": 123,
  "site_id": 2,
  "membership_id": 3,
  "method_name": "red",
  "created_at": "2017-06-15T21:07:04.092Z",
  "updated_at": "2017-06-15T21:07:04.092Z",
  "forecast_at": "2017-06-15T21:07:04Z",
  "external_predictions": [
    {
      "id": 1,
      "question_id": 1,
      "answer_id": 431,
      "site_id": 2,
      "membership_id": 3,
      "method_name": "red",
      "created_at": "2017-06-15T21:07:04.113Z",
      "updated_at": "2017-06-15T21:07:04.113Z",
      "value": 0.65,
      "forecast_at": "2017-06-15T21:07:04Z"
    },
    {
      "id": 2,
      "question_id": 1,
      "answer_id": 432,
      "site_id": 2,
      "membership_id": 3,
      "method_name": "red",
      "created_at": "2017-06-15T21:07:04.126Z",
      "updated_at": "2017-06-15T21:07:04.126Z",
      "value": 0.35,
      "forecast_at": "2017-06-15T21:07:04Z"
    }
  ]
}
```

### HTTP Request

`POST https://yoursite.cultivateforecasts.com/api/v1/external_predictions`


### External Prediction Set Parameters

Parameter | Required? | Description
--------- | --------- | -----------
question_id | Yes | The question id associated with this forecast
metadata | Yes | A JSON-formatted string containing metadata describing how this forecast was generated.
external_predictor_attributes.method_name | Yes | A string identifying the method you're using to generate this forecast. Can be any string.
external_predictions_attributes | Yes | An array of external prediction objects that are part of this prediction set. Valid parameters for external predictions are listed below.


### External Prediction Parameters

Parameter | Required? | Description
--------- | --------- | -----------
answer_id | Yes | The answer id associated with this forecast
external_predictions_attributes.value | Yes | Contains the value of the forecast. Must be a number between 1 and 0.


### External Prediction Set Response Attribute Descriptions

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The id of the external prediction
question_id | integer | The question id associated with this forecast
answer_id | integer | The answer id associated with this forecast
method_name | string | The name of the `External Predictor` method used to generate the forecast
forecast_at | date | The auto-generated timestamp of when this forecast was submitted. This timestamp is used for scoring forecasts.
site_id | string | The site id associated with this forecast
membership_id | string | The id of the membership that submitted this forecast
external_predictions | array | An array of external prediction objects, which are described below


### External Prediction Response Attribute Descriptions

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The id of the external prediction
question_id | integer | The question id associated with this forecast
answer_id | integer | The answer id associated with this forecast
method_name | string | The name of the `External Predictor` method used to generate the forecast
forecast_at | date | The auto-generated timestamp of when this forecast was submitted. This timestamp is used for scoring forecasts.
site_id | string | The site id associated with this forecast
membership_id | string | The id of the membership that submitted this forecast
value | float | Contains the forecasted probability
