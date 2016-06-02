---
title: View a Database Snapshot (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 123f19b2-0850-4033-8507-59ebdfb368ee
---
# View a Database Snapshot (SQL Server)
  This topic explains how to view a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database snapshot using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
> [!NOTE]  
>  To create, revert to, or delete a database snapshot, you must use [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 **In This Topic**  
  
-   **To view a database snapshot, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 **To view a database snapshot**  
  
1.  In Object Explorer, connect to the instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] and then expand that instance.  
  
2.  Expand **Databases.**  
  
3.  Expand **Database Snapshots**, and select the snapshot you want to view.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 **To view a database snapshot**  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  To list the database snapshots of the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], query the **source\_database\_id** column of the [sys.databases](../Topic/sys.databases%20\(Transact-SQL\).md) catalog view for non\-NULL values.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Create a Database Snapshot &#40;Transact-SQL&#41;](../Topic/Create%20a%20Database%20Snapshot%20\(Transact-SQL\).md)  
  
-   [Revert a Database to a Database Snapshot](../../Topics\TopicNameContainA/Revert-a-Database-to-a-Database-Snapshot.md)  
  
-   [Drop a Database Snapshot &#40;Transact-SQL&#41;](../Topic/Drop%20a%20Database%20Snapshot%20\(Transact-SQL\).md)  
  
## See Also  
 [Database Snapshots &#40;SQL Server&#41;](../Topic/Database%20Snapshots%20\(SQL%20Server\).md)  
  
  