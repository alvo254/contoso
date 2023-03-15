# Introduction

Completed100 XP

-   1 minute

Relational databases store data in relational tables, but sometimes the structure imposed by this model can be too rigid, and often leads to poor performance unless you spend time implementing detailed tuning. Other models, collectively known as _NoSQL_ databases, exist. These models store data in other structures, such as documents, graphs, key-value stores, and column family stores.

Azure Cosmos DB is a highly scalable cloud database service for NoSQL data.

## Learning objectives

In this module, you'll learn how to:

-   Describe key features and capabilities of Azure Cosmos DB
-   Identify the APIs supported in Azure Cosmos DB
-   Provision and use an Azure Cosmos DB instance

# Describe Azure Cosmos DB

Completed100 XP

-   5 minutes

![Azure Cosmos DB as a store for multiple NoSQL formats](https://learn.microsoft.com/en-us/training/wwl-data-ai/explore-non-relational-data-stores-azure/media/azure-cosmos-db.png)

Azure Cosmos DB supports multiple application programming interfaces (APIs) that enable developers to use the programming semantics of many common kinds of data store to work with data in a Cosmos DB database. The internal data structure is abstracted, enabling developers to use Cosmos DB to store and query data using APIs with which they're already familiar.

 Note

An _API_ is an _Application Programming Interface_. Database management systems (and other software frameworks) provide a set of APIs that developers can use to write programs that need to access data. The APIs vary for different database management systems.

Cosmos DB uses indexes and partitioning to provide fast read and write performance and can scale to massive volumes of data. You can enable multi-region writes, adding the Azure regions of your choice to your Cosmos DB account so that globally distributed users can each work with data in their local replica.

## When to use Cosmos DB

Cosmos DB is a highly scalable database management system. Cosmos DB automatically allocates space in a container for your partitions, and each partition can grow up to 10 GB in size. Indexes are created and maintained automatically. There's virtually no administrative overhead.

Cosmos DB is a foundational service in Azure. Cosmos DB has been used by many of Microsoft's products for mission critical applications at global scale, including Skype, Xbox, Microsoft 365, Azure, and many others. Cosmos DB is highly suitable for the following scenarios:

-   _IoT and telematics_. These systems typically ingest large amounts of data in frequent bursts of activity. Cosmos DB can accept and store this information quickly. The data can then be used by analytics services, such as Azure Machine Learning, Azure HDInsight, and Power BI. Additionally, you can process the data in real-time using Azure Functions that are triggered as data arrives in the database.
    
-   _Retail and marketing_. Microsoft uses Cosmos DB for its own e-commerce platforms that run as part of Windows Store and Xbox Live. It's also used in the retail industry for storing catalog data and for event sourcing in order processing pipelines.
    
-   _Gaming_. The database tier is a crucial component of gaming applications. Modern games perform graphical processing on mobile/console clients, but rely on the cloud to deliver customized and personalized content like in-game stats, social media integration, and high-score leaderboards. Games often require single-millisecond latencies for reads and write to provide an engaging in-game experience. A game database needs to be fast and be able to handle massive spikes in request rates during new game launches and feature updates.
    
-   _Web and mobile applications_. Azure Cosmos DB is commonly used within web and mobile applications, and is well suited for modeling social interactions, integrating with third-party services, and for building rich personalized experiences. The Cosmos DB SDKs can be used to build rich iOS and Android applications using the popular Xamarin framework.
    

For additional information about uses for Cosmos DB, read [Common Azure Cosmos DB use cases](https://learn.microsoft.com/en-us/azure/cosmos-db/use-cases).

# Identify Azure Cosmos DB APIs

Completed100 XP

-   6 minutes

Azure Cosmos DB is Microsoft's fully managed and serverless distributed database for applications of any size or scale, with support for both relational and non-relational workloads. Developers can build and migrate applications fast using their preferred open source database engines, including PostgreSQL, MongoDB, and Apache Cassandra. When you provision a new Cosmos DB instance, you select the database engine that you want to use. The choice of engine depends on many factors including the type of data to be stored, the need to support existing applications, and the skills of the developers who will work with the data store.

## Azure Cosmos DB for NoSQL

Azure Cosmos DB for NoSQL is Microsoft’s native non-relational service for working with the document data model. It manages data in JSON document format, and despite being a NoSQL data storage solution, uses SQL syntax to work with the data.

A SQL query for an Azure Cosmos DB database containing customer data might look similar to this:

SQLCopy

```
SELECT *
FROM customers c
WHERE c.id = "joe@litware.com"
```

The result of this query consists of one or more JSON documents, as shown here:

JSONCopy

```
{
   "id": "joe@litware.com",
   "name": "Joe Jones",
   "address": {
        "street": "1 Main St.",
        "city": "Seattle"
    }
}
```

## Azure Cosmos DB for MongoDB

MongoDB is a popular open source database in which data is stored in Binary JSON (BSON) format. Azure Cosmos DB for MongoDB enables developers to use MongoDB client libraries and code to work with data in Azure Cosmos DB.

MongoDB Query Language (MQL) uses a compact, object-oriented syntax in which developers use _objects_ to call _methods_. For example, the following query uses the **find** method to query the **products** collection in the **db** object:

JavaScriptCopy

```
db.products.find({id: 123})
```

The results of this query consist of JSON documents, similar to this:

JSONCopy

```
{
   "id": 123,
   "name": "Hammer",
   "price": 2.99
}
```

## Azure Cosmos DB for PostgreSQL

Azure Cosmos DB for PostgreSQL is a native PostgreSQL, globally distributed relational database that automatically shards data to help you build highly scalable apps. You can start building apps on a single node server group, the same way you would with PostgreSQL anywhere else. As your app's scalability and performance requirements grow, you can seamlessly scale to multiple nodes by transparently distributing your tables. PostgreSQL is a relational database management system (RDBMS) in which you define relational tables of data, for example you might define a table of products like this:

ProductID

ProductName

Price

123

Hammer

2.99

162

Screwdriver

3.49

You could then query this table to retrieve the name and price of a specific product using SQL like this:

SQLCopy

```
SELECT ProductName, Price 
FROM Products
WHERE ProductID = 123;
```

The results of this query would contain a row for product 123, like this:

ProductName

Price

Hammer

2.99

## Azure Cosmos DB for Table

Azure Cosmos DB for Table is used to work with data in key-value tables, similar to Azure Table Storage. It offers greater scalability and performance than Azure Table Storage. For example, you might define a table named Customers like this:

PartitionKey

RowKey

Name

Email

1

123

Joe Jones

joe@litware.com

1

124

Samir Nadoy

samir@northwind.com

You can then use the Table API through one of the language-specific SDKs to make calls to your service endpoint to retrieve data from the table. For example, the following request returns the row containing the record for _Samir Nadoy_ in the table above:

textCopy

```
https://endpoint/Customers(PartitionKey='1',RowKey='124')
```

## Azure Cosmos DB for Apache Cassandra

Azure Cosmos DB for Apache Cassandra is compatible with Apache Cassandra, which is a popular open source database that uses a column-family storage structure. Column families are tables, similar to those in a relational database, with the exception that it's not mandatory for every row to have the same columns.

For example, you might create an **Employees** table like this:

ID

Name

Manager

1

Sue Smith

2

Ben Chan

Sue Smith

Cassandra supports a syntax based on SQL, so a client application could retrieve the record for _Ben Chan_ like this:

SQLCopy

```
SELECT * FROM Employees WHERE ID = 2
```

## Azure Cosmos DB for Apache Gremlin

Azure Cosmos DB for Apache Gremlin is used with data in a graph structure; in which entities are defined as vertices that form nodes in connected graph. Nodes are connected by edges that represent relationships, like this:

![A graph showing employees and departments and the connections between them](https://learn.microsoft.com/en-us/training/wwl-data-ai/explore-non-relational-data-stores-azure/media/graph.png)

The example in the image shows two kinds of vertex (employee and department) and edges that connect them (employee "Ben" reports to employee "Sue", and both employees work in the "Hardware" department).

Gremlin syntax includes functions to operate on vertices and edges, enabling you to insert, update, delete, and query data in the graph. For example, you could use the following code to add a new employee named _Alice_ that reports to the employee with ID **1** (_Sue_)

Copy

```
g.addV('employee').property('id', '3').property('firstName', 'Alice')
g.V('3').addE('reports to').to(g.V('1'))
```

The following query returns all of the _employee_ vertices, in order of ID.

Copy

```
g.V().hasLabel('employee').order().by('id')
```


