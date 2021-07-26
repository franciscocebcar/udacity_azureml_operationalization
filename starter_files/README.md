# Operationalizing the Bank Marketing AutoML Model

For this project I use the AutoML capabilities of AzureML to train multiple machine learning models and operationalize the best performing model according to the accuracy metric.

Once the best model is deployed on an Azure Container Instance and is available through a REST API endpoint, I test calling the "score" endpoint to generate predictions for a couple of observations.

I also create and publish a pipeline that performs that training using the AzureML SDK. This is performed using a Jupyter Notebook executed on an Azure Compute Instance, although it can be run locally as well (i.e. local VS Code connected to Azure)

## Architectural Diagram
*TODO*: Provide an architectual diagram of the project and give an introduction of each step. An architectural diagram is an image that helps visualize the flow of operations from start to finish. In this case, it has to be related to the completed project, with its various stages that are critical to the overall flow. For example, one stage for managing models could be "using Automated ML to determine the best model". 

## Key Steps
*TODO*: Write a short discription of the key steps. Remeber to include all the screenshots required to demonstrate key steps. 

## Screen Recording
Please access the recording through this link: https://youtu.be/pyIye5BNzjs

## Standout Suggestions
No standout suggestions were attempted as I would focus on other areas of data analysis
