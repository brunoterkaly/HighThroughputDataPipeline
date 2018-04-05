### Help Guide to Building a High Throughput Data Pipeline Using CosmosDB

The following guidance is design to help you learn about the pieces that make up a high throughput pipeline.

| Technology | Usage  |
|:-------------------- |:--------------------  |
| Event Hub Queues | A temporary storage area for messages and events  |
| Event Grid | A service for managing routing of all events from any source to any destination.  |
| Redis Cache | Lower web requests and data queries  |
| Spark | The Spark to Azure Cosmos DB connector enables Azure Cosmos DB to act as an input source or output sink for Apache Spark jobs.  |
| Azure Functions | Provide a server-less development experience supporting a robust set of event triggers and data bindings  |
| CosmosDB | The fault-tolerant and globally persistent data store  |
| Change Feed | Used as a persistent, append only log that stores changes in CosmosDB in order  |

## Event Hub Queues

Bursts of data can be ingested by Azure Event Hubs as it offers high throughput data ingestion with low latency. Data can then be loaded into Azure Cosmos DB for adhoc querying.

| Description | Link  |
|:-------------------- |:--------------------  |
| Java client library for Azure Event Hubs  | [https://github.com/Azure/azure-event-hubs-java](https://github.com/Azure/azure-event-hubs-java)  |
| Azure Event Hubs Java samples | [https://github.com/Azure/azure-event-hubs/tree/master/samples/Java](https://github.com/Azure/azure-event-hubs/tree/master/samples/Java)  |
| Microsoft Azure EventHubs Java Event Processor Host library | [http://repo1.maven.org/maven2/com/microsoft/azure/azure-eventhubs-eph/1.0.0/](http://repo1.maven.org/maven2/com/microsoft/azure/azure-eventhubs-eph/1.0.0/)  |
| Create an Event Hubs namespace and an event hub using the Azure portal | [https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-create](https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-create)  |
| Databricks docs for Event Hubs | [https://docs.azuredatabricks.net/spark/latest/structured-streaming/streaming-event-hubs.html](https://docs.azuredatabricks.net/spark/latest/structured-streaming/streaming-event-hubs.html)  |

## Event Grid

A single service for managing routing of all events from any source to any destination. Designed for high availability, consistent performance, and dynamic scale, Event Grid lets you focus on your app logic rather than infrastructure.

An HTTP-based reactive event handling helps you build efficient solutions through intelligent filtering and routing of events.

| Description | Link  |
|:-------------------- |:--------------------  |
| An introduction to Azure Event Grid | [https://docs.microsoft.com/en-us/azure/event-grid/overview](https://docs.microsoft.com/en-us/azure/event-grid/overview)  |
| Azure Event Grid Documentation | [https://docs.microsoft.com/en-us/azure/event-grid/](https://docs.microsoft.com/en-us/azure/event-grid/)  |
| Storing Event Grid data in CosmosDB | [https://docdb.info/storing-event-grid-messages-in-cosmos-db/](https://docdb.info/storing-event-grid-messages-in-cosmos-db/)  |

## Redis Cache

| Description | Link  |
|:-------------------- |:--------------------  |
| Redis Cache Offerings | [https://azure.microsoft.com/en-us/services/cache/](https://azure.microsoft.com/en-us/services/cache/)  |
| Java API for Redis Cache | [https://docs.microsoft.com/en-us/java/api/com.microsoft.azure.management.redis._redis_cache](https://docs.microsoft.com/en-us/java/api/com.microsoft.azure.management.redis._redis_cache)  |
| Caching Guidance (Private vs Shared) | [https://docs.microsoft.com/en-us/azure/architecture/best-practices/caching#considerations-for-using-caching](https://docs.microsoft.com/en-us/azure/architecture/best-practices/caching#considerations-for-using-caching)  |

## Spark

#### There are two ways to run Spark

+ batch or
+ interactive

##### Batch
As batch you will use spark-submit with the python script you have in pycharm. Add the pyspark package to the pythonpath to have code completion in pycharm.

##### Interactive
For interactive use, it might be a good idea to combine jupyter notebook together with pycharm. In pycharm create classes and methods like any python project. In jupyter notebook load the classes with %run magic or import, and use them interactively from the jupyter notebook. You have to setup jupyter notebook to run with spark, there are many online tutorials for it. I run spark on a hadoop cluster, so my setup might differ from what you need.

#### Here's how you do it:

	01 - Go to File > Preferences > Project: [Project Name] > Project Structure
	02 - Click 'Add Content Root'
	03 - Add <SPARK_PATH>/python
	04 - Click 'Add Content Root'
	05 - Add <SPARK_PATH>/python/lib/py4j-[version]-src.zip
	06 - Go to Run > Edit Configurations... > Defaults > Python > Environment Variables
	07 - Add name: "SPARK_HOME", value: <SPARK_PATH>
	08 - Click OK
	09 - Click Apply

| Description | Link  |
|:-------------------- |:--------------------  |
| Spark SQL, DataFrames and Datasets Guide | [https://spark.apache.org/docs/latest/sql-programming-guide.html](https://spark.apache.org/docs/latest/sql-programming-guide.html)  |
| Spark Connector for #CosmosDB - seamless interaction with globally-distributed, multi-model data | [https://azure.microsoft.com/en-us/blog/spark-connector-for-cosmosdb-seamless-interaction-with-globally-distributed-multi-model-data/](https://azure.microsoft.com/en-us/blog/spark-connector-for-cosmosdb-seamless-interaction-with-globally-distributed-multi-model-data/)  |
| How use the Azure Cosmos DB Spark Connector, Create and attach libraries, Example Notebook | [https://docs.databricks.com/spark/latest/data-sources/azure/cosmosdb-connector.html](https://docs.databricks.com/spark/latest/data-sources/azure/cosmosdb-connector.html)  |
| Azure Databricks | [https://docs.azuredatabricks.net/](https://docs.azuredatabricks.net/)  |
| Work with Spark Dataframes | [https://docs.azuredatabricks.net/spark/latest/dataframes-datasets/index.html](https://docs.azuredatabricks.net/spark/latest/dataframes-datasets/index.html)  |
| Query Sql Server From Spark - Links 1 | [https://stephanefrechette.com/connect-sql-server-using-apache-spark/#.WsKvNpdlAUE](https://stephanefrechette.com/connect-sql-server-using-apache-spark/#.WsKvNpdlAUE)  |
| Apache Spark - Mix SQL Queries with Spark Programs | [https://spark.apache.org/sql/](https://spark.apache.org/sql/)  |

## Azure Functions

| Description | Link  |
|:-------------------- |:--------------------  |
| Store unstructured data using Azure Functions and Azure Cosmos DB | [https://docs.microsoft.com/en-us/azure/azure-functions/functions-integrate-store-unstructured-data-cosmosdb](https://docs.microsoft.com/en-us/azure/azure-functions/functions-integrate-store-unstructured-data-cosmosdb)  |
