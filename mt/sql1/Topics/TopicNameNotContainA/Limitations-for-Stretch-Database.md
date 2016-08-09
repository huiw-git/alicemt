---
title: "Limitations for Stretch Database"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 2016-05-23
ms.prod: sql-server-2016
ms.reviewer: na
ms.service: sql-server-stretch-database
ms.suite: na
ms.technology: 
  - dbe-stretch
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2b1fbec1-7859-44fc-8417-724fc57a59c0
caps.latest.revision: 26
manager: jhubbard
---
# Limitations for Stretch Database
Learn about blocking issues that you have to resolve before you can enable Stretch Database for certain tables, and about other limitations for Stretch-enabled tables.  
  
##  <a name="Limitations"></a> Blocking issues  
 In [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)], the following items make a table ineligible for Stretch.  
  
 **Table properties**  
 -   More than 1,023 columns  
  
-   More than 998 indexes  
  
-   Tables that contain FILESTREAM data  
  
-   FileTables  
  
-   Replicated tables  
  
     Replication is not aware of the remote tables in Azure used by Stretch Database. As a result, when Stretch migrates a row from SQL Server to Azure, replication sees that row as deleted from the SQL Server table and removes the row from subscribers.  
  
-   Tables that are actively using Change Tracking or Change Data Capture  
  
-   Memory-optimized tables  
  
 **Data types and column properties**  
 -   text, ntext and image  
  
-   timestamp  
  
-   sql_variant  
  
-   XML  
  
-   geometry  
  
-   geography  
  
-   hierarchyid  
  
-   CLR user-defined types (UDTs)  
  
 **Column types**  
 -   COLUMN_SET  
  
-   Computed columns  
  
 **Constraints**  
 -   Check constraints  
  
-   Default constraints  
  
-   Foreign key constraints that reference the table  
  
     In a parent-child relationship (for example, Order and Order_Detail), you can stretch the child table (Order_Detail) but not the parent table (Order).  
  
 **Indexes**  
 -   Full text indexes  
  
-   XML indexes  
  
-   Spatial indexes  
  
-   Indexed views that reference the table  
  
##  <a name="Caveats"></a> Limitations and caveats for Stretch-enabled tables  
 In [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)], Stretch-enabled tables have the following limitations or caveats.  
  
-   Uniqueness is not enforced for UNIQUE constraints and PRIMARY KEY constraints in the Azure table that contains the migrated data from a Stretch-enabled table.  
  
-   You can't UPDATE or DELETE rows in a Stretch-enabled table, or in a view that includes Stretch-enabled tables.  
  
-   You can't INSERT rows into a Stretch-enabled table on a linked server.  
  
-   You can't create an index for a view that includes Stretch-enabled tables.  
  
-   Filters on [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] indexes are not propagated to the remote table.  
  
## See Also  
 [Identify databases and tables for Stretch Database by running Stretch Database Advisor](../../Topics/TopicNameNotContainA/Identify-databases-and-tables-for-Stretch-Database-by-running-Stretch-Database-Advisor.md)   
 [Enable Stretch Database for a database](../../Topics/TopicNameContainA/Enable-Stretch-Database-for-a-database.md)   
 [Enable Stretch Database for a table](../../Topics/TopicNameContainA/Enable-Stretch-Database-for-a-table.md)