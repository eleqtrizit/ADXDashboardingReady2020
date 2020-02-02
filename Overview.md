
# Task: Visualize data in Azure Data Explorer Dashboards 

Azure Data Explorer’s native dashboarding capability enables you to quickly and easily visualize your Kusto data without leaving the platform. The goal of this task is to familiarize yourself with this capability by creating a dashboard using the data from a sample cluster. 

This task will teach you how to: 
1. Create a sample dashboard with Azure Data Explorer 
2. Add additional tiles by cloning existing tiles 
3. Add tiles by pinning a query to a dashboard 
4. Explore data on existing tiles in a dashboard 
5. Create and use a parameter in a query and the dashboard 

NOTE: This is a “preview” capability and new features are added regularly. Please contact us on the Teams channel if you encounter any bugs or have questions/feedback. 

## Prerequisites 

### KQL 

This task assumes that you have some familiarity with KQL (Kusto Query Language). If not, you can find a quick tutorial [here](https://docs.microsoft.com/en-us/azure/kusto/query/tutorial?pivots=azuredataexplorer). 

### Data Set 

The data set we’ll be working on is the live GitHub event data stream. It contains different operations done on GitHub, such as pushing code, creating an issue, and so on. 

* Data source name: Github 
* Cluster URI: https://demo11.westus.kusto.windows.net/ 
* Database: GitHub

Some statistics about this data set:

* Size: ~6 TB 
* Throughput: ~1000 / sec 
* Total number of Events: ~1.8 Billion (and counting) 
