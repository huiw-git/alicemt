---
title: "Manage and troubleshoot Stretch Database"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.service: sql-server-stretch-database
ms.suite: na
ms.technology: 
  - dbe-stretch
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6334db3e-9297-44df-8d53-211187a95520
caps.latest.revision: 39
caps.handback.revision: 0
manager: jhubbard
---
# Manage and troubleshoot Stretch Database
To manage and troubleshoot Stretch Database, use the tools and methods described in this topic .  
  
##  <a name="LocalInfo"></a> Get info about local databases and tables enabled for Stretch Database  
 Open the catalog views **sys.databases** and **sys.tables** to see info about Stretch-enabled SQL Server databases and tables. For more info, see [sys.databases (Transact-SQL)](assetId:///46c288c1-3410-4d68-a027-3bbf33239289) and [sys.tables (Transact-SQL)](assetId:///8c42eba1-c19f-4045-ac82-b97a5e994090).  
  
##  <a name="RemoteInfo"></a> Get info about remote databases and tables used by Stretch Database  
 Open the catalog views **sys.remote_data_archive_databases** and **sys.remote_data_archive_tables** to see info about the remote databases and tables in which migrated data is stored. For more info, see [sys.remote_data_archive_databases (Transact-SQL)](assetId:///25bffb0c-9821-40b4-88cf-75f854891a09) and [sys.remote_data_archive_tables (Transact-SQL)](assetId:///765069b7-60fd-414c-875f-3455460b75cd).  
  
## Check the filter predicate applied to a table  
 Open the catalog view **sys.remote_data_archive_tables** and check the value of the **filter_predicate** column. If the value is null, the entire table is eligible to be migrated. For more info, see [sys.remote_data_archive_tables (Transact-SQL)](assetId:///765069b7-60fd-414c-875f-3455460b75cd).  
  
##  <a name="Migration"></a> Check the status of data migration  
 Select **Tasks &#124; Stretch &#124; Monitor** for a database in SQL Server Management Studio to monitor data migration in Stretch Database Monitor. For more info, see [Monitor and troubleshoot data migration (Stretch Database)](../../Topics/TopicNameNotContainA/Monitor-and-troubleshoot-data-migration--Stretch-Database-.md).  
  
 Or, open the dynamic management view **sys.dm_db_rda_migration_status** to see how many batches and rows of data have been migrated.  
  
## Increase Azure performance level for resource-intensive operations such as indexing  
 When you build, rebuild, or reorganize an index on a large table that's configured for Stretch Database, consider increasing the performance level of the corresponding remote database for the duration of the operation.  
  
## Don't change the schema of the remote table  
 Don't change the schema of a remote Azure table that's associated with a SQL Server table configured for Stretch Database. In particular, don't modify the name or the data type of a column. The Stretch Database feature makes various assumptions about the schema of the remote table in relation to the schema of the SQL Server table. If you change the remote schema, Stretch Database stops working for the changed table.  
  
##  <a name="Firewall"></a> Troubleshoot data migration  
 For troubleshooting suggestions, see [Monitor and troubleshoot data migration (Stretch Database)](../../Topics/TopicNameNotContainA/Monitor-and-troubleshoot-data-migration--Stretch-Database-.md).  
  
## Troubleshoot query performance  
 **Queries that include my Stretch-enabled table are slow.**  
 Queries that include Stretch-enabled tables are expected to perform more slowly than they did before the tables were enabled for Stretch. If query performance degrades significantly, review the following possible problems.  
  
-   Is your Azure server in a different geographical region than your SQL Server? Configure your Azure server to be in the same geographical region as your SQL Server to reduce network latency.  
  
-   Your network conditions may have degraded. Contact your network administrator for info about recent issues or outages.  
  
## See Also  
 [Monitor and troubleshoot data migration (Stretch Database)](../../Topics/TopicNameNotContainA/Monitor-and-troubleshoot-data-migration--Stretch-Database-.md)   
 [Backup Stretch-enabled databases (Stretch Database)](../../Topics/TopicNameNotContainA/Backup-Stretch-enabled-databases--Stretch-Database-.md)