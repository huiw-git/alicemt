---
title: Create a Full Database Backup (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 586561fc-dfbb-4842-84f8-204a9100a534
---
# Create a Full Database Backup (SQL Server)
  This topic describes how to create a full database backup in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or PowerShell.  
  
>  For information on SQL Server backup to the Windows Azure Blob storage service, see, [SQL Server Backup and Restore with Microsoft Azure Blob Storage Service](../../Topics\TopicNameNotContainA/SQL-Server-Backup-and-Restore-with-Microsoft-Azure-Blob-Storage-Service.md).  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   The BACKUP statement is not allowed in an explicit or implicit transaction.  
  
-   Backups that are created by more recent version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] cannot be restored in earlier versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
-   For more information, see [Backup Overview &#40;SQL Server&#41;](../Topic/Backup%20Overview%20\(SQL%20Server\).md).  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   As a database increases in size full database backups take more time to finish and require more storage space. Therefore, for a large database, you might want to supplement a full database backup with a series of *differential database backups*. For more information, see [Differential Backups &#40;SQL Server&#41;](../Topic/Differential%20Backups%20\(SQL%20Server\).md).  
  
-   You can estimate the size of a full database backup by using the [sp\_spaceused](../Topic/sp_spaceused%20\(Transact-SQL\).md) system stored procedure.  
  
-   By default, every successful backup operation adds an entry in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] error log and in the system event log. If back up the log very frequently, these success messages accumulate quickly, resulting in huge error logs that can make finding other messages difficult. In such cases you can suppress these log entries by using trace flag 3226 if none of your scripts depend on those entries. For more information, see [Trace Flags &#40;Transact-SQL&#41;](../Topic/Trace%20Flags%20\(Transact-SQL\).md).  
  
###  <a name="Security"></a> Security  
 TRUSTWORTHY is set to OFF on a database backup. For information about how to set TRUSTWORTHY to ON, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md).  
  
 Beginning with [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] the **PASSWORD** and **MEDIAPASSWORD** options are discontinued for creating backups. You can still restore backups created with passwords.  
  
####  <a name="Permissions"></a> Permissions  
 BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db\_owner** and **db\_backupoperator** fixed database roles.  
  
 Ownership and permission problems on the backup device's physical file can interfere with a backup operation. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service runs must have write permissions. However, [sp\_addumpdevice](../Topic/sp_addumpdevice%20\(Transact-SQL\).md), which adds an entry for a backup device in the system tables, does not check file access permissions. Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
>  When you specify a back up task by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], you can generate the corresponding [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] [BACKUP](../Topic/BACKUP%20\(Transact-SQL\).md) script by clicking the **Script** button and selecting a script destination.  
  
#### To back up a database  
  
1.  After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)], in Object Explorer, click the server name to expand the server tree.  
  
2.  Expand **Databases**, and depending on the database, either select a user database or expand **System Databases** and select a system database.  
  
3.  Right\-click the database, point to **Tasks**, and then click **Back Up**. The **Back Up Database** dialog box appears.  
  
4.  In the **Database** list box, verify the database name. You can optionally select a different database from the list.  
  
5.  You can perform a database backup for any recovery model \(**FULL**, **BULK\_LOGGED**, or **SIMPLE**\).  
  
