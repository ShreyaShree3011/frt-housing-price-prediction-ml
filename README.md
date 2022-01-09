# HOUSING PRICE PREDICTION USING MACHINE LEARNING
## DESCRIPTION 
##### Housing Price Prediction Using Machine Learning is to predict the data of housings. Here I have included many data features. The most important feature according to the builders perspective view would be Bedroom. Sometimes it’s very important for a builder to check which is the highest selling house type which enables the builder to make houses which are more than three bedrooms. In the output section you would be seeing the visualization of three bedroom houses that are most commonly sold followed by four bedrooms. The main aim of this project is to make a model which can give a good prediction on the price of the house based on other variables. 
#
## PROGRAMMING LANGUAGE USED
##### PYTHON
#
## AZURE TECHNOLOGIES USED 

##### AZURE MACHINE LEARNING 
##### AZURE CLOUD SHELL
##### VISUAL STUDIO CODE

#

## INSTALLATION
##### STEP 1 : Install Python, Git, Anaconda and Jupyter in your systems.
##### STEP 2 : After all the installation part rebbot your system.
##### STEP 3 : Open Command Prompt in your system and check the python version.
##### STEP 4 :In Command Prompt install 
- #### PyPI
- #### numpy
- #### pandas
- #### matplotlib 
- #### seaborn 

#
## UPLOADING CODE TO AZURE MACHINE LEARNING STUDIO
##### STEP 1 : Login to your Azure Portal 
##### STEP 2 : Create a Resource Group
##### STEP 3 : In resource group click on create 
##### STEP 4 : Go to Categories and under that select AI + Machine Learning.
##### STEP 5: Select Machine Learning and click on create.  
##### STEP 6 : In Basic Section under project details select your subscription and resource group. After that in Workspace details specify your Workspace name and select your nearest region.  
##### STEP 7 : Click on Review + Create and the Deployment progress will start.
##### STEP 8 : After a sucessfull deployment launched Azure Machine Learning Studio to build and deploy the machine learning models.
##### STEP 9 : Create a new notebook in azure machine learning studio and uploaded your code.
##### STEP 10 : Next step is to upload the code in GitHub. So here, I have used Azure Cloud Shell. 
##### STEP 11 : Log in to GitHub Account and create a repository name.
##### STEP 12 : Follow the below steps.

#

# ML WITH GITHUB ACTIONS AND AZURE MACHINE LEARNING

### 1. Prerequisites

The following prerequisites are required to make this repository work:
- Azure subscription
- Contributor access to the Azure subscription
- Access to GitHub Actions

### 2. Create repository
Create a new repositary in GitHub and save the file.

### 3. Setting up the required secrets
Go to Resource group and use azure cloud shell.

```sh
# Replace {service-principal-name}, {subscription-id} and {resource-group} with your 
# Azure subscription id and resource group name and any name for your service principle
az ad sp create-for-rbac --name {"service-principal-name"} --role contributor --scopes /subscriptions/{subscription-id}/resourceGroups/{resource-group} --sdk-auth
```

This will generate the following JSON output:

```sh
{
  "clientId": "<GUID>",
  "clientSecret": "<GUID>",
  "subscriptionId": "<GUID>",
  "tenantId": "<GUID>",
  (...)
}
```

Add this JSON output as a secret with the name AZURE_CREDENTIALS in GitHub repository

### 4. Define your workspace parameters

You have to modify the parameters in the "/.cloud/.azure/workspace.json">`/.cloud/.azure/workspace.json"`.
Please use the same value for the `resource_group` parameter that you have used when generating the azure credentials. If you already have an Azure ML Workspace under that resource group, change the `name` parameter in the JSON file to the name of your workspace, if you want the Action to create a new workspace in that resource group, pick a name for your new workspace, and assign it to the `name` parameter. You can also delete the `name` parameter, if you want the action to use the default value, which is the repository name. Once you save your changes to the file, the predefined GitHub workflow that trains and deploys a model on Azure Machine Learning gets triggered. Check the actions tab to view if your actions have successfully run.

### 5. Modify the code

Now you can start modifying the code in the code folder, so that your model and not the provided sample model gets trained on Azure. Where required, modify the environment yaml so that the training and deployment environments will have the correct packages installed in the conda environment for your training and deployment. Upon pushing the changes, actions will kick off your training and deployment run. Check the actions tab to view if your actions have successfully run.

### 6. Viewing your AML resources and runs
The log outputs of your action will provide URLs for you to view the resources that have been created in AML. Alternatively, you can visit the Machine Learning Studio to view the progress of your runs, etc.
