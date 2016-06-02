---
title: Restore a Database Backup Using SSMS
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 24b3311d-5ce0-4581-9a05-5c7c726c7b21
---
# Restore a Database Backup Using SSMS
  This topic explains how to restore a full database backup.    
       
### Important!    
Before you can restore a database under the full or bulk-logged recovery model, you may need to back up the active transaction log (known as [tail of the log](https://msdn.microsoft.com/library/ms179314.aspx). For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](../Topic/Back%20Up%20a%20Transaction%20Log%20\(SQL%20Server\).md).     
    
To restore an encrypted database, you need access to the certificate or asymmetric key used to encrypt that database. Without the certificate or asymmetric key, you cannot restore that database. You must retain the certificate used to encrypt the database encryption key for as long as you need to save the backup. For more information, see [SQL Server Certificates and Asymmetric Keys](../../Topics\TopicNameNotContainA/SQL-Server-Certificates-and-Asymmetric-Keys.md).    
    
If you restore an older version database to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], that database will automatially upgrade to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].   
  
Typically, the database becomes available immediately. However, if a [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] database has full\-text indexes, the upgrade process either imports, resets, or rebuilds the indexes, depending on the setting of the **Full\-Text Upgrade Option** server property. If you set upgrade option to **Import** or **Rebuild**, the full\-text indexes will be unavailable during the upgrade. Depending on the amount of data being indexed, importing can take several hour; rebuilding will take up to ten times longer.     
    
When you set upgrade option to **Import**, if a full\-text catalog is not available, the associated full\-text indexes are rebuilt. For information about viewing or changing the setting of the **Full\-Text Upgrade Option** property, see [Manage and Monitor Full-Text Search for a Server Instance](../../Topics\TopicNameContainA/Manage-and-Monitor-Full-Text-Search-for-a-Server-Instance.md).    

## Examples
    
### A. Restore a full database backup    
    
1.  In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] and then expand that instance.  
    
2.  Right-click **Databases** and select **Restore Database...**    
    