6.  In the **Backup type** list box, select **Full**.  
  
     Note that after creating a full database backup, you can create a differential database backup; for more information, see [Create a Differential Database Backup &#40;SQL Server&#41;](../Topic/Create%20a%20Differential%20Database%20Backup%20\(SQL%20Server\).md).  
  
7.  Optionally, you can select **Copy Only Backup** to create a copy\-only backup. A *copy\-only backup* is a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] backup that is independent of the sequence of conventional [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] backups. For more information, see [Copy-Only Backups &#40;SQL Server&#41;](../Topic/Copy-Only%20Backups%20\(SQL%20Server\).md).  
  
     
  When the **Differential** option is selected, you cannot create a copy\-only backup.  
  
8.  For **Backup component**, click **Database**.  
  
9. Either accept the default backup set name suggested in the **Name** text box, or enter a different name for the backup set.  
  
10. Optionally, in the **Description** text box, enter a description of the backup set.  
  
11. Choose the type of backup destination by clicking **Disk**, **Tape** or **URL**. To select the paths of up to 64 disk or tape drives containing a single media set, click **Add**. The selected paths are displayed in the **Backup to** list box.  
  
     To remove a backup destination, select it and click **Remove**. To view the contents of a backup destination, select it and click **Contents**.  
  
12. To view or select the media options, click **Media Options** in the **Select a page** pane.  
  
13. Select an **Overwrite Media** option, by clicking one of the following:  
  
    -   **Back up to the existing media set**  
  
         For this option, click either **Append to the existing backup set** or **Overwrite all existing backup sets**. For more information, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](../Topic/Media%20Sets,%20Media%20Families,%20and%20Backup%20Sets%20\(SQL%20Server\).md).  
  
         Optionally, select **Check media set name and backup set expiration** to cause the backup operation to verify the date and time at which the media set and backup set expire.  
  
         Optionally, enter a name in the **Media set name** text box. If no name is specified, a media set with a blank name is created. If you specify a media set name, the media \(tape or disk\) is checked to see whether the actual name matches the name you enter here.  
  
        > [!IMPORTANT]  
        >  This option is disabled if you selected **URL** as the backup destination in the **General** page. For more information, see [Back Up Database &#40;Media Options Page&#41;](../Topic/Back%20Up%20Database%20\(Media%20Options%20Page\).md)  
        >   
        >  If you plan to use encryption, do not select this option. If you select this option, the encryption options in the **Backup Options** page will be disabled. Encryption is not supported when appending to the existing backup set.  
  
    -   **Back up to a new media set, and erase all existing backup sets**  
  
         For this option, enter a name in the **New media set name** text box, and, optionally, describe the media set in the **New media set description** text box.  
  
        > [!IMPORTANT]  
        >  This option is disabled if you selected **URL** in the **General** page. These actions are not supported when backing up to Windows Azure storage.  
  
14. In the **Reliability** section, optionally check:  
  
    -   **Verify backup when finished**.  
  
    -   **Perform checksum before writing to media**, and, optionally, **Continue on checksum error**. For information on checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](../Topic/Possible%20Media%20Errors%20During%20Backup%20and%20Restore%20\(SQL%20Server\).md).  
  
15. If you are backing up to a tape drive \(as specified in the **Destination** section of the **General** page\), the **Unload the tape after backup** option is active. Clicking this option activates the **Rewind the tape before unloading** option.  
  
    >   
    >  The options in the **Transaction log** section are inactive unless you are backing up a transaction log \(as specified in the **Backup type** section of the **General** page\).  
  
16. To view or select the backup options, click **Backup Options** in the **Select a page** pane.  
  
