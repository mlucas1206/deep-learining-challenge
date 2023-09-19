## Overview
The purpose of this analysis is to accurately predict if Alphabet Soup will fund a specific application.

## Results
### Data Preprocessing
I created 3 different frameworks for the machine learning process. See table below to see the details of each model created. After the initial model, I used `RandomForestClassifier` to determine the weight or significance of each feature to the target. With that data, I remove more features from the training model.

|File/Model|Target|Features|Removed|
|---|---|---|---|
|Initial|IS_SUCCESSFUL|APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, STATUS, INCOME_AMT, SPECIAL_CONSIDERATIONS, ASK_AMT | EIN, NAME|
|Optimization|IS_SUCCESSFUL|APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, ORGANIZATION, ASK_AMT | EIN, NAME, STATUS, USE_CASE, SPECIAL_CONSIDERATION, INCOME_AMT|
|Optimization 2|IS_SUCCESSFUL|APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, INCOME_AMT, ASK_AMT | EIN, NAME, STATUS, SPECIAL_CONSIDERATIONS|

### Compiling, Training, and Evaluating the Model

|File/Model|Layers(neurons)|input_features|Epoch|Batch Size|Model Accuracy
|---|---|---|---|---|---|
|Initial|First(80), Second(30), Output(1)|43|100|32|0.7284
|Optimization|First(50), Second(50), Third(50), Output(1)|26|1000|32|0.7291
|Optimization 2|First(60), Second(50), Third(50), Fourth(30), Output(1)|40|300|20|0.7272

All hidden layers use `relu` while the output layer uses the `sigmoid`. I was not able to get the target performance and all 3 attempt gave an accuracy of under 73% and loss of at least 55%. To get different results, I adjusted many things, I added layers, adjusted neuron count, changed batch sizes, and even tried setting epoch count to 1000 to see if it will make a big change.

### Summary:
Based on the Loss and and accuracy results. Data is considered overfit. After surfing the web. a better model for overfitted data is using Gradient Boosting Models (GBM) like XGBoost. That would be a good recommendation for the next attempts with the data.