3.  On the **General** page, use the **Source** section to specify the source and location of the backup sets to restore. Select one of the following options:    
    
    -   **Database**    
    
         Select the database to restore from the drop\-down list. The list contains only databases that have been backed up according to the **msdb** backup history.    
    
    > [!NOTE]    
    >  If the backup is taken from a different server, the destination server will not have the backup history information for the specified database. In this case, select **Device** to manually specify the file or device to restore.    
    
    -   **Device**    
    
         Click the browse \(**...**\) button to open the **Select backup devices** dialog box. In the **Backup media type** box, select one of the listed device types. To select one or more devices for the **Backup media** box, click **Add**.    
    
         After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.    
    
         In the **Source: Device: Database** list box, select the name of the database which should be restored.    
    
        > [!NOTE]    
        >  This list is only available when **Device** is selected. Only databases that have backups on the selected device will be available.    
    
         **Backup media**    
         Select the medium for the restore operation: **File**, **Tape**, **URL**or **Backup Device**. The **Tape** option appears only if a tape drive is mounted on the computer, and the **Backup Device** option appears, only if at least one backup device exists.    
    
         **Backup location**    
         View, add, or remove media for the restore operation. The list can contain up to 64 files, tapes, or backup devices.    
    
         **Add**    
         Adds the location of a backup device to the **Backup location** list. Depending on the type of media you select in the **Backup media** field, clicking **Add** opens one of the following dialog boxes.    
    
        |Media type|Dialog box|Description|    
        |----------------|----------------|-----------------|    
        |**File**|**Locate Backup File**|In this dialog box, you can select a local file from the tree or specify a remote file using its fully qualified universal naming convention \(UNC\) name. For more information, see [Backup Devices &#40;SQL Server&#41;](../Topic/Backup%20Devices%20\(SQL%20Server\).md).|    
        |**Device**|**Select Backup Device**|In this dialog box, you can select from a list of the logical backup devices defined on the server instance.|    
        |**Tape**|**Select Backup Tape**|In this dialog box, you can select from a list of the tape drives that are physically connected to the computer running the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].|    
        |**URL**|This launches two dialog boxes. First **Connect to Windows Azure Storage** and then **Locate Backup File in Windows Azure**.|In the **Connect to Windows Azure Storage**  dialog box, Select an existing SQL Credential that stores the Windows Azure storage account name and access key information, or create new SQL Credential by specifying the storage account name and storage access key information. For more information, see [Connect to Microsoft Azure Storage &#40;Restore&#41;](../Topic/Connect%20to%20Microsoft%20Azure%20Storage%20\(Restore\).md).<br /><br /> In the **Locate Backup File** dialog box, you can select a file from the list of containers displayed on the left frame.|    
    
         If the list is full, the **Add** button is unavailable.    
    
         **Remove**    
         Removes one or more selected files, tapes, or logical backup devices.    
    
         **Contents**    
         Displays the media contents of a selected file, tape, or logical backup device.    
    
4.  In the **Destination** section, the **Database** box is automatically populated with the name of the database to be restored. To change the name of the database, enter the new name in the **Database** box.    
    
5.  In the **Restore to** box, leave the default as **To the last backup taken** or click on **Timeline** to access the **Backup Timeline** dialog box to manually select a point in time to stop the recovery action. For more information on designating a specific point in time, see [Backup Timeline](../../Topics\TopicNameNotContainA/Backup-Timeline.md).    
    
6.  In the **Backup sets to restore** grid, select the backups to restore. This grid displays the backups available for the specified location. By default, a recovery plan is suggested. To override the suggested recovery plan, you can change the selections in the grid. Backups that depend on the restoration of an earlier backup are automatically deselected when the earlier backup is deselected. For information about the columns in the **Backup sets to restore** grid, see [Restore Database &#40;General Page&#41;](../Topic/Restore%20Database%20\(General%20Page\).md).    
    
7.  Optionally, click **Files** in the **Select a page** pane to access the **Files** dialog box. From here, you can restore the database to a new location by specifying a new restore destination for each file in the **Restore the database files as** grid. For more information about this grid, see [Restore Database &#40;Files Page&#41;](../Topic/Restore%20Database%20\(Files%20Page\).md).    
    
8. To view or select the advanced options, on the **Options** page, in the **Restore options** panel, you can select any of the following options, if appropriate for your situation:    
    
    1.  **WITH** options \(not required\):    
    
        -   **Overwrite the existing database \(WITH REPLACE\)**    
    
        -   **Preserve the replication settings \(WITH KEEP\_REPLICATION\)**    
    
        -   **Restrict access to the restored database \(WITH RESTRICTED\_USER\)**    
    
    2.  Select an option for the **Recovery state** box. This box determines the state of the database after the restore operation.    
    
        -   **RESTORE WITH RECOVERY** is the default behavior which leaves the database ready for use by rolling back the uncommitted transactions. Additional transaction logs cannot be restored. Select this option if you are restoring all of the necessary backups now.    
    
        -   **RESTORE WITH NORECOVERY** which leaves the database non\-operational, and does not roll back the uncommitted transactions. Additional transaction logs can be restored. The database cannot be used until it is recovered.    
    
        -   **RESTORE WITH STANDBY** which leaves the database in read\-only mode. It undoes uncommitted transactions, but saves the undo actions in a standby file so that recovery effects can be reverted.    
    
    3.  **Take tail\-log backup before restore.** Not all restore scenarios require a tail-log backup.  For more information, see **Scenarios That Require a Tail\-Log Backup** from [Tail\-Log Backups (SQL Server).](Tail-Log%20Backups%20\(SQL%20Server\).md)
    
    4.  Restore operations may fail if there are active connections to the database. Check the **Close existing connections option** to ensure that all active connections between [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] and the database are closed. This check box sets the database to single user mode before performing the restore operations, and sets the database to multi\-user mode when complete.    
    
    5.  Select **Prompt before restoring each backup** if you wish to be prompted between each restore operation. This is not usually necessary unless the database is large and you wish to monitor the status of the restore operation.    
    
     For more information about these restore options, see [Restore Database &#40;Options Page&#41;](../Topic/Restore%20Database%20\(Options%20Page\).md).    
    
9. [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)] 

### B. Restore an earlier disk backup over an existing database    
The following example restores an earlier disk backup of `Sales` and overwrites the existing `Sales` database.

1.  In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] and then expand that instance.  
    
2.  Right-click **Databases** and select **Restore Database...**  

3.	On the **General** page, select **Device** under the **Source** section.

4.	Click the browse \(**...**\) button to open the **Select backup devices** dialog box. Click **Add** and navigate to your backup.  Click **OK** after you have selected your disk backup file\(s\).

5.	Click **OK** to return to the **General** page.

6.	Click **Options** in the **Select a page** pane.

7.	Under the **Restore options** section, check \"**Overwrite the existing database (WITH REPLACE)**\"

    > [!NOTE] 
    > Not checking this option may result in the following error message: \"System.Data.SqlClient.SqlError: The backup set holds a backup of a database other than the existing '`Sales`' database. \(Microsoft.SqlServer.SmoExtended\)\"

8.	Under the **Tail\-log backup** section, uncheck \"**Take tail-log backup before restore**\".

    > [!NOTE] 
    > Not all restore scenarios require a tail-log backup. You do not need a tail-log backup if the recovery point is contained in an earlier log backup. Also, a tail-log backup is unnecessary if you are moving or replacing (overwriting) a database and do not need to restore it to a point of time after its most recent backup.  For more information, see [Tail\-Log Backups (SQL Server)](Tail-Log%20Backups%20\(SQL%20Server\).md).
This option is not available for databases in the SIMPLE recovery model.

9.	Under the **Server connections** section, check \"**Close existing connections to destination database**\".

    > [!NOTE] 
    > Not checking this option may result in the following error message: \"System.Data.SqlClient.SqlError: Exclusive access could not be obtained because the database is in use. \(Microsoft.SqlServer.SmoExtended\)\"
    
10. [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)] 

### C.	Restore an earlier disk backup with a new database name where the original database still exists
The following example restores an earlier disk backup of `Sales` and creates a new database called `SalesTest`.  The original database, `Sales`, still exists on the server.

1.  In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] and then expand that instance.  
    
