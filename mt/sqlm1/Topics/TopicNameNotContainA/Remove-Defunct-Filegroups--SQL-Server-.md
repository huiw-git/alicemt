---
title: Remove Defunct Filegroups (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 055f9c6a-5c18-4942-98e7-ec918f0ff975
---
# Remove Defunct Filegroups (SQL Server)
  This topic describes how to remove defunct filegroups in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
-   [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To remove defunct filegroups, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   This topic is relevant for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] databases that contain multiple files or filegroups; and, under the simple model, only for read\-only filegroups.  
  
-   All files in a filegroup become defunct when an offline filegroup is removed.  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   If an unrestored filegroup will never have to be restored, you can make the filegroup *defunct* by removing it from the database. The defunct filegroup can never be restored to this database, but its metadata remains. After the filegroup is defunct, the database can be restarted, and recovery will make the database consistent across the restored filegroups.  
  
     For example, making a filegroup defunct is an option for resolving deferred transactions that were caused by an offline filegroup that you no longer want in the database. Transactions that were deferred because the filegroup was offline are moved out of the deferred state after the filegroup becomes defunct. For more information, see [Deferred Transactions &#40;SQL Server&#41;](../Topic/Deferred%20Transactions%20\(SQL%20Server\).md).  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the database.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To remove defunct filegroups  
  
1.  In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] and then expand that instance.  
  
2.  Expand **Databases**, right\-click the database from which to delete the file, and then click **Properties**.  
  
3.  Select the **Files** page.  
  
4.  In the **Database files** grid, select the files to delete, click **Remove**, and then click **OK**.  
  
5.  Select the **Filegroups** page.  
  
6.  In the **Rows** grid, select the filegroup to delete, click **Remove**, and then click **OK**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To remove defunct filegroups  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. \(**Note:** This example assumes that the files and filegroup already exist. To create these objects, see example B in the [ALTER DATABASE File and Filegroup Options](../Topic/ALTER%20DATABASE%20File%20and%20Filegroup%20Options%20\(Transact-SQL\).md) topic.\) The first example removes the `test1dat3` and `test1dat4` files from the defunct filegroup by using the `ALTER DATABASE` statement with the `REMOVE FILE` clause. The second example removes the defunct filegroup `Test1FG1`by using the `REMOVE FILEGROUP` clause.  
  
```tsql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
REMOVE FILE test1dat3 ;  
ALTER DATABASE AdventureWorks2012  
REMOVE FILE test1dat4 ;  
GO  
  
```  
  
```tsql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
REMOVE FILEGROUP Test1FG1 ;  
GO  
  
```  
  
## See Also  
 [ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20File%20and%20Filegroup%20Options%20\(Transact-SQL\).md)   
 [Deferred Transactions &#40;SQL Server&#41;](../Topic/Deferred%20Transactions%20\(SQL%20Server\).md)   
 [File Restores &#40;Full Recovery Model&#41;](../Topic/File%20Restores%20\(Full%20Recovery%20Model\).md)   
 [File Restores &#40;Simple Recovery Model&#41;](../Topic/File%20Restores%20\(Simple%20Recovery%20Model\).md)   
 [Online Restore &#40;SQL Server&#41;](../Topic/Online%20Restore%20\(SQL%20Server\).md)   
 [Restore Pages &#40;SQL Server&#41;](../Topic/Restore%20Pages%20\(SQL%20Server\).md)   
 [Piecemeal Restores &#40;SQL Server&#41;](../Topic/Piecemeal%20Restores%20\(SQL%20Server\).md)  
  
  