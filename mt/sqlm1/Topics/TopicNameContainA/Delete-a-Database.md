---
title: Delete a Database
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1fd8c0f5-03e1-449a-af45-b8cacb479d9c
---
# Delete a Database
  This topic describes how to delete a user\-defined database in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Prerequisites](#Prerequisites)  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To delete a database, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
-   **Follow Up:**  [After deleting a database](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   System databases cannot be deleted.  
  
###  <a name="Prerequisites"></a> Prerequisites  
  
-   Delete any database snapshots that exist on the database. For more information, see [Drop a Database Snapshot &#40;Transact-SQL&#41;](../Topic/Drop%20a%20Database%20Snapshot%20\(Transact-SQL\).md).  
  
-   If the database is involved in log shipping, remove log shipping.  
  
-   If the database is published for transactional replication, or published or subscribed to merge replication, remove replication from the database.  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   Consider taking a full backup of the database. A deleted database can be re\-created only by restoring a backup.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 To execute DROP DATABASE, at a minimum, a user must have CONTROL permission on the database.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To delete a database  
  
1.  In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)], and then expand that instance.  
  
2.  Expand **Databases**, right\-click the database to delete, and then click **Delete**.  
  
3.  Confirm the correct database is selected, and then click **OK**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To delete a database  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. The example removes the `Sales` and `NewSales` databases.  
  
```tsql  
USE master ;  
GO  
DROP DATABASE Sales, NewSales ;  
GO  
```  
  
##  <a name="FollowUp"></a> Follow Up: After deleting a database  
 Back up the **master** database. If **master** must be restored, any database that has been deleted since the last backup of **master** will still have references in the system catalog views and may cause error messages to be raised.  
  
## See Also  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../Topic/CREATE%20DATABASE%20\(SQL%20Server%20Transact-SQL\).md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20\(Transact-SQL\).md)  
  
  