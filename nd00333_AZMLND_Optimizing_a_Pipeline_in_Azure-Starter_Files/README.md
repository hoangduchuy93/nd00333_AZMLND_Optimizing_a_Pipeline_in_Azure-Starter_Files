# Optimizing an ML Pipeline in Azure

## Overview
This project is part of the Udacity Azure ML Nanodegree.
In this project, we build and optimize an Azure ML pipeline using the Python SDK and a provided Scikit-learn model.
This model is then compared to an Azure AutoML run.

## Useful Resources
- [ScriptRunConfig Class](https://docs.microsoft.com/en-us/python/api/azureml-core/azureml.core.scriptrunconfig?view=azure-ml-py)
- [Configure and submit training runs](https://docs.microsoft.com/en-us/azure/machine-learning/how-to-set-up-training-targets)
- [HyperDriveConfig Class](https://docs.microsoft.com/en-us/python/api/azureml-train-core/azureml.train.hyperdrive.hyperdriveconfig?view=azure-ml-py)
- [How to tune hyperparamters](https://docs.microsoft.com/en-us/azure/machine-learning/how-to-tune-hyperparameters)


## Summary
- The dataset is about the characteristics of customers at a bank such as age, default, loan, ... The purpose of this project is to predict if the customer will subcribe to term deposit (TD)

- The best model is Voting Ensembler

## Scikit-learn Pipeline
- The traditional way is to import the Logistics regression from sklearn and process the HyperDrive to find the most accurate model.
- The dataset is cleaned first. Then split to train and test with ratio 80:20.
- Model using: Logistics Regression

- Benefit of sampler: The Random Parameter Sampling help to choose randomly different parameters provided. Each combination of C and max_iter will be tried to find the optimal accuracy.

- Benefit of early stopping: Bandit early stopping helps to stop the training when there is not improvement in accuracy. This can help to reduce the training time and resource.
## AutoML
- AutoML can automatically take the input data, then performce missing values handler, feature engineerings, hyperdrive automatically with different types of models. Some paramters of AutoML are: task (classification/ regression), training_data (the data for training), label_column_name (your target), primary_metric (metric for evaluation), n_cross_validations (k-fold cross validation), etc.

## Pipeline comparison
- I do not see much different between AutoML and HyperDrive manually in this case. The accuracy of HyperDrive is 0.908 while AutoML is 0.918.
- I think the gap between 2 methods are little in this case because the dataset is small, clean, and the variables are very close to target (I mean they have strong relation). In real world projects, datasets are much more complex. In real world I think AutoML will perform better, if the person do HyperDrive do not have any extra knowledge about the dataset.
- Overall, I think AutoML is great because it can use many models, so that it can find the best one. Rather than HyperDrive in this case only use Logistics Regression. Using one model can lead to bias.

## Future work
- I would try to recreate the AutoML for my real wolrd problem. Because the AutoML seems to be a black box. I do not know how can it can recoginize different data types, and have solution to handle with data as well as create new features.

## Proof of cluster clean up
**If you did not delete your compute cluster in the code, please complete this section. Otherwise, delete this section.**
**Image of cluster marked for deletion**
