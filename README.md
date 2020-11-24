# How to eliminiate Azure Data Factory's public internet exposure using private link

Azure Private Link was made generally available on Feb 2020.  Since then, it made numerous Azure PaaS services more secured.  By eliminating data transfer via the public internet, Azure Private Link help reduce the exposure to cyber security attacks significantly.

Of most PaaS Services, Azure DAta Factory is considered to be 1 of the most important services to be secured. An ADF instance can connect to numerous data sources that might contain sensitive customer information - and the impact of data exposure can be far more serious than any other PaaS service.  Making ADF more secured, therefore, is critical in building a secure data solution on Azure.

In the folloowing sections, we are going to walk through
i) How private link work to make Azure Data Factory more secured; and
ii) Provide sample ARM tempalte for you to provision an ADF environment that makes use of private link; and
iii) Provide reference links to Azure certification, in case you want to learn more about Azure Data Factory / Azure Private Linke

## What is Azure Private Link?
Azure Private Link enables you to access Azure PaaS Services (for example, Azure Storage and SQL Database) and Azure hosted customer-owned/partner services over a private endpoint in your virtual network.
Traffic between your virtual network and the service travels the Microsoft backbone network. Exposing your service to the public internet is no longer necessary.

Refer to below link for more details
 What is Azure Private Link?
 https://docs.microsoft.com/en-us/azure/private-link/private-link-overview


## What is Azure Data Factory?
Azure Data Factory is the cloud-based ETL and data integration service that allows you to create data-driven workflows for orchestrating data movement and transforming data at scale. Using Azure Data Factory, you can create and schedule data-driven workflows (called pipelines) that can ingest data from disparate data stores. You can build complex ETL processes that transform data visually with data flows or by using compute services such as Azure HDInsight Hadoop, Azure Databricks, and Azure SQL Database.

Azure Data Factory consists of 2 planes: the "control plane" and "data plane".

The "control plane" store metadata such as pipeline definition and schedule, and provides Data Factory pipelines authoring and monitoring.  

The "data plane" is a compute infrastructure called Integration Runtime (IR) to provide data integration capabilities.   It connects to "linked service", which are data stores or compute services, to perform "activities", which can be copying data between data stores, running Data Flows, or dispatching transform activities to other Azure services such as HDInsight, Databricks and Azure Machine Learning. 

The below logical diagram illustrates the various components for an Azure Data Factory pipeline.  
![Azure Data Factory - logical diagram](https://github.com/caryeun/adfpl/blob/main/media/ADF_Overview.png)


## How does Private Link makes Data Factory more secure?




## How may I test it out?


## I am interested to know more.  Where may I find more information?


 

