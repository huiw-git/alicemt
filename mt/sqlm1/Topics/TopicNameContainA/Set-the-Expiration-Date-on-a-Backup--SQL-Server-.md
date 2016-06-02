---
title: Set the Expiration Date on a Backup (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 76e814df-6487-4893-9f09-7759f1863a5c
---
# Set the Expiration Date on a Backup (SQL Server)
  This topic describes how to set the expiration date on a backup in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To set the expiration date on a backup, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db\_owner** and **db\_backupoperator** fixed database roles.  
  
 Ownership and permission problems on the backup device's physical file can interfere with a backup operation. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service runs must have write permissions. However, [sp\_addumpdevice](../Topic/sp_addumpdevice%20\(Transact-SQL\).md), which adds an entry for a backup device in the system tables, does not check file access permissions. Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To set the expiration date on a backup  
  
1.  After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)], in Object Explorer, click the server name to expand the server tree.  
  
2.  Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.  
  
3.  Right\-click the database, point to **Tasks**, and then click **Back Up**. The **Back Up Database** dialog box appears.  
  
4.  On the **General** page, for **Backup set will expire**, specify an expiration date to indicate when the backup set can be overwritten by another backup:  
  
    -   To have the backup set expire after a specific number of days, click **After** \(the default option\), and enter the number of days after set creation that the set will expire. This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.  
  
         The default value is set in the **Default backup media retention \(in days\)** option of the **Server Properties** dialog box \(**Database Settings** page\). To access this, right\-click the server name in Object Explorer and select properties; then select the **Database Settings** page.  
  
    -   To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To set the expiration date on a backup  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  In the [BACKUP](../Topic/BACKUP%20\(Transact-SQL\).md) statement, specify either the EXPIREDATE or RETAINDAYS option to determine when the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] can overwrite the backup. If neither option is specified, the expiration date is determined by the [media retention](../../Topics\TopicNameNotContainA/Configure-the-media-retention-Server-Configuration-Option.md) server configuration setting. This example uses the `EXPIREDATE` option to specify an expiration date of June 30, 2015 \(`6/30/2015`\).  
  
```tsql  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
 TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.Bak'  
   WITH EXPIREDATE = '6/30/2015' ;  
GO  
```  
  
## See Also  
 [Create a Full Database Backup &#40;SQL Server&#41;](../Topic/Create%20a%20Full%20Database%20Backup%20\(SQL%20Server\).md)   
 [Back Up Files and Filegroups &#40;SQL Server&#41;](../Topic/Back%20Up%20Files%20and%20Filegroups%20\(SQL%20Server\).md)   
 [Back Up a Transaction Log &#40;SQL Server&#41;](../Topic/Back%20Up%20a%20Transaction%20Log%20\(SQL%20Server\).md)   
 [Create a Differential Database Backup &#40;SQL Server&#41;](../Topic/Create%20a%20Differential%20Database%20Backup%20\(SQL%20Server\).md)  
  
  