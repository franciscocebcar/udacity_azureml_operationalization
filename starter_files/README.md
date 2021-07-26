# Operationalizing the Bank Marketing AutoML Model

For this project I use the AutoML capabilities of AzureML to train multiple machine learning models and operationalize the best performing model according to the accuracy metric.

Once the best model is deployed on an Azure Container Instance and is available through a REST API endpoint, I test calling the "score" endpoint to generate predictions for a couple of observations.

I also create and publish a pipeline that performs that training using the AzureML SDK. This is performed using a Jupyter Notebook executed on an Azure Compute Instance, although it can be run locally as well (i.e. local VS Code connected to Azure)

## Architectural Diagram
*TODO*: Provide an architectual diagram of the project and give an introduction of each step. An architectural diagram is an image that helps visualize the flow of operations from start to finish. In this case, it has to be related to the completed project, with its various stages that are critical to the overall flow. For example, one stage for managing models could be "using Automated ML to determine the best model". 

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
### Create, Publish and Consume Training Pipeline

## Screen Recording
Please access the recording through this link: https://youtu.be/pyIye5BNzjs

## Standout Suggestions
No standout suggestions were attempted as I would focus on other areas of data analysis
