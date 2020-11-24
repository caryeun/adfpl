# How to eliminiate Azure Data Factory's public internet exposure using private link

Azure Private Link was made generally available on Feb 2020.  Since then, it made numerous Azure PaaS services more secured.  By eliminating data transfer via the public internet, Azure Private Link help reduce the exposure to cyber security attacks significantly.

Of most PaaS Services, Azure DAta Factory is considered to be 1 of the most important services to be secured. An ADF instance can connect to numerous data sources that might contain sensitive customer information - and the impact of data exposure can be far more serious than any other PaaS service.  Making ADF more secured, therefore, is critical in building a secure data solution on Azure.

In the folloowing sections, we are going to walk through
i) How private link work to make Azure Data Factory more secured; and
ii) Provide sample ARM tempalte for you to provision an ADF environment that makes use of private link; and
iii) Provide best practices and considerations of implementing it in your production environment.





