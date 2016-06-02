---
title: Remove the Witness from a Database Mirroring Session (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f3ce7afc-8936-4d35-80ce-d0f8fbc318d3
---
# Remove the Witness from a Database Mirroring Session (SQL Server)
  This topic describes how to remove a witness from a database mirroring session in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. At any time during a database mirroring session, the database owner can turn off the witness for a database mirroring session.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To Replace remove the witness, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After Removing the Witness](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the database.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To remove the witness  
  
1.  Connect to the principal server instance and, in the **Object Explorer** pane, click the server name to expand the server tree.  
  
2.  Expand **Databases**, and select the database whose witness you want to remove.  
  
3.  Right\-click the database, select **Tasks**, and then click **Mirror**. This opens the **Mirroring** page of the **Database Properties** dialog box.  
  
4.  To remove the witness, delete its server network address from the **Witness** field.  
  
    > [!NOTE]  
    >  If you switch from high\-safety mode with automatic failover to high\-performance mode, the **Witness** field is automatically cleared.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To remove the witness  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] on either partner server instance.  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Issue the following statement:  
  
     [ALTER DATABASE](../Topic/ALTER%20DATABASE%20Database%20Mirroring%20\(Transact-SQL\).md) *database\_name* SET WITNESS OFF  
  
     where *database\_name* is the name of the mirrored database.  
  
     The following example removes the witness from the [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] database.  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET WITNESS OFF ;  
    ```  
  
##  <a name="FollowUp"></a> Follow Up: After Removing the Witness  
 Turning off the witness changes the [operating mode](../../Topics\TopicNameNotContainA/Database-Mirroring-Operating-Modes.md)in accordance with the transaction\-safety setting:  
  
-   If transaction safety is set to FULL \(the default\), the session uses high\-safety, synchronous mode without automatic failover.  
  
-   If transaction safety is set to OFF, the session operates asynchronously \(in high\-performance mode\) without requiring quorum. Whenever transaction safety is turned off, we strongly recommend also turning the witness off.  
  
> [!TIP]  
>  The transaction safety setting of the database is recorded on each partner in the [sys.database\_mirroring](../Topic/sys.database_mirroring%20\(Transact-SQL\).md) catalog view in the **mirroring\_safety\_level** and **mirroring\_safety\_level\_desc** columns.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;](../Topic/Add%20a%20Database%20Mirroring%20Witness%20Using%20Windows%20Authentication%20\(Transact-SQL\).md)  
  
-   [Add or Replace a Database Mirroring Witness &#40;SQL Server Management Studio&#41;](../Topic/Add%20or%20Replace%20a%20Database%20Mirroring%20Witness%20\(SQL%20Server%20Management%20Studio\).md)  
  
## See Also  
 [ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20Database%20Mirroring%20\(Transact-SQL\).md)   
 [Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;](../Topic/Change%20Transaction%20Safety%20in%20a%20Database%20Mirroring%20Session%20\(Transact-SQL\).md)   
 [Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;](../Topic/Add%20a%20Database%20Mirroring%20Witness%20Using%20Windows%20Authentication%20\(Transact-SQL\).md)   
 [Database Mirroring Witness](../../Topics\TopicNameNotContainA/Database-Mirroring-Witness.md)  
  
  