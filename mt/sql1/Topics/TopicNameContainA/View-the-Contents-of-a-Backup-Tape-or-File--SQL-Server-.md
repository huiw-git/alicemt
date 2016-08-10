---
title: "View the Contents of a Backup Tape or File (SQL Server)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cd6674a2-ca55-4b5a-a971-878ba001821e
caps.latest.revision: 31
caps.handback.revision: 0
manager: jhubbard
---
# View the Contents of a Backup Tape or File (SQL Server)
This topic describes how to view the content of a backup tape or file in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
> [!NOTE]  
>  Support for tape backup devices will be removed in a future version of SQL Server. Avoid using this feature in new development work, and plan to modify applications that currently use this feature.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To view the content of a backup tape or file, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
 For information about security, see [RESTORE HEADERONLY (Transact-SQL)](assetId:///4b88e98c-49c4-4388-ab0e-476cc956977c).  
  
####  <a name="Permissions"></a> Permissions  
 In [!INCLUDE[ssKatmai](../../Topics/TopicNameContainA/tokens/ssKatmai_md.md)] and later versions, obtaining information about a backup set or backup device requires CREATE DATABASE permission. For more information, see [GRANT Database Permissions (Transact-SQL)](assetId:///499e5ed6-945c-4791-ab45-68dec0b9c289).  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To view the content of a backup tape or file  
  
1.  After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)], in Object Explorer, click the server name to expand the server tree.  
  
2.  Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.  
  
3.  Right-click the database you want to backup, point to **Tasks**, and then click **Back Up**. The **Back Up Database** dialog box appears.  
  
4.  In the **Destination** section of the **General** page, click either **Disk** or **Tape**. In the **Back up to** list box, look for the disk file or tape you want.  
  
     If the disk file or tape is not displayed in the list-box, click **Add**. Select a file name or tape drive. To add it to the **Back up to** list-box, click **OK**.  
  
5.  In the **Back up to** list-box, select the path of the disk or tape drive you want to view, and click **Contents**. This opens the **Device Contents** dialog box.  
  
6.  The right-hand pane displays information about the media set and backup sets on the selected tape or file.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To view the content of a backup tape or file  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Use the [RESTORE HEADERONLY](assetId:///4b88e98c-49c4-4388-ab0e-476cc956977c) statement. This example returns information about the file named `AdventureWorks2012-FullBackup.bak`.  
  
```tsql  
USE AdventureWorks2012;  
RESTORE HEADERONLY   
FROM DISK = N'C:\AdventureWorks2012-FullBackup.bak' ;  
GO  
```  
  
## See Also  
 [backupfilegroup (Transact-SQL)](assetId:///d26e8fbe-f5c5-4e10-b2bd-0d8e16ea21f9)   
 [backupfile (Transact-SQL)](assetId:///f1a7fc0a-f4b4-47eb-9138-eebf930dc9ac)   
 [backupset (Transact-SQL)](assetId:///6ff79bbf-4acf-4f75-926f-38637ca8a943)   
 [backupmediaset (Transact-SQL)](assetId:///d9c18a93-cab9-4db8-ae09-c6bd8145ab8f)   
 [backupmediafamily (Transact-SQL)](assetId:///ee16de24-3d95-4b2e-a094-78df2514d18a)   
 [Backup Devices (SQL Server)](../../Topics/TopicNameNotContainA/Backup-Devices--SQL-Server-.md)   
 [Define a Logical Backup Device for a Disk File (SQL Server)](../../Topics/TopicNameContainA/Define-a-Logical-Backup-Device-for-a-Disk-File--SQL-Server-.md)   
 [Define a Logical Backup Device for a Tape Drive (SQL Server)](../../Topics/TopicNameContainA/Define-a-Logical-Backup-Device-for-a-Tape-Drive--SQL-Server-.md)