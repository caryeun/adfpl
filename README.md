# How to eliminate Azure Data Factory's public internet exposure using private link

Azure Private Link was made generally available on Feb 2020.  Since then, it made numerous Azure PaaS services more secured.  By eliminating data transfer via the public internet, Azure Private Link help reduce the exposure to cyber security attacks significantly.

Of most PaaS Services, Azure DAta Factory is considered to be 1 of the most important services to be secured. An ADF instance can connect to numerous data sources that might contain sensitive customer information - and the impact of data exposure can be far more serious than any other PaaS service.  Making ADF more secured, therefore, is critical in building a secure data solution on Azure.

In the folloowing sections, we are going to walk through
i) How private link work to make Azure Data Factory more secured; and
ii) Provide sample ARM tempalte for you to provision an ADF environment that makes use of private link; and
iii) Provide reference links to Azure certification, in case you want to learn more about Azure Data Factory / Azure Private Linke

## What is Azure Private Link?
Azure Private Link enables you to access Azure PaaS Services (for example, Azure Storage and SQL Database) and Azure hosted customer-owned/partner services over a private endpoint in your virtual network.
Traffic between your virtual network and the service travels the Microsoft backbone network. Exposing your service to the public internet is no longer necessary.

Refer to below link for more details about Private Link:
 What is Azure Private Link?
 https://docs.microsoft.com/en-us/azure/private-link/private-link-overview


## What is Azure Data Factory?
Azure Data Factory is the cloud-based ETL and data integration service that allows you to create data-driven workflows for orchestrating data movement and transforming data at scale. Using Azure Data Factory, you can create and schedule data-driven workflows (called pipelines) that can ingest data from disparate data stores. You can build complex ETL processes that transform data visually with data flows or by using compute services such as Azure HDInsight Hadoop, Azure Databricks, and Azure SQL Database.

Azure Data Factory consists of 2 planes: the "control plane" and "data plane".

The "control plane" store metadata such as pipeline definition and schedule, and provides Data Factory pipelines authoring and monitoring.  

The "data plane" is a compute infrastructure called Integration Runtime (IR) to provide data integration capabilities.   It connects to "linked service", which are data stores or compute services, to perform "activities", which can be copying data between data stores, running Data Flows, or dispatching transform activities to other Azure services such as HDInsight, Databricks and Azure Machine Learning. 

The below logical diagram illustrates the various components for an Azure Data Factory pipeline.  
![Azure Data Factory - logical diagram](https://github.com/caryeun/adfpl/blob/main/media/ADF_Overview.png)

Refer to below link for more details Azure Data Factory:
 What is Azure Data Factory
 https://docs.microsoft.com/en-us/azure/data-factory/introduction


## How does Private Link makes Data Factory more secure?

### Network diagram - before Private Link for ADF is implemented
Before private link is available, the communication between ADF IR and ADF control plane will have to traverse the public internet, as shown below.

![Azure Data Factory - network diagram - without private link](https://github.com/caryeun/adfpl/blob/main/media/ADF_BeforePrivateLink.png)

In addition, you will have to open several communication channels between the Azure Data Factory and the virtual network:
- adf.azure.com, port 443; and
- \*.{region}.datafactory.azure.net, port 443; and
- \*.servicebus.windows.net, port 443; and
- download.microsoft.com

All of these adding up together are adding up unnessary risk exposure for Azure Data Factory.

### Network diagram - after  Private Link for ADF is implemented
After private link is introduced, you can secure communication between ADF IR and ADF control plane using private link.  The below diagram illustrates how it works.  

![Azure Data Factory - network diagram - with private link](https://github.com/caryeun/adfpl/blob/main/media/ADF_PostPrivateLink.png)

What's more - you don’t need to configure the preceding domain and port in a virtual network - which further reduced your risk exposure.

(Note: in addition to the communication between ADF IR and ADF control plan, the above diagram also secure the connections between ADF IR and Azure Storage Account)


## How may I set up Private Link for Azure Data Factory, and ensure no public internet is allowed?

You can configure Private Link for Azure Data Factory via the portal UI.  Below screen capture for quick reference. 
![Azure Data Factory - Private Endpoint](https://docs.microsoft.com/en-us/azure/data-factory/media/data-factory-private-link/create-private-endpoint.png)

You can disable public network access to the data factory.  Below screen capture for quick reference.
![Azure Data Factory - Disable public network access](https://docs.microsoft.com/en-us/azure/data-factory/media/data-factory-private-link/create-private-endpoint.png)


If you would like to test it out in your test environment, this arm tempalte will help deploy a sample setup in your subscription. (link to be provided)


## I am interested to know more.  Where may I get more info?

Azure Data Factory is just 1 of the data services offered on Azure. To learn more about the management, monitoring, security and prviacy of data on Azure, the below learning path for "Azure Data Engineer Associate" shall help.
 Microsoft Certified: Azure Data Engineer Associate
 - https://docs.microsoft.com/en-us/learn/certifications/azure-data-engineer

Private link is among 1 of the security features offered by Azure.  To learn more about the other security features, the below learning path for "Azure Security Engineer Associate" shall give you a more comprehensive overview on Azure Security. 
 Microsoft Certified: Azure Security Engineer Associate
 - https://docs.microsoft.com/en-us/learn/certifications/azure-security-engineer
 
If you are looking for information for security consideration of implementing just Data Factory, refer to the link below:
 Security considerations for data movement in Azure Data Factory
 - https://docs.microsoft.com/en-us/azure/data-factory/data-movement-security-considerations
 
Hope you find this blog post useful!


