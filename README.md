*NOTE:* This file is a template that you can use to create the README for your project. The *TODO* comments below will highlight the information you should be sure to include.

# Your Project Title Here
Capstone Project - Azure Machine Learning Engineer
*TODO:* Write a short introduction to your project.
In this project, we created two models: one using Automated ML (denoted as AutoML from now on) and one customized model whose hyperparameters are tuned using HyperDrive.We, then compared the performance of both the models and deployed the best performing model.

## Project Set Up and Installation
*OPTIONAL:* If your project has any special installation steps, this is where you should put it. To turn this project into a professional portfolio project, you are encouraged to explain how to set up this project in AzureML.

## Dataset
Heart Failure Prediction
### Overview
*TODO*: Explain about the data you are using and where you got it from.
Heart failure is a common event caused by CVDs and this dataset contains 12 features that can be used to predict mortality by heart failure. This dataset contains 300 samples. This dataset is availabe on Kaggle, which can be accesed using following link

https://www.kaggle.com/datasets/andrewmvd/heart-failure-clinical-data


### Task
*TODO*: Explain the task you are going to be solving with this dataset and the features you will be using for it.
This is a classification task where we need to predict the death event (which is a binary class) given the related features. The Features which are used to predict as follows:

['age', 'anaemia', 'creatinine_phosphokinase', 'diabetes','ejection_fraction', 'high_blood_pressure', 'platelets','serum_creatinine', 'serum_sodium', 'sex', 'smoking', 'time']

### Access
*TODO*: Explain how you are accessing the data in your workspace.
We are accessing data using an external link with the help of "TabularDatasetFactory().from_delimited_files()" this Azureml funtion. The dataset is available on GitHub repo. 
![alt text](https://github.com/Keshav-agrawal2829/Udacity-capstone-azureml/blob/main/dataset.PNG)

## Automated ML
*TODO*: Give an overview of the `automl` settings and configuration you used for this experiment
the Automl setting adn Configuration is used as showin in the following image
![alt text](https://github.com/Keshav-agrawal2829/Udacity-capstone-azureml/blob/main/aml_config.PNG)

| Configuration | Description | Value |
| ------ | ------ | ------|
| task | The type of task to run. Values can be 'classification', 'regression', or 'forecasting' depending on the type of automated ML problem | classification|
| training_data | data on which model needs to be trained | dataset |
| label_column_name | Target Column name | DEATH_EVENT |
| experiment_timeout_minutes | This is used as an exit criteria, it defines how long, in minutes, your experiment should continue to run | 20 |
| max_concurrent_iterations | Represents the maximum number of iterations that would be executed in parallel | 5 |
| primary_metric | 	The metric that Automated Machine Learning will optimize for model selection | AUC_Weighted |
| compute_target | The compute target | trainCluster |
| n_cross_validations | No. of cross validations to perform | 5 |


### Results
*TODO*: What are the results you got with your automated ML model? What were the parameters of the model? How could you have improved it?

| Parameters | Value|
| ----| ---- |
| boosting_type | gbdt|
| colsample_bytree | 0.723333333332 |
| learning_rate | 0.068893135642 |
| max_bin| 70 |
| max_depth | 8 |
| min_child_weight | 8 |
| min_data_in_leaf | 0.039986572413755 |
| n_estimators | 400 |
| num_leaves | 200 |
| subsample | 0.29658742214525 |


To improve the results we can take more samples to train the model, increase in sample size will improve the model quality


*TODO* Remeber to provide screenshots of the `RunDetails` widget as well as a screenshot of the best model trained with it's parameters.
*Run Details* 
![alt text](https://github.com/Keshav-agrawal2829/Udacity-capstone-azureml/blob/main/rundetails_automl.PNG)

*Printing best Model detailes*
![alt text](https://github.com/Keshav-agrawal2829/Udacity-capstone-azureml/blob/main/rundetails_automl.PNG)

## Hyperparameter Tuning
*TODO*: What kind of model did you choose for this experiment and why? Give an overview of the types of parameters and their ranges used for the hyperparameter search

To do the classification I have used the logistic regression based Machine Learning Method where there are two hyperparameters are there "C" and "max-iter". 
"C" : - The Inverse of regularization Strength
"max_iter" :-  Maximum number of iterations taken for the solver to converge

### Results
*TODO*: What are the results you got with your model? What were the parameters of the model? How could you have improved it?

![alt text](https://github.com/Keshav-agrawal2829/Udacity-capstone-azureml/blob/main/best_model_hyperdrive1.PNG)

we can improve the model if we can normalize the columns of the dataset and if we can increase the range of hyperparameters we might get batter set of values of hyperparameters

*TODO* Remeber to provide screenshots of the `RunDetails` widget as well as a screenshot of the best model trained with it's parameters.

![alt text](https://github.com/Keshav-agrawal2829/Udacity-capstone-azureml/blob/main/rundetails_hyperdrive.PNG)

## Model Deployment
*TODO*: Give an overview of the deployed model and instructions on how to query the endpoint with a sample input.

*Service Active*
![alt text](https://github.com/Keshav-agrawal2829/Udacity-capstone-azureml/blob/main/service_active.PNG)

*testing the response of the Deployed Model*
![alt text](https://github.com/Keshav-agrawal2829/Udacity-capstone-azureml/blob/main/service_response_logs.PNG)

## Screen Recording
Please find the recorded video on below link
https://youtu.be/IY9YQMa7Qp4

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
