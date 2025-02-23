# Split of Data

[prev](./dataoperations.md) | [home](./introduction.md)  | [next](./splitofdata2.md)

This module focusses on certain database scenarios which should help you narrow down your options for storing data. Often neglected these are few important concepts one must consider before creating pipelines

## Transactional Data

This is the day to day data that gets generated through transactions.Common scenarios here are
> Note:Sizing limit may vary or increase with time.

### 1) OLTP

The management of transactional data using computer systems is referred to as online transaction processing (OLTP). OLTP systems record business interactions as they occur in the day-to-day operation of the organization, and support querying of this data to make inferences.These systems are optimized for dealing with discrete system or user requests immediately and responding as quickly as possible. They can handle a few GB to 16(OSS) and 100TB(SQL) volume of data </br>

#### When to use OLTP solution

* Choose OLTP when you need to efficiently process and store business transactions and immediately make them available to client applications in a consistent way. Use this architecture when any tangible delay in processing would have a negative impact on the day-to-day operations of the business.

![OLTP](/images/OLTP.png)

## Historical Data

This is data you don't generate every day. Its accumulated over a period of time and mostly used for reports that involve aggregation of various subsets of this data for meaningful insights. Common scenarios here are

### 2) OLAP systems

These are optimized for the analytical processing, ingesting, synthesizing, and managing large sets of historical data. The data processed by OLAP systems largely originates from OLTP systems and needs to be loaded into the OLAP systems by **ETL (Extract, Transform, and Load)** batch processes.</br>

#### When to use OLAP solution

* Consider OLAP when there is a need to execute complex analytical and ad hoc queries rapidly over large amount of data, without negatively affecting your OLTP systems over structural data
* OLAP systems are optimized for read-heavy scenarios, such as analytics and business intelligence where users are required to segment multi-dimensional data into slices that can be viewed in two dimensions (such as a pivot table) or filter the data by specific values.

### 3) Modern Data Warehouse

A conventional data warehousing (OLAP systems) solution typically involves copying data from transactional data stores into a relational database with a schema that's optimized for querying and building multidimensional models. A modern data warehouse also lets you ingest data from multiple sources of different types, including structured, semi-structured, unstructured and/or streaming data with capabilities like scalability and in-built dashboards. Before storing data is cleansed **(ETL- Extract, Transform, and Load)** to reduce the overhead of space and compute for processing this data when called.This can handle up to 1PB of data.

#### When to use Data Warehouse solution

* Choose a data warehouse when you need to turn massive amounts of data from operational systems into a format that is easy to understand. 
* Preferred when you need to keep historical data separate from the source transaction systems for performance reasons.
* Data warehouses don't need to follow the same terse data structure you may be using in your OLTP databases. You can use column names that make sense to business users and analysts, restructure the schema to simplify relationships, and consolidate several tables into one.

![Data Warehouse](/images/DataWarehouse.png)

### 4) Data Mart

This is a specialized subset of data warehouse, designed to handle business and reporting needs to a specific unit or department within an organization. For example if you are in the retail industry you have a data warehouse that stores records of all your stores, inventory, sales, marketing, online transactions, etc. For specifically catering to the needs of marketing unit you may choose to have a data mart instead. Given its nature of specialization it may have fewer sources of data ingestion and likewise lesser volume of data than a data warehouse. This helps with faster aggregation on data and more structural focus on summarizing data. Majority of the time they are project-focused with limited or oriented and focussed usage.Datamarts provide a simple and optionally no-code experience to ingest data from different data sources, **Extract Transform and Load (ETL)** the data using Power Query, then load it into an Azure SQL database that's fully managed and requires no tuning or optimization. They can handle up to 100GB of data. 

#### When to use Data Mart solution

* Choose a data mart when you need to turn moderate volume of data from operational systems into a format that is easy to understand for a particular business unit or department.
* Datamarts are good options where auto generated datasets are viable for generating reports.It works well for relational database analytics with Power BI.
* No-code experience is preferred over emphasis on a particular structure and schema. Minimizing orchestration and administration cost in developing dataflow and pipelines is key advantage of such solution

![Data Mart](/images/DataMarts.png)

The heirarchy is summarized as follows

![Data Hierarchy](/images/DataHeirarchyOLTPtoOLAP.png)

In the next page we shall see the change in trend from **ETL to ELT** with the advent of Big Data

## Additional Information

* [Important data engineering concepts](https://learn.microsoft.com/training/modules/introduction-to-data-engineering-azure/4-common-patterns-azure-data-engineering)
* [OLTP](https://learn.microsoft.com/azure/architecture/data-guide/relational-data/online-transaction-processing)
* [OLAP](https://learn.microsoft.com/azure/architecture/data-guide/relational-data/online-analytical-processing)
* [Data Warehousing](https://learn.microsoft.com/azure/architecture/data-guide/relational-data/data-warehousing)
* [Data Marts](https://learn.microsoft.com/power-bi/transform-model/datamarts/datamarts-overview)
* [Big Data Characteristics](https://www.teradata.com/Glossary/What-are-the-5-V-s-of-Big-Data#:~:text=Big%20data%20is%20a%20collection,variety%2C%20velocity%2C%20and%20veracity)
