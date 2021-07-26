# Operationalizing the Bank Marketing AutoML Model

For this project I use the AutoML capabilities of AzureML to train multiple machine learning models and operationalize the best performing model according to the accuracy metric.

Once the best model is deployed on an Azure Container Instance and is available through a REST API endpoint, I test calling the "score" endpoint to generate predictions for a couple of observations.

I also create and publish a pipeline that performs that training using the AzureML SDK. This is performed using a Jupyter Notebook executed on an Azure Compute Instance, although it can be run locally as well (i.e. local VS Code connected to Azure)

## Architectural Diagram
This is a high level diagram of the steps completed for this project:

![Image architecture](https://github.com/franciscocebcar/udacity_azureml_operationalization/blob/master/starter_files/screenshots/architecture.png)

We first use the AzureML AutoML functionality to train a number of models and identify the best performing model.

We then deploy the best model and obtain a REST API endpoint.

Once the model is deployed, we test it by using Python to call the REST API endpoint and Apache Benchmark to generate some metrics.

Lastly, I create a AzureML Pipeline programmatically using the AzureML SDK so that all the model training steps can be executed as a pipeline through a REST API endpoint (provisioning of cluster, acquisition/register of dataset and AutoML configuration and execution)

## Key Steps
### Creation of AutoML Experiment
The AutoML experiment is created by completing 3 basic steps: registering/selecting the dataset, specifying the compute target, and specifying AutoML configuration settings.

The registered dataset:

![Image of registered dataset](https://github.com/franciscocebcar/udacity_azureml_operationalization/blob/master/starter_files/screenshots/step_2_registered_dataset.png)

Once the AutoML Experiment completes, we can check its details, including the best model:

![Image of run details](https://github.com/franciscocebcar/udacity_azureml_operationalization/blob/master/starter_files/screenshots/step_2_completed_automl_run.png)

Best model:

![Image of best model](https://github.com/franciscocebcar/udacity_azureml_operationalization/blob/master/starter_files/screenshots/step_2_best_model.png)

We can dig deeper and inspect all the metrics captured:

![Image of model metrics](https://github.com/franciscocebcar/udacity_azureml_operationalization/blob/master/starter_files/screenshots/step_2_best_model_metrics.png)

### Deployment of Best Model
We can then click on the best model and then on the "Deploy" button in order to deploy the model and get a REST API endpoint.

Once the model is deployed, we see its endpoint:

![Image endpoints](https://github.com/franciscocebcar/udacity_azureml_operationalization/blob/master/starter_files/screenshots/step_3_deployed_model_endpoint.png)

And we can inspect the endpoint details:

![Image endpoint details](https://github.com/franciscocebcar/udacity_azureml_operationalization/blob/master/starter_files/screenshots/step_3_endpoint_details.png)

### Enabling Application Insights and checking logs
We can also enable logging and Application Insights by using the AzureML SDK. Once Application Insights is enabled:

![Image application insights](https://github.com/franciscocebcar/udacity_azureml_operationalization/blob/master/starter_files/screenshots/step_4_application_insights_enabled.png)

And we can take a look at the logs also using the AzureML SDK:

![Image logs](https://github.com/franciscocebcar/udacity_azureml_operationalization/blob/master/starter_files/screenshots/step_4_logs.png)

### Exploring the REST API endpoint using Swagger
We can download the swagger.json file from the endpoint, and inspect it locally using the swagger docker container:

![Image swagger](https://github.com/franciscocebcar/udacity_azureml_operationalization/blob/master/starter_files/screenshots/step_5_swagger.png)

This allows us to inspect the web service endpoints in order to build a JSON file to submit to the model endpoint.

### Consume Model Endpoint to generate predictions
We can use a Python script to create a JSON payload and call the REST API endpoint:

![Image endpoint call](https://github.com/franciscocebcar/udacity_azureml_operationalization/blob/master/starter_files/screenshots/step_6_endpoint_call.png)

We can also run Apache Benchmark (ab) to make multiple calls to the REST API endpoint and capture some metrics:

![Image benchmark start](https://github.com/franciscocebcar/udacity_azureml_operationalization/blob/master/starter_files/screenshots/step_6_benchmark_start.png)

![Image benchamark end](https://github.com/franciscocebcar/udacity_azureml_operationalization/blob/master/starter_files/screenshots/step_6_benchmark_end.png)

### Create, Publish and Consume Training Pipeline
Lastly, we can also create an AzureML Pipeline using the SDK to perform all the steps programmatically.
For this purpose, I used the Jupyter notebook provided and modified it to refer to the experiment, cluster and dataset that had been manually created.

After creating the pipeline, we can see it in the AzureML interface:

![Image pipelines](https://github.com/franciscocebcar/udacity_azureml_operationalization/blob/master/starter_files/screenshots/step_7_pipelines.png)

After running and publishing the pipeline, we is accessible through a pipeline endpoing:

![Image pipeline endpoint](https://github.com/franciscocebcar/udacity_azureml_operationalization/blob/master/starter_files/screenshots/step_7_pipeline_endpoint.png)

And we can see the details of the published pipeline:

![Image published pipeline](https://github.com/franciscocebcar/udacity_azureml_operationalization/blob/master/starter_files/screenshots/step_7_published_pipeline.png)

In the Jupyter Notebook, as the pipeline was running, we could track its progress via the RunDetails Widget:

![Image run details](https://github.com/franciscocebcar/udacity_azureml_operationalization/blob/master/starter_files/screenshots/step_7_rundetails_widget.png)

Lastly, we can schedule the pipeline to run every 12 hours:

![Image schedule](https://github.com/franciscocebcar/udacity_azureml_operationalization/blob/master/starter_files/screenshots/step_7_scheduled_run.png)

## Screen Recording
Please access the recording through this link: https://youtu.be/pyIye5BNzjs

## Standout Suggestions
No standout suggestions were attempted as I would focus on other areas of data analysis