17. Specify when the backup set will expire and can be overwritten without explicitly skipping verification of the expiration data:  
  
    -   To have the backup set expire after a specific number of days, click **After** \(the default option\), and enter the number of days after set creation that the set will expire. This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.  
  
         The default value is set in the **Default backup media retention \(in days\)** option of the **Server Properties** dialog box \(Database Settings Page\). To access this, right\-click the server name in Object Explorer and select properties; then select the **Database Settings** page.  
  
    -   To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.  
  
         For more information about backup expiration dates, see [BACKUP &#40;Transact-SQL&#41;](../Topic/BACKUP%20\(Transact-SQL\).md).  
  
18. [!INCLUDE[ssEnterpriseEd10](../../Token\Other/ssEnterpriseEd10_md.md)] and later supports [backup compression](../Topic/Backup%20Compression%20\(SQL%20Server\).md). By default, whether a backup is compressed depends on the value of the **backup\-compression default** server configuration option. However, regardless of the current server\-level default, you can compress a backup by checking **Compress backup**, and you can prevent compression by checking **Do not compress backup**.  
  
     **To view or change the current backup compression default**  
  
    -   [View or Configure the backup compression default Server Configuration Option](../../Topics\TopicNameNotContainA/View-or-Configure-the-backup-compression-default-Server-Configuration-Option.md)  
  
19. Specify whether to use encryption for the backup. Select an encryption algorithm to use for the encryption step, and provide a Certificate or Asymmetric key from a list of existing certificates or asymmetric keys. Encryption is supported in SQL Server 2014 or later. For more details on the Encryption options, see [Back Up Database &#40;Backup Options Page&#41;](../Topic/Back%20Up%20Database%20\(Backup%20Options%20Page\).md).  
  
  
You can use the [Maintenance Plan Wizard](https://msdn.microsoft.com/library/ms191002.aspx) to create database backups.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To create a full database backup  
  
1.  Execute the BACKUP DATABASE statement to create the full database backup, specifying:  
  
    -   The name of the database to back up.  
  
    -   The backup device where the full database backup is written.  
  
     The basic [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] syntax for a full database backup is:  
  
     BACKUP DATABASE *database*  
  
     TO *backup\_device* \[ **,**...*n* \]  
  
     \[ WITH *with\_options* \[ **,**...*o* \] \] ;  
  
    |Option|Description|  
    |------------|-----------------|  
    |*database*|Is the database that is to be backed up.|  
    |*backup\_device* \[ **,**...*n* \]|Specifies a list of from 1 to 64 backup devices to use for the backup operation. You can specify a physical backup device, or you can specify a corresponding logical backup device, if already defined. To specify a physical backup device, use the DISK or TAPE option:<br /><br /> { DISK &#124; TAPE } **\=***physical\_backup\_device\_name*<br /><br /> For more information, see [Backup Devices &#40;SQL Server&#41;](../Topic/Backup%20Devices%20\(SQL%20Server\).md).|  
    |WITH *with\_options* \[ **,**...*o* \]|Optionally, specifies one or more additional options, *o*. For information about some of the basic with options, see step 2.|  
  
2.  Optionally, specify one or more WITH options. A few basic WITH options are described here. For information about all the WITH options, see [BACKUP &#40;Transact-SQL&#41;](../Topic/BACKUP%20\(Transact-SQL\).md).  
  
    -   Basic backup set WITH options:  
  
         { COMPRESSION | NO\_COMPRESSION }  
         In [!INCLUDE[ssEnterpriseEd10](../../Token\Other/ssEnterpriseEd10_md.md)] and later only, specifies whether [backup compression](../Topic/Backup%20Compression%20\(SQL%20Server\).md) is performed on this backup, overriding the server\-level default.  
  
         ENCRYPTION \(ALGORITHM,  SERVER CERTIFICATE |ASYMMETRIC KEY\)  
         In SQL Server 2014 or later only, specify the encryption algorithm to use, and the Certificate or Asymmetric key to use to secure the encryption.  
  
         DESCRIPTION **\=** { **'***text***'** | **@***text\_variable* }  
         Specifies the free\-form text that describes the backup set. The string can have a maximum of 255 characters.  
  
         NAME **\=** { *backup\_set\_name* | **@***backup\_set\_name\_var* }  
         Specifies the name of the backup set. Names can have a maximum of 128 characters. If NAME is not specified, it is blank.  
  
    -   Basic backup set WITH options:  
  
         By default, BACKUP appends the backup to an existing media set, preserving existing backup sets. To explicitly specify this, use the NOINIT option. For information about appending to existing backup sets, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](../Topic/Media%20Sets,%20Media%20Families,%20and%20Backup%20Sets%20\(SQL%20Server\).md).  
  
         Alternatively, to format the backup media, use the FORMAT option:  
  
         FORMAT \[ **,** MEDIANAME**\=** { *media\_name* | **@***media\_name\_variable* } \] \[ **,** MEDIADESCRIPTION **\=** { *text* | **@***text\_variable* } \]  
         Use the FORMAT clause when you are using media for the first time or you want to overwrite all existing data. Optionally, assign the new media a media name and description.  
  
        > [!IMPORTANT]  
        >  Use extreme caution when you are using the FORMAT clause of the BACKUP statement because this destroys any backups that were previously stored on the backup media.  
  
###  <a name="TsqlExample"></a> Examples \(Transact\-SQL\)  
  
#### A. Backing up to a disk device  
 The following example backs up the complete [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] database to disk, by using `FORMAT` to create a new media set.  
  
```tsql  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.Bak'  
   WITH FORMAT,  
      MEDIANAME = 'Z_SQLServerBackups',  
      NAME = 'Full Backup of AdventureWorks2012';  
GO  
```  
  
#### B. Backing up to a tape device  
 The following example backs up the complete [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] database to tape, appending the backup to the previous backups.  
  
```tsql  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
   TO TAPE = '\\.\Tape0'  
   WITH NOINIT,  
      NAME = 'Full Backup of AdventureWorks2012';  
GO  
```  
  
#### C. Backing up to a logical tape device  
 The following example creates a logical backup device for a tape drive. The example then backs up the complete [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] database to that device.  
  
```tsql  
-- Create a logical backup device,   
-- AdventureWorks2012_Bak_Tape, for tape device \\.\tape0.  
USE master;  
GO  
EXEC sp_addumpdevice 'tape', 'AdventureWorks2012_Bak_Tape', '\\.\tape0'; USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
   TO AdventureWorks2012_Bak_Tape  
   WITH FORMAT,  
      MEDIANAME = 'AdventureWorks2012_Bak_Tape',  
      MEDIADESCRIPTION = '\\.\tape0',   
      NAME = 'Full Backup of AdventureWorks2012';  
GO  
```  
  
##  <a name="PowerShellProcedure"></a> Using PowerShell  
  
1.  Use the **Backup\-SqlDatabase** cmdlet. To explicitly indicate that this is a full database backup, specify the **\-BackupAction**  parameter with its default value, **Database**. This parameter is optional for full database backups.  
  
     The following example creates a full database backup of the `MyDB` database to the default backup location of the server instance `Computer\Instance`. Optionally, this example specifies **\-BackupAction Database**.  
  
    ```  
    --Enter this command at the PowerShell command prompt, C:\PS>  
    Backup-SqlDatabase -ServerInstance Computer\Instance -Database MyDB -BackupAction Database  
    ```  
  
 **To set up and use the SQL Server PowerShell provider**  
  
-   [SQL Server PowerShell Provider](../../Topics\TopicNameNotContainA/SQL-Server-PowerShell-Provider.md)  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Back Up a Database \(SQL Server\)](../Topic/Create%20a%20Full%20Database%20Backup%20\(SQL%20Server\).md)  
  
-   [Create a Differential Database Backup &#40;SQL Server&#41;](../Topic/Create%20a%20Differential%20Database%20Backup%20\(SQL%20Server\).md)  
  
-   [Restore a Database Backup Using SSMS](../../Topics\TopicNameContainA/Restore-a-Database-Backup-Using-SSMS.md)  
  
-   [Restore a Database Backup Under the Simple Recovery Model &#40;Transact-SQL&#41;](../Topic/Restore%20a%20Database%20Backup%20Under%20the%20Simple%20Recovery%20Model%20\(Transact-SQL\).md)  
  
-   [Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;](../Topic/Restore%20a%20Database%20to%20the%20Point%20of%20Failure%20Under%20the%20Full%20Recovery%20Model%20\(Transact-SQL\).md)  
  
-   [Restore a Database to a New Location &#40;SQL Server&#41;](../Topic/Restore%20a%20Database%20to%20a%20New%20Location%20\(SQL%20Server\).md)  
  
-   [Use the Maintenance Plan Wizard](../../Topics\TopicNameNotContainA/Use-the-Maintenance-Plan-Wizard.md)  
  
## See Also  
 [Backup Overview &#40;SQL Server&#41;](../Topic/Backup%20Overview%20\(SQL%20Server\).md)   
 [Transaction Log Backups &#40;SQL Server&#41;](../Topic/Transaction%20Log%20Backups%20\(SQL%20Server\).md)   
 [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](../Topic/Media%20Sets,%20Media%20Families,%20and%20Backup%20Sets%20\(SQL%20Server\).md)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](../Topic/sp_addumpdevice%20\(Transact-SQL\).md)   
 [BACKUP &#40;Transact-SQL&#41;](../Topic/BACKUP%20\(Transact-SQL\).md)   
 [Back Up Database &#40;General Page&#41;](../Topic/Back%20Up%20Database%20\(General%20Page\).md)   
 [Back Up Database &#40;Backup Options Page&#41;](../Topic/Back%20Up%20Database%20\(Backup%20Options%20Page\).md)   
 [Differential Backups &#40;SQL Server&#41;](../Topic/Differential%20Backups%20\(SQL%20Server\).md)   
 [Full Database Backups &#40;SQL Server&#41;](../Topic/Full%20Database%20Backups%20\(SQL%20Server\).md)  
  
  