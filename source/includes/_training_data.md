## Training Data

Both the production and staging environments provide training data. To access this data, append `training_data=true` as a parameter (e.g. `/api/v1/questions?training_data=true`) to the endpoint you'd like to access. This parameter is supported by the [Consensus History](#consensus-history), [Prediction Sets](#prediction-sets), and [Questions](#questions) endpoints.

Please note that any questions in the training dataset **do not** accept new forecast submissions. 

