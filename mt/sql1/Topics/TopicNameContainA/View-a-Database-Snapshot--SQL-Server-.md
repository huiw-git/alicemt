---
title: "View a Database Snapshot (SQL Server)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 123f19b2-0850-4033-8507-59ebdfb368ee
caps.latest.revision: 23
manager: jhubbard
---
# View a Database Snapshot (SQL Server)
This topic explains how to view a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] database snapshot using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)].  
  
> [!NOTE]  
>  To create, revert to, or delete a database snapshot, you must use [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
 **In This Topic**  
  
-   **To view a database snapshot, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 **To view a database snapshot**  
  
1.  In Object Explorer, connect to the instance of the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)] and then expand that instance.  
  
2.  Expand **Databases.**  
  
3.  Expand **Database Snapshots**, and select the snapshot you want to view.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
 **To view a database snapshot**  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  To list the database snapshots of the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], query the **source_database_id** column of the [sys.databases](assetId:///46c288c1-3410-4d68-a027-3bbf33239289) catalog view for non-NULL values.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Create a Database Snapshot (Transact-SQL)](../../Topics/TopicNameContainA/Create-a-Database-Snapshot--Transact-SQL-.md)  
  
-   [Revert a Database to a Database Snapshot](../../Topics/TopicNameContainA/Revert-a-Database-to-a-Database-Snapshot.md)  
  
-   [Drop a Database Snapshot (Transact-SQL)](../../Topics/TopicNameContainA/Drop-a-Database-Snapshot--Transact-SQL-.md)  
  
## See Also  
 [Database Snapshots (SQL Server)](../../Topics/TopicNameNotContainA/Database-Snapshots--SQL-Server-.md)