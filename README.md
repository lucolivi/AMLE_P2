# Deploying and Debugging Models and Pipelines
### Author: Lucas V. Oliveira

## Table of Contents
1. [Overview](#overview)
2. [Architectural Diagram](#architectural-diagram)
3. [Key Steps](#key-steps)
4. [Screen Recording](#screen-recording)
5. [Further Improvements](#further-improvements)


## Overview

In this project we are using the [bank marketing dataset](https://archive.ics.uci.edu/ml/datasets/bank+marketing) to predict whether or not a bank client will subscribe to a term deposit. This task is divided into two parts:
- Train a model using Azure AutoML, deploying the best model and consume and debug its API using a REST endpoint;
- Create, run and publish a pipeline so we can use a REST endpoint to trigger automatically a model training using Azure AutoML.

## Architectural Diagram
![](project_flow.png)

## Key Steps

### Register Dataset
In this step we register dataset that will be used in the project.
![](screenshots/registered_datasets.png)

### Setup AutoML Experiment
Here we setup and run an AutoML experiment with the previous registered dataset in order to generate a well performing machine learning model.

![](screenshots/experiment_completed1.png)

![](screenshots/experiment_completed2.png)

### Deploy the Best Model API
Here we pick the best model found by the AutoML and deploy it so we can make requests to it using a REST API.

![](screenshots/best_model.png)
![](screenshots/best_model_deployed.png)

### Document API
In this step we use Swagger to expose our model API documentation methods so we can make use of them to get predictions.
![](screenshots/swagger1.png)

### Consume API
Using the methods shown in the documentation perform requests to the API and get predictions from it.
![](screenshots/consuming.png)

### Monitor API
In this step we monitor the usage of our deployed model. We can retrieve its logs of access, errors and also using application insights to get graphs with data about its usage.

![](screenshots/logging.png)

![](screenshots/app_insights2.png)


### Create Pipeline
In this step we create a pipeline to load the dataset into an AutoML experiment and run it.
![](screenshots_pipeline/pipeline_created1.png)
![](screenshots_pipeline/pipeline_created2.png)

### Publish Pipeline
Here we publish the create pipeline so it can be triggered by a REST endpoint.
![](screenshots_pipeline/published_pipeline_active_1.png)
![](screenshots_pipeline/published_pipeline_active_2.png)

### Trigger Pipeline
Here we use the published rest endpoint to trigger the pipeline created.
![](screenshots_pipeline/step_runs2.png)
![](screenshots_pipeline/scheduled_run.png)


## Screen Recording
A demo for this project is available in this link https://www.youtube.com/watch?v=4hulm2lHSEI

### Further Improvements

This project aims to automate a pipeline for model training. To improve it even further, we can do a few things:

- Get new versions of the dataset. The way the pipeline is configured it uses a static dataset, however the nature of the domain (bank client data) tends to increase the data available over time. Since more data is usually good for training a machine learning model, enhance the actual data gathering pipeline step to update the dataset would be useful.
- Include the deploy step into the pipeline. This way after making some change (like updating the dataset) and triggering the pipeline, it will complete the full cycle of getting the data, training the model and also deploying it automatically, without human intervention.

