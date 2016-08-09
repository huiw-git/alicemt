---
title: "Remove the Witness from a Database Mirroring Session (SQL Server)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f3ce7afc-8936-4d35-80ce-d0f8fbc318d3
caps.latest.revision: 40
caps.handback.revision: 0
manager: jhubbard
---
# Remove the Witness from a Database Mirroring Session (SQL Server)
This topic describes how to remove a witness from a database mirroring session in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)]. At any time during a database mirroring session, the database owner can turn off the witness for a database mirroring session.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To Replace remove the witness, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After Removing the Witness](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the database.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To remove the witness  
  
1.  Connect to the principal server instance and, in the **Object Explorer** pane, click the server name to expand the server tree.  
  
2.  Expand **Databases**, and select the database whose witness you want to remove.  
  
3.  Right-click the database, select **Tasks**, and then click **Mirror**. This opens the **Mirroring** page of the **Database Properties** dialog box.  
  
4.  To remove the witness, delete its server network address from the **Witness** field.  
  
    > [!NOTE]  
    >  If you switch from high-safety mode with automatic failover to high-performance mode, the **Witness** field is automatically cleared.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To remove the witness  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] on either partner server instance.  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Issue the following statement:  
  
     [ALTER DATABASE](assetId:///27a032ef-1cf6-4959-8e67-03d28c4b3465) *database_name* SET WITNESS OFF  
  
     where *database_name* is the name of the mirrored database.  
  
     The following example removes the witness from the [!INCLUDE[ssSampleDBobject](../../Topics/TopicNameContainA/tokens/ssSampleDBobject_md.md)] database.  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET WITNESS OFF ;  
    ```  
  
##  <a name="FollowUp"></a> Follow Up: After Removing the Witness  
 Turning off the witness changes the [operating mode](../../Topics/TopicNameNotContainA/Database-Mirroring-Operating-Modes.md)in accordance with the transaction-safety setting:  
  
-   If transaction safety is set to FULL (the default), the session uses high-safety, synchronous mode without automatic failover.  
  
-   If transaction safety is set to OFF, the session operates asynchronously (in high-performance mode) without requiring quorum. Whenever transaction safety is turned off, we strongly recommend also turning the witness off.  
  
> [!TIP]  
>  The transaction safety setting of the database is recorded on each partner in the [sys.database_mirroring](assetId:///480de2b0-2c16-497d-a6a3-bf7f52a7c9a0) catalog view in the **mirroring_safety_level** and **mirroring_safety_level_desc** columns.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Add a Database Mirroring Witness Using Windows Authentication (Transact-SQL)](../../Topics/TopicNameContainA/Add-a-Database-Mirroring-Witness-Using-Windows-Authentication--Transact-SQL-.md)  
  
-   [Add or Replace a Database Mirroring Witness (SQL Server Management Studio)](../../Topics/TopicNameContainA/Add-or-Replace-a-Database-Mirroring-Witness--SQL-Server-Management-Studio-.md)  
  
## See Also  
 [ALTER DATABASE Database Mirroring (Transact-SQL)](assetId:///27a032ef-1cf6-4959-8e67-03d28c4b3465)   
 [Change Transaction Safety in a Database Mirroring Session (Transact-SQL)](../../Topics/TopicNameContainA/Change-Transaction-Safety-in-a-Database-Mirroring-Session--Transact-SQL-.md)   
 [Add a Database Mirroring Witness Using Windows Authentication (Transact-SQL)](../../Topics/TopicNameContainA/Add-a-Database-Mirroring-Witness-Using-Windows-Authentication--Transact-SQL-.md)   
 [Database Mirroring Witness](../../Topics/TopicNameNotContainA/Database-Mirroring-Witness.md)