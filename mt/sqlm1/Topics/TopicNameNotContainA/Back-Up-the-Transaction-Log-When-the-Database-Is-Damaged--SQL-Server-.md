---
title: Back Up the Transaction Log When the Database Is Damaged (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9b8873cc-df54-4336-ab9b-8f525132c2b0
---
# Back Up the Transaction Log When the Database Is Damaged (SQL Server)
  This topic describes how to back up a transaction log when the database is damaged in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To back up the transaction log when the database is damaged, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   The BACKUP statement is not allowed in an explicit or implicit transaction.  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   For a database that uses either the full or bulk\-logged recovery model, you generally need to back up the tail of the log before beginning to restore the database. You also should back up the tail of the log of the primary database before failing over a log shipping configuration. Restoring the tail\-log backup as the final log backup before recovering the database avoids work loss after a failure. For more information about tail\-log backups, see [Tail-Log Backups &#40;SQL Server&#41;](../Topic/Tail-Log%20Backups%20\(SQL%20Server\).md).  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db\_owner** and **db\_backupoperator** fixed database roles.  
  
 Ownership and permission problems on the backup device's physical file can interfere with a backup operation. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service runs must have write permissions. However, [sp\_addumpdevice](../Topic/sp_addumpdevice%20\(Transact-SQL\).md), which adds an entry for a backup device in the system tables, does not check file access permissions. Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To back up the tail of the transaction log  
  
1.  After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)], in Object Explorer, click the server name to expand the server tree.  
  
2.  Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.  
  
3.  Right\-click the database, point to **Tasks**, and then click **Back Up**. The **Back Up Database** dialog box appears.  
  
4.  In the **Database** list box, verify the database name. You can optionally select a different database from the list.  
  
5.  Verify that the recovery model is either **FULL** or **BULK\_LOGGED**.  
  
6.  In the **Backup type** list box, select **Transaction Log**.  
  
7.  Leave **Copy Only Backup** deselected.  
  
8.  In the **Backup set** area, either accept the default backup set name suggested in the **Name** text box, or enter a different name for the backup set.  
  
9. In the **Description** text box, enter a description for the tail\-log backup.  
  
10. Specify when the backup set will expire:  
  
    -   To have the backup set expire after a specific number of days, click **After** \(the default option\), and enter the number of days after set creation that the set will expire. This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.  
  
         The default value is set in the **Default backup media retention \(in days\)** option of the **Server Properties** dialog box \(**Database Settings** page\). To access this dialog box, right\-click the server name in Object Explorer and select properties; then select the **Database Settings** page.  
  
    -   To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.  
  
11. Choose the type of backup destination by clicking **Disk** or **Tape**. To select the paths of up to 64 disk or tape drives containing a single media set, click **Add**. The selected paths are displayed in the **Backup to** list box.  
  
     To remove a backup destination, select it and click **Remove**. To view the contents of a backup destination, select it and click **Contents**.  
  
12. On the **Options** page, select an **Overwrite Media** option, by clicking one of the following:  
  
    -   **Back up to the existing media set**  
  
         For this option, click either **Append to the existing backup set** or **Overwrite all existing backup sets**.  
  
         Optionally, select **Check media set name and backup set expiration** to cause the backup operation to verify the date and time at which the media set and backup set expire.  
  
         Optionally, enter a name in the **Media set name** text box. If no name is specified, a media set with a blank name is created. If you specify a media set name, the media \(tape or disk\) is checked to see whether the actual name matches the name you enter here.  
  
         If you leave the media name blank and check the box to check it against the media, success will equal the media name on the media also being blank.  
  
    -   **Back up to a new media set, and erase all existing backup sets**  
  
         For this option, enter a name in the **New media set name** text box, and, optionally, describe the media set in the **New media set description** text box.  
  
     For more information about media set options, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](../Topic/Media%20Sets,%20Media%20Families,%20and%20Backup%20Sets%20\(SQL%20Server\).md).  
  
