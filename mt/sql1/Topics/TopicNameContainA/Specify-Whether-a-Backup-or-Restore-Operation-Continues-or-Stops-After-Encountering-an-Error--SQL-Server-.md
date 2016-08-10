---
title: "Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error (SQL Server)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 042be17a-b9b0-4629-b6bb-b87a8bc6c316
caps.latest.revision: 27
caps.handback.revision: 0
manager: jhubbard
---
# Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error (SQL Server)
This topic describes how to specify whether a backup or restore operation continues or stops after encountering an error in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To specify whether a backup or restore operation continues after encountering an error, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 BACKUP  
 BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.  
  
 Ownership and permission problems on the backup device's physical file can interfere with a backup operation. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] service runs must have write permissions. However, [sp_addumpdevice](assetId:///c2d2ae49-0808-46d8-8444-db69a69d0ec3), which adds an entry for a backup device in the system tables, does not check file access permissions. Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.  
  
 RESTORE  
 If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE. If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).  
  
 RESTORE permissions are given to roles in which membership information is always readily available to the server. Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To specify whether backup continues or stops after an error is encountered  
  
1.  Follow the steps to [create a database backup](../../Topics/TopicNameContainA/Create-a-Full-Database-Backup--SQL-Server-.md).  
  
2.  On the **Options** page, in the **Reliability** section, click **Perform checksum before writing to media** and **Continue on error**.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
  
#### To specify whether a backup operation continues or stops after encountering an error  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  In the [BACKUP](assetId:///89a4658a-62f1-4289-8982-f072229720a1) statement, specify the CONTINUE_AFTER ERROR option to continue or the STOP_ON_ERROR option to stop. The default behavior is to stop after encountering an error. This example instructs the backup operation to continue despite encountering an error.  
  
```tsql  
BACKUP DATABASE AdventureWorks2012   
 TO DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'  
   WITH CHECKSUM, CONTINUE_AFTER_ERROR;  
GO  
```  
  
#### To specify whether a restore operation continues or stops after encountering an error  
  
1.  Connect to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  In the [RESTORE](assetId:///877ecd57-3f2e-4237-890a-08f16e944ef1) statement, specify the CONTINUE_AFTER ERROR option to continue or the STOP_ON_ERROR option to stop. The default behavior is to stop after encountering an error. This example instructs the restore operation to continue despite encountering an error.  
  
```tsql  
RESTORE DATABASE AdventureWorks2012   
 FROM DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'   
   WITH CHECKSUM, CONTINUE_AFTER_ERROR;  
GO  
```  
  
## See Also  
 [RESTORE FILELISTONLY (Transact-SQL)](assetId:///0b4b4d11-eb9d-4f3e-9629-6c79cec7a81a)   
 [RESTORE HEADERONLY (Transact-SQL)](assetId:///4b88e98c-49c4-4388-ab0e-476cc956977c)   
 [RESTORE LABELONLY (Transact-SQL)](assetId:///7cf0641e-0d55-4ffb-9500-ecd6ede85ae5)   
 [RESTORE VERIFYONLY (Transact-SQL)](assetId:///cba3b6a0-b48e-4c94-812b-5b3cbb408bd6)   
 [BACKUP (Transact-SQL)](assetId:///89a4658a-62f1-4289-8982-f072229720a1)   
 [backupset (Transact-SQL)](assetId:///6ff79bbf-4acf-4f75-926f-38637ca8a943)   
 [RESTORE Arguments (Transact-SQL)](assetId:///4bfe5734-3003-4165-afd4-b1131ea26e2b)   
 [Possible Media Errors During Backup and Restore (SQL Server)](../../Topics/TopicNameNotContainA/Possible-Media-Errors-During-Backup-and-Restore--SQL-Server-.md)   
 [Enable or Disable Backup Checksums During Backup or Restore (SQL Server)](../../Topics/TopicNameNotContainA/Enable-or-Disable-Backup-Checksums-During-Backup-or-Restore--SQL-Server-.md)