# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### NAME - MOHD KAIF

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
-Round negative count values to zero 
-Round the numbers in count column to zero

### What was the top ranked model that performed?
WeightedEnsemble_L2 with hyper parameter optimized

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
-Time series analysis shows that:
    - There are data missing for last 10 days of the month. i.e; from 20th.
    - The changes in the demand of every hour during weekday and weekend.
-Correlation graph showed the high correlation between month and seasonality. So, removed seasonality from features.

### How much better did your model preform after adding additional features and why do you think that is?
Very slight improvement after adding additional features.

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
The addition of additional features `improved model performance by approximately 238%` in comparison to the initial/raw model (without EDA and/or feature engineering) performance.
Moreover, splitting the `datetime` feature into multiple independent features such as `year`, `month`, `day` and `hour` along with the addition of `day_type`, further improved the model performance because these predictor variables `aid the model assess seasonality or historical patterns in the data` more effectively. 


### If you were given more time with this dataset, where do you think you would spend more time?
Hyperparameter tuning was beneficial because it enhanced the model's performance compared to the initial submission. Three different configurations were used while performing hyperparameter optimization experiments. Although hyperparameter tuned models delivered competitive performances in comparison to the model with EDA and added features, the latter performed exceptionally better on the Kaggle (test) dataset. 

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|hpo1|hpo2|hpo3|score|
|--|--|--|--|--|
|initial|default|default|default|1.80899|
|add_features|default|default|default|1.80899|
|hpo|CAT(iterations),RF(n_estimators), XT(n_estimators)|GB(num_boost_round, num_leaves)|scheduler, searcher|0.66816|

### Create a line plot showing the top model score for the three (or more) training runs during the project.

TODO: Replace the image below with your own.

![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

TODO: Replace the image below with your own.

![model_test_score.png](img/model_test_score.png)

## Summary
-The AutoGluon AutoML framework for Tabular Data was thoroughly studied and incorporated into this bike sharing demand prediction project. 
-The AutoGluon framework's capabilities were fully utilized to make automated stack ensembled as well as individually distinct configured regression models trained on tabular data. It assisted in quickly prototyping a base-line model. 
-The top-ranked AutoGluon-based model improved results significantly by utilizing data obtained after extensive exploratory data analysis (EDA) and feature engineering without hyperparameter optimization.
-Leveraging automatic hyperparameter tuning, model selection/ensembling and architecture search allowed AutGluon to explore and exploit the best possible options. 
-Addtionally, hyperparameter tuning using AutoGluon also offered improved performance over the initial raw submission; but it wasn't better than that of the model with EDA, feature engineering and no hyperparameter tuning.  
-It was noticed that hyperparameter-tuning using AutoGluon (without default hyperparameters or random configuration of parameters) is a cumbersome process, and is highly dependent on the time limit, prescribed presets, possible family of models and range of hyperparameters to be tuned.