2.  Right-click **Databases** and select **Restore Database...**  

3.	On the **General** page, select **Device** under the **Source** section.

4.	Click the browse \(**...**\) button to open the **Select backup devices** dialog box. Click **Add** and navigate to your backup.  Click **OK** after you have selected your disk backup file\(s\).

5.	Click **OK** to return to the **General** page.

6.	In the **Destination** section, the **Database** box is automatically populated with the name of the database to be restored.  To change the name of the database, enter the new name in the **Database** box.

7.	Click **Options** in the **Select a page** pane.

8.	Under the **Tail\-log backup** section, uncheck \"**Take tail-log backup before restore**\".

    > [!IMPORTANT] 
    > Not unchecking this option will result in the existing database, `Sales`, to change to the restoring state.

9. [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)] 

    > [!NOTE] 
    > If you receive the following error message: \"System.Data.SqlClient.SqlError: The tail of the log for the database \"`Sales`\" has not been backed up. Use BACKUP LOG WITH NORECOVERY to backup the log if it contains work you do not want to lose. Use the WITH REPLACE or WITH STOPAT clause of the RESTORE statement to just overwrite the contents of the log. (Microsoft.SqlServer.SmoExtended)\".  
Then you likely did not enter the new database name from Step 6, above.  Restore normally prevents accidentally overwriting a database with a different database.  If the database specified in a RESTORE statement already exists on the current server and the specified database family GUID differs from the database family GUID recorded in the backup set, the database is not restored. This is an important safeguard.

### D.	Restore earlier disk backups to a point in time
The following example restores a database to its state as of 1:23:17 PM on May 30, 2016 and shows a restore operation that involves multiple log backups.  The database does not currently exist on the server.

1.  In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] and then expand that instance.  
    
2.  Right-click **Databases** and select **Restore Database...**  

3.	On the **General** page, select **Device** under the **Source** section.

4.	Click the browse \(**...**\) button to open the **Select backup devices** dialog box. Click **Add** and navigate to your full backup and all relevant transaction log backups.  Click **OK** after you have selected your disk backup files.

5.	Click **OK** to return to the **General** page.

6.	In the **Destination** section, click on **Timeline** to access the **Backup Timeline** dialog box to manually select a point in time to stop the recovery action.

7.	Select **Specific date and time**.
8.	Change the **Timeline interval** to **Hour** in the drop down box (optional).
9.	Move the slider to the desired time.

10.	Click **OK** to return to the General page.

11. [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)] 


## See Also    
 [Back Up a Transaction Log &#40;SQL Server&#41;](../Topic/Back%20Up%20a%20Transaction%20Log%20\(SQL%20Server\).md)     
 [Create a Full Database Backup &#40;SQL Server&#41;](../Topic/Create%20a%20Full%20Database%20Backup%20\(SQL%20Server\).md)     
 [Restore a Database to a New Location &#40;SQL Server&#41;](../Topic/Restore%20a%20Database%20to%20a%20New%20Location%20\(SQL%20Server\).md)     
 [Restore a Transaction Log Backup &#40;SQL Server&#41;](../Topic/Restore%20a%20Transaction%20Log%20Backup%20\(SQL%20Server\).md)     
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)     
 [Restore Database &#40;Options Page&#41;](../Topic/Restore%20Database%20\(Options%20Page\).md)     
 [Restore Database &#40;General Page&#41;](../Topic/Restore%20Database%20\(General%20Page\).md)    
    
  