13. In the **Reliability** section, optionally, check:  
  
    -   **Verify backup when finished**.  
  
    -   **Perform checksum before writing to media**.  
  
    -   **Continue on checksum error**  
  
     For information on checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](../Topic/Possible%20Media%20Errors%20During%20Backup%20and%20Restore%20\(SQL%20Server\).md).  
  
14. In the **Transaction log** section, check **Back up the tail of the log, and leave database in the restoring state**.  
  
     This is equivalent to specifying the following [BACKUP](../Topic/BACKUP%20\(Transact-SQL\).md) statement:  
  
     `BACKUP LOG <database_name> TO <backup_device> WITH NORECOVERY`  
  
    > [!IMPORTANT]  
    >  At restore time, the Restore Database dialog box displays the type of a tail\-log backup as **Transaction Log \(Copy Only\)**.  
  
15. If you are backing up to a tape drive \(as specified in the **Destination** section of the **General** page\), the **Unload the tape after backup** option is active. Clicking this option activates the **Rewind the tape before unloading** option.  
  
16. [!INCLUDE[ssEnterpriseEd10](../../Token\Other/ssEnterpriseEd10_md.md)] and later supports [backup compression](../Topic/Backup%20Compression%20\(SQL%20Server\).md). By default, whether a backup is compressed depends on the value of the **backup\-compression default** server configuration option. However, regardless of the current server\-level default, you can compress a backup by checking **Compress backup**, and you can prevent compression by checking **Do not compress backup**.  
  
     **To view the current backup compression default**  
  
    -   [View or Configure the backup compression default Server Configuration Option](../../Topics\TopicNameNotContainA/View-or-Configure-the-backup-compression-default-Server-Configuration-Option.md)  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To create a backup of the currently active transaction log  
  
1.  Execute the BACKUP LOG statement to back up the currently active transaction log, specifying:  
  
    -   The name of the database to which the transaction log to back up belongs.  
  
    -   The backup device where the transaction log backup will be written.  
  
    -   The NO\_TRUNCATE clause.  
  
         This clause allows the active part of the transaction log to be backed up even if the database is inaccessible, provided that the transaction log file is accessible and undamaged.  
  
###  <a name="TsqlExample"></a> Example \(Transact\-SQL\)  
  
> [!NOTE]  
>  This example uses the [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)], which uses the simple recovery model. To permit log backups, before taking a full database backup, the database was set to use the full recovery model. For more information, see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](../Topic/View%20or%20Change%20the%20Recovery%20Model%20of%20a%20Database%20\(SQL%20Server\).md).  
  
 This example backs up the currently active transaction log when a database is damaged and inaccessible, if the transaction log is undamaged and accessible.  
  
```scr  
BACKUP LOG AdventureWorks2012  
   TO MyAdvWorks_FullRM_log1  
   WITH NO_TRUNCATE;  
GO  
```  
  
## See Also  
 [Restore a Transaction Log Backup &#40;SQL Server&#41;](../Topic/Restore%20a%20Transaction%20Log%20Backup%20\(SQL%20Server\).md)   
 [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](../Topic/Restore%20a%20SQL%20Server%20Database%20to%20a%20Point%20in%20Time%20\(Full%20Recovery%20Model\).md)   
 [Back Up Database &#40;Backup Options Page&#41;](../Topic/Back%20Up%20Database%20\(Backup%20Options%20Page\).md)   
 [Back Up Database &#40;General Page&#41;](../Topic/Back%20Up%20Database%20\(General%20Page\).md)   
 [Apply Transaction Log Backups &#40;SQL Server&#41;](../Topic/Apply%20Transaction%20Log%20Backups%20\(SQL%20Server\).md)   
 [BACKUP &#40;Transact-SQL&#41;](../Topic/BACKUP%20\(Transact-SQL\).md)   
 [File Restores &#40;Simple Recovery Model&#41;](../Topic/File%20Restores%20\(Simple%20Recovery%20Model\).md)   
 [File Restores &#40;Full Recovery Model&#41;](../Topic/File%20Restores%20\(Full%20Recovery%20Model\).md)  
  
  