# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Bhaswata Choudhury

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
Replace negative values with zeros as negative values aren't valid.

### What was the top ranked model that performed?
WeightedEnsamble was the top ranked model.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
* EDA showed no missing values
* No strongly correlated values found, hence nothing needed to be dropped for feature reduction
* atemp, temp and humidity showed gaussian distribution
* casual and registered columns werent in the test dataframe hence were dropped to avoid problems during inference
* people preferred to fo on bike rides more often when holiday bool is set to 0

### How much better did your model preform after adding additional features and why do you think that is?
The model performed drastically better on addition of the hour feature from datetime column. The hour of the day drastically influences how long people rent the bike for. And since many people preferred not to rent bikes for long periods of time, it plays a significant role in prediction 

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
My model performed slightly worse than with default parameters

### If you were given more time with this dataset, where do you think you would spend more time?
* feature engineering
* ensamble of different models rather than autogluon
* Custom Neural Network implementation with more hidden layers

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|time|gbm_options|nn_options|score|
|--|--|--|--|--|
|initial|600|default|default|1.79443|
|add_features|600|default|default|0.67597|
|hpo|600|num_boost_round:100, num_leaves: ag.space.Int(lower=26, upper=66, default=36)|lr = ag.space.Real(1e-4, 1e-2, default=5e-4, log=True), activation: ag.space.Categorical('relu', 'softrelu', 'tanh'), dropout_prob: ag.space.Real(0.0, 0.5, default=0.1)	0.50082|0.50082|

### Create a line plot showing the top model score for the three (or more) training runs during the project.



![model_train_score.png](nd009t-c1-intro-to-ml-templates/cd0385-project-starter/project/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.



![model_test_score.png](nd009t-c1-intro-to-ml-templates/cd0385-project-starter/project/model_kaggle_score.png)


#SUMMARY
This report presents the findings and outcomes of a project focused on predicting bike sharing demand using the AutoGluon solution. Throughout the project, several key insights and adjustments were made to enhance the accuracy of the predictions. The top-performing model was identified as the WeightedEnsemble. This model demonstrated superior performance in accurately forecasting bike rental demand.

Exploratory data analysis revealed that there were no missing values in the dataset, and no strongly correlated features needed to be dropped for feature reduction. Gaussian distributions were observed in variables such as "atemp," "temp," and "humidity." Additionally, the "holiday" boolean had a significant impact on bike ride preferences, with a preference for non-holiday periods.

Hyperparameter tuning was conducted; however, it was found that the model's performance slightly deteriorated compared to the default parameters. This highlighted the effectiveness of the default settings for the given problem.