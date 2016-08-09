---
title: "Remove Defunct Filegroups (SQL Server)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 055f9c6a-5c18-4942-98e7-ec918f0ff975
caps.latest.revision: 28
caps.handback.revision: 0
manager: jhubbard
---
# Remove Defunct Filegroups (SQL Server)
This topic describes how to remove defunct filegroups in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
-   [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To remove defunct filegroups, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   This topic is relevant for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] databases that contain multiple files or filegroups; and, under the simple model, only for read-only filegroups.  
  
-   All files in a filegroup become defunct when an offline filegroup is removed.  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   If an unrestored filegroup will never have to be restored, you can make the filegroup *defunct* by removing it from the database. The defunct filegroup can never be restored to this database, but its metadata remains. After the filegroup is defunct, the database can be restarted, and recovery will make the database consistent across the restored filegroups.  
  
     For example, making a filegroup defunct is an option for resolving deferred transactions that were caused by an offline filegroup that you no longer want in the database. Transactions that were deferred because the filegroup was offline are moved out of the deferred state after the filegroup becomes defunct. For more information, see [Deferred Transactions (SQL Server)](../../Topics/TopicNameNotContainA/Deferred-Transactions--SQL-Server-.md).  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the database.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To remove defunct filegroups  
  
1.  In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)] and then expand that instance.  
  
2.  Expand **Databases**, right-click the database from which to delete the file, and then click **Properties**.  
  
3.  Select the **Files** page.  
  
4.  In the **Database files** grid, select the files to delete, click **Remove**, and then click **OK**.  
  
5.  Select the **Filegroups** page.  
  
6.  In the **Rows** grid, select the filegroup to delete, click **Remove**, and then click **OK**.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To remove defunct filegroups  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. (**Note:** This example assumes that the files and filegroup already exist. To create these objects, see example B in the [ALTER DATABASE File and Filegroup Options](assetId:///1f635762-f7aa-4241-9b7a-b51b22292b07) topic.) The first example removes the `test1dat3` and `test1dat4` files from the defunct filegroup by using the `ALTER DATABASE` statement with the `REMOVE FILE` clause. The second example removes the defunct filegroup `Test1FG1`by using the `REMOVE FILEGROUP` clause.  
  
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
 [ALTER DATABASE File and Filegroup Options (Transact-SQL)](assetId:///1f635762-f7aa-4241-9b7a-b51b22292b07)   
 [Deferred Transactions (SQL Server)](../../Topics/TopicNameNotContainA/Deferred-Transactions--SQL-Server-.md)   
 [File Restores (Full Recovery Model)](../../Topics/TopicNameNotContainA/File-Restores--Full-Recovery-Model-.md)   
 [File Restores (Simple Recovery Model)](../../Topics/TopicNameNotContainA/File-Restores--Simple-Recovery-Model-.md)   
 [Online Restore (SQL Server)](../../Topics/TopicNameNotContainA/Online-Restore--SQL-Server-.md)   
 [Restore Pages (SQL Server)](../../Topics/TopicNameNotContainA/Restore-Pages--SQL-Server-.md)   
 [Piecemeal Restores (SQL Server)](../../Topics/TopicNameNotContainA/Piecemeal-Restores--SQL-Server-.md)