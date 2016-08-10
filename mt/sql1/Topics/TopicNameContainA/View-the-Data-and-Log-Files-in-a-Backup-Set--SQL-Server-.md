---
title: "View the Data and Log Files in a Backup Set (SQL Server)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: abb6420c-f809-426e-aeb4-d0a74989cf39
caps.latest.revision: 24
caps.handback.revision: 0
manager: jhubbard
---
# View the Data and Log Files in a Backup Set (SQL Server)
This topic describes how to view the data and log files in a backup set in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To view the data and log files in a backup set, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
 For information about security, see [RESTORE FILELISTONLY (Transact-SQL)](assetId:///0b4b4d11-eb9d-4f3e-9629-6c79cec7a81a)  
  
####  <a name="Permissions"></a> Permissions  
 In [!INCLUDE[ssKatmai](../../Topics/TopicNameContainA/tokens/ssKatmai_md.md)] and later versions, obtaining information about a backup set or backup device requires CREATE DATABASE permission. For more information, see [GRANT Database Permissions (Transact-SQL)](assetId:///499e5ed6-945c-4791-ab45-68dec0b9c289).  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To view the data and log files in a backup set  
  
1.  After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)], in Object Explorer, click the server name to expand the server tree.  
  
2.  Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.  
  
3.  Right-click the database, and then click **Properties**, which opens the **Database Properties** dialog box.  
  
4.  In the **Select a Page** pane, click **Files**.  
  
5.  Look in the **Database files** grid for a list of the data and log files and their properties.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To view the data and log files in a backup set  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Use the [RESTORE FILELISTONLY](assetId:///0b4b4d11-eb9d-4f3e-9629-6c79cec7a81a) statement. This example returns information about the second backup set (`FILE=2`) on the `AdventureWorksBackups` backup device.  
  
```tsql  
USE AdventureWorks2012 ;  
RESTORE FILELISTONLY FROM AdventureWorksBackups   
   WITH FILE=2;  
GO  
```  
  
## See Also  
 [backupfilegroup (Transact-SQL)](assetId:///d26e8fbe-f5c5-4e10-b2bd-0d8e16ea21f9)   
 [backupfile (Transact-SQL)](assetId:///f1a7fc0a-f4b4-47eb-9138-eebf930dc9ac)   
 [backupset (Transact-SQL)](assetId:///6ff79bbf-4acf-4f75-926f-38637ca8a943)   
 [backupmediaset (Transact-SQL)](assetId:///d9c18a93-cab9-4db8-ae09-c6bd8145ab8f)   
 [backupmediafamily (Transact-SQL)](assetId:///ee16de24-3d95-4b2e-a094-78df2514d18a)   
 [Backup Devices (SQL Server)](../../Topics/TopicNameNotContainA/Backup-Devices--SQL-Server-.md)