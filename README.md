# Table Of Contents

1. Introduction
2. Open COVID-19 datasets
3. Data Flow Architecture Diagram
4. Data Pipeline deployment steps
5. CI/CD setup for Azure Data Factory
6. Connect Azure Boards with the Github Repo
7. Add Metric Alerts to Azure Data Factory Pipelines
8. Configure Data Share
9. Set up Synapse Notebook
10. Machine Learning forecast model
11. Troubleshoot ADF Pipelines
12. Contact Us

# One-Click Deployment of Covid-19 Data Pipelines
This is a guide for processing the following open Covid-19 datasets, using the Microsoft Azure data factory. 


## 1. Introduction
We have seen COVID-19 changing the landscape around us in a matter of a few months and as anticipated, businesses and communities are trying to adapt to this situation and continue their operations while minimizing the risks associated with the current situation and the long term pandemic recovery phase, the future. We live in a data-driven world, where many organizations are trying to fight this pandemic and start the recovery process. This document is about utilizing open COVID-19 datasets in Microsoft Azure Data Factory to get meaningful insights that can help organizations make informed decisions and initiate the recovery phase.


## 2. Open COVID-19 datasets
We have published the ARM templates for utilizing the following datasets. 

Dataset | Descriptions | Link | Status
------- | ------------ | ---- | ------
[Definitive Healthcare USA](https://coronavirus-resources.esri.com/datasets/definitivehc::definitive-healthcare-usa-hospital-beds?geometry=110.039%2C-16.820%2C-135.000%2C72.123) | The latest data on COVID-19 about USA Hospital Beds. | [definitive-healthcare](https://github.com/nashahz/azure-data-pipelines/tree/master/datasets/covid-19/definitive-healthcare) | Available
[Newyork Times](https://github.com/nytimes/covid-19-data) | Daily data on COVID-19 about US counties. | [newyork-times](https://github.com/nashahz/azure-data-pipelines/tree/master/datasets/covid-19/newyork-times) | Available
[Govt of Ontario](https://data.ontario.ca/dataset?keywords_en=COVID-19) | Compiled daily reported data from public health units on confirmed positive cases of COVID-19 in Ontario. | [ontario](https://github.com/nashahz/azure-data-pipelines/tree/master/datasets/covid-19/ontario) | Available
[Govt of British Columbia](http://www.bccdc.ca/health-info/diseases-conditions/covid-19/data) | Daily data on COVID-19 cases in British Columbia. | [british-columbia](https://github.com/nashahz/azure-data-pipelines/tree/master/datasets/covid-19/british-columbia) | Available

## 3. Data Flow Architecture Diagram
![Azul_Data_Pipeline](./images/architectureV1.png)

## 4. Data Pipeline deployment steps
  You can see that the repo has multiple sections. Go inside each of the directories to deploy that relevant section.  

## 5. CI/CD setup for Azure Data Factory

We have provided an Azure Pipelines yaml that can be used to set up CI/CD for Azure Data Factory. The pipeline is triggered when you publish changes in the Dev data factory (The one that is connected to Github). The pipeline reads the generated ARM templates from the Dev Data factory and deploys it to Prod. 

You can follow the instructions given in the following link to set up CI/CD using Azure Pipelines:-

[Azure Data Factory CICD](./datasets/covid-19/definitive-healthcare/azure-pipelines-cicd/readme.md)

## 6. Connect Azure Boards with the Github Repo

Boost your team's productivity with Boards, Backlogs, and Sprints for even the most complex project. Simply connect your GitHub repo to Azure Boards and start linking commits and PRs to work items.

By connecting your Azure Boards project with GitHub.com repositories, you support linking between GitHub commits and pull requests to work items. You can use GitHub for software development while using Azure Boards to plan and track your work.

When you make the connection from Azure Boards, the list of GitHub repositories correspond to ones that you allow Azure Boards to access. You can limit which repositories Azure Boards can access overall, and limit what a particular project can access or split the management of work across different Azure Boards projects.

Please follow the instructions given in the following link to connect Azure Boards to Github:-

[Connect Azure Boards to Github](https://docs.microsoft.com/en-us/azure/devops/boards/github/connect-to-github?view=azure-devops)


## 7. Add Metric Alerts to Azure Data Factory Pipelines

Alerts come in handy when we want feedback on failure or cancellation of the pipeline or its respective activities. We get debugging information out of the box which helps save a lot of effort and reduce downtime. 

Follow the instructions given in the following link to set up alerts:-

For Public Environment Alerts:- 

[Setup Metric Alerts Public Environment](./datasets/covid-19/definitive-healthcare/public/Readme.md)

For Customer Environment Alerts:- 

[Setup Metric Alerts Customer Environment](./datasets/covid-19/definitive-healthcare/customer/Readme.md)

## 8. Configure Data Share

If you are using Data Share to get data from a public environment into the customer environment, you need to set up a Data Share account along with share on the public side and send an invite to the customer side where a Data Share account must be present to accept the invitation. To deploy the Data Share account on either of the two environments, you will need to select the option Yes/No to do so. If Yes is selected while deploying the public side, then the data share account and a share will be deployed in the public side whereas if you select Yes on the customer side, a data share account will be deployed and the data pipeline that will be deployed will be the one without copy data activity that copies the data from the public storage account to the customer one.

You can follow the instructions given in the following link to set up a Azure Data Share account and create/accept invitation:-

[Azure Data Share](./datasets/covid-19/definitive-healthcare/customer/Readme.md)

## 9. Set up Synapse Notebook

You can make use of Azure Synapse notebook for quick experimentation, data preparation, visualization and validation using Azure Notebook. Given below is the link with instruction to set up that:-


[Azure Synapse Notebook](./datasets/covid-19/definitive-healthcare/azure-notebook/readme.md)

## 10. Machine Learning forecast model

To run an ML model as part of your pipeline, on top of curated dataset using Azure Machine Learning, follow the instructions given below. By following the instructions you can build an ML model, make its execution part of the ADF pipeline and then use Power BI for visualization.

[On Demand Forecasting](./datasets/covid-19/newyork-times/on-demand-forecast-model/Readme.md)

## 11. Troubleshoot ADF Pipelines

Please follow the instructions given in the link below:-

[Troubleshoot ADF Pipelines](./docs/trouebleshoot.md)

## 12. Contact us

We hope that this document is helpful to you. In case you have any questions, feel free to reach out to us at ayesha.khaliq@emumba.com OR hamza.rashid@emumba.com.
