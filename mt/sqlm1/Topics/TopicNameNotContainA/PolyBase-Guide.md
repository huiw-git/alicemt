---
title: PolyBase Guide
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-polybase
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: b42b7d48-328a-4046-abe9-f73fd83212dc
---
# PolyBase Guide
  PolyBase is a technology that accesses and combines both non\-relational and relational data, all  from within SQL Server.   It allows you to run queries on external data in Hadoop or Azure blob storage.   The queries are optimized to push computation to Hadoop  
  
 By simply using Transact\-SQL \(T\-SQL\) statements, you an import and export data back and forth between relational tables in SQL Server and non\-relational data stored in Hadoop or Azure Blob Storage. You can also query the external data from within a T\-SQL query and join it with relational data.  
  
 To use PolyBase, see [Get started with PolyBase](../../Topics\TopicNameNotContainA/Get-started-with-PolyBase.md).  
  
 ![PolyBase logical](../../Images\Image\ImageNotContaina/PolyBase-logical.png "PolyBase logical")  
  
## Why use PolyBase?  
 To make good decisions, business decision makers need to analyze both relational data and other data that is not structured into tables      —notably Hadoop and other NoSQL technologies. This is difficult to do unless you have a way to transfer data among the different types of data stores. PolyBase bridges this gap by operating on data that is external to SQL Server.  
  
 To keep it simple, PolyBase does not require you to install additional software to your Hadoop or Azure environment.         Querying external data uses the same syntax as querying a database table. This all happens transparently. PolyBase handles all the details behind\-the\-scenes, and no knowledge about Hadoop or Azure is required to use PolyBase successfully..  
  
 PolyBase can:  
  
-   **Query data stored in Hadoop.** Users are storing data in cost\-effective distributed and scalable systems, such as Hadoop. PolyBase makes it easy to query the data by using T\-SQL.  
  
-   **Query data stored in  Azure blob storage.** Azure blob storage is a convenient place to store data for use by Azure services.  PolyBase makes it easy to access the data by using T\-SQL.  
  
-   **Import data from Hadoop or Azure blob storage.** Leverage the speed of Microsoft SQL's columnstore technology and analysis capabilities by importing data from Hadoop or Azure blob storage into relational tables. There is no need for a separate  ETL or import tool.  
  
-   **Export data to Hadoop or Azure blob storage.** Archive data to Hadoop or Azure blob storage to achieve cost\-effective storage and keep it online for easy access.  
  
-   **Integrate with BI tools.** Use PolyBase with Microsoft’s business intelligence and analysis stack, or use any third party tools that is compatible with SQL Server.  
  
## Performance  
  
-   **Push computation to Hadoop.**The query optimizer makes a cost\-based decision to push computation to Hadoop when doing so will improve query performance.  It uses statistics on external tables to make the cost\-based decision.   Pushing computation creates MapReduce jobs and leverages Hadoop's distributed computational resources.  
  
-   **Scale compute resources.** To improve query performance, you can use SQL Server [PolyBase scale-out groups](../../Topics\TopicNameNotContainA/PolyBase-scale-out-groups.md). This enables parallel data transfer between SQL Server instances and Hadoop nodes, and it adds compute resources for operating on the external data.  
  
## PolyBase Guide Topics  
 This guide includes topics to help you use PolyBase efficiently and effectively.  
  
|||  
|-|-|  
|**Topic**|**Description**|  
|[Get started with PolyBase](../../Topics\TopicNameNotContainA/Get-started-with-PolyBase.md)|Basic steps to install and configure PolyBase. This shows how to create external objects that point to data in Hadoop or Azure blob storage, and gives query examples.|  
|[PolyBase Versioned Feature Summary](../../Topics\TopicNameNotContainA/PolyBase-Versioned-Feature-Summary.md)|Describes which  PolyBase features are supported on SQL Server, SQL Database, and SQL Data Warehouse.|  
|[PolyBase scale-out groups](../../Topics\TopicNameNotContainA/PolyBase-scale-out-groups.md)|Scale out parallelism between SQL Server and Hadoop by using SQL Server scale\-out groups.|  
|[PolyBase installation](../../Topics\TopicNameNotContainA/PolyBase-installation.md)|Reference and steps for installing PolyBase with the installation wizard or with a command\-line tool.|  
|[PolyBase configuration](../../Topics\TopicNameNotContainA/PolyBase-configuration.md)|Configure SQL Server settings for PolyBase.  For example, configure computation pushdown and kerberos security.|  
|[PolyBase T-SQL objects](../../Topics\TopicNameNotContainA/PolyBase-T-SQL-objects.md)|Create the T\-SQL objects that PolyBase uses to define and access external data.|  
|[PolyBase Queries](../../Topics\TopicNameNotContainA/PolyBase-Queries.md)|Use T\-SQL statements to query, import, or export external data.|  
|[PolyBase troubleshooting](../../Topics\TopicNameNotContainA/PolyBase-troubleshooting.md)|Techniques to manage PolyBase queries. Use dynamic management views \(DMVs\) to monitor PolyBase queries, and learn to read a PolyBase query plan to find performance bottlenecks.|  
  
  