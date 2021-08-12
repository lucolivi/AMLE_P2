# Deploying and Debugging Models and Pipelines
### Author: Lucas V. Oliveira

## Table of Contents
1. [Overview](#overview)
2. [Architectural Diagram](#architectural-diagram)
3. [Key Steps](#key-steps)
4. [Screen Recording](#screen-recording)


## Overview

In this project we are using the [bank marketing dataset](https://archive.ics.uci.edu/ml/datasets/bank+marketing) to do two things:
- Train a model using Azure AutoML, deploying the best model and debugging its webservice;
- Create, run and publish a pipeline to trigger automatically a model training using Azure AutoML.

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
A demo for this project is available in this link https://www.youtube.com/watch?v=sH_8H4oWJa4

