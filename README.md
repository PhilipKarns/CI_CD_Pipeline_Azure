# CI_CD_Pipeline_Azure
Building a Continuous Integration and Continuous Delivery pipeline for a Flask machine learning application in Python

# Overview
This project will start with cloning a github repo in Azure Cloud Shell, followed by creating project scaffolding for Continuous Integration which includes a Makefile, requirements.txt, 
a Python Virtual Environment, a Python script and test file for the script. Then, it will use GitHub Actions to test our project when change events occur in GitHub. GitHub Actions will
automatically build our project, performing install, lint and test actions to verify our tests pass, and this step completes the Continuous Integration portion of the project. Finaly,
this project will be integrated with Azure Pipelines to enable Continuous Delivery to Azure App Service using a Flask Machine Learning API.

## Project Plan

### Trello Board
https://trello.com/b/7KN3nSMa/build-devops-process-to-deploy-ml-app

### Spreadsheet with Project Plan
https://docs.google.com/spreadsheets/d/1vs-qzjjO7mzfw8u8LQUzjz72jgQyWUKWP8PfD2kf7fs/edit#gid=0

## Architectural Diagram
![architectural Diagram](./images/ArchitecturalDiagram.PNG)

## Instructions
<TODO:  Instructions for running the Python project.  How could a user with no context run this project without asking you for any help.  Include screenshots with explicit steps to create that work. Be sure to at least include the following screenshots:
### Continuous Integration

#### Part 1
:white_check_mark: Create SSH Keys in Azure Cloud Shell and add to GitHub
:white_check_mark: Clone GitHub Repository
:white_check_mark: Run make all to install, lint and test the code

Click on the Azure Cloud Shell Icon in the Azure Portal
![Azure Cloud Shell](./images/click-azuzre-cloud-shell.PNG)

Run command ssh-keygen -t rsa to generate SSH Keys
![Generate SSH Keys](./images/generate-ssh-keys.PNG)

Type command cat /home/yourAzureName/.ssh/id_rsa.pub to get your key, and then copy it, including the ssh-rsa part. For example,
as seen in the below image, my name in lowercase, philip, is listed in front of Azure at the prompt, so in the cat command I put 
/home/philip/.ssh/id_rsa.pub. 
![Get SSH key value](./images/cat-ssh-key.PNG)

In GitHub, click on your profile picture, then settings, then SSH and GPG keys, and then New SSH key. Paste your SSH key into
the key field and then click the Add SSH key button. 
![Get SSH key value](./images/github-ssh-key-add.PNG)

In Azure Cloud Shell clone this repository using the SSH link git@github.com:PhilipKarns/CI_CD_Pipeline_Azure.git. After hitting enter, 
cd into the project.
![Clone Repository](./images/git_project_cloned_to_AzureCloudShell_screenshot.PNG)

Run the Make All command to install, lint, and test the code using the Makefile.
![Make All](./images/makeallscreenshot1.PNG)
![Make All](./images/makeallscreenshot2.PNG)

### Continuous Delivery 
:white_check_mark: Set up Virtual Environment
:white_check_mark: Create an App Service 
:white_check_mark: Verify the deployed application works
:white_check_mark: Perform a prediction
:white_check_mark: Azure Pipelines Deployment
:white_check_mark: Running Azure App Service from Azure Pipelines


To set up the virtual environment, first enter command  python3 -m venv ~/.CI_CD_Pipeline_Azure and hit enter. Then enter command 
source ~/.CI_CD_Pipeline_Azure/bin/activate and hit enter 
![Virtual Environment](./images/virtual-environment.PNG)

To create your app service, first run command make install to install any required libraries. Then run command 
az webapp up -n yourappservicename. Your app service name has to be one that hasn't already been used. Here's mine:
![Create App Service](./images/appservice-create.PNG)

Click on the URL to see your deployed app service:  
![Deployed App Service](./images/appservice-url-running.PNG)

To perform a prediction, first go into the make_predict_azure_app.sh file and change the app name to the one you created:  
![Change App Service Name](./images/make-predict-changeappname.PNG)

Then run command ./make_predict_azure_app.sh to get a prediction
![App Service Prediction](./images/appservice-prediction.PNG)

To complete the Continuous Delivery, I've set up this Machine Learning Application to deploy in Azure Pipelines within the Azure devops
environment. Here is an example of a recent successful deployment: 
![Azure Pipelines Deployment](./images/azure-piplines-deployment.PNG)

And if I click on Deploy Web App from the above screen, we can see the URL of the successfully deployed Flask app, and if we click on it 
we see the running app service application.
![App Service Deployed](./images/appservice-deployed-azurepipelines.PNG)
![App Service Deployed URL](./images/appservice-deployed-azurepipelines-url.PNG)

Here is the output of the log files from the application:  
![Running App Log Files](./images/log-files.PNG)

## Enhancements
- this project could be improved by setting up additional machine learning predictions for housing in other major cities
- we could also use GitHub Actions for deployment instead of Azure Pipelines

## Demo 

<TODO: Add link Screencast on YouTube>

=======
![Python application test with Github Actions](https://github.com/PhilipKarns/CI_CD_Pipeline_Azure/workflows/Python+application+test+with+Github+Actions/badge.svg)
<!-- >>>>>>> 55093ffc384c3972fb7a26e5b3f5fbe7e60f4d7d -->
