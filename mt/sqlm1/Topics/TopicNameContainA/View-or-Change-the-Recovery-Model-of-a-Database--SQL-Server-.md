---
title: View or Change the Recovery Model of a Database (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-backup-restore
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 94918d1d-7c10-4be7-bf9f-27e00b003a0f
---
# View or Change the Recovery Model of a Database (SQL Server)
  This topic describes how to view or change the recovery model of a database in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. A *recovery model* is a database property that controls how transactions are logged, whether the transaction log requires \(and allows\) backing up, and what kinds of restore operations are available. Three recovery models exist: simple, full, and bulk\-logged. Typically, a database uses the full recovery model or simple recovery model. A database can be switched to another recovery model at any time. The **model** database sets the default recovery model of new databases.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Recommendations](#Recommendations)  
  
     [Security](#Security)  
  
-   **To view or change the recovery model of a database, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
-   **Follow Up Recommendations:**  [After You Change the Recovery Model](#FollowUp)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   Before switching from the full recovery or bulk\-logged recovery model, back up the transaction log.  
  
-   Point\-in\-time recovery is not possible with bulk\-logged model. Therefore, if you run transactions under the bulk\-logged recovery model that might require a transaction log restore, these transactions could be exposed to data loss. To maximize data recoverability in a disaster\-recovery scenario, we recommend that you switch to the bulk\-logged recovery model only under the following conditions:  
  
    -   Users are currently not allowed in the database.  
  
    -   All modifications made during bulk processing are recoverable without depending on taking a log backup; for example, by re\-running the bulk processes.  
  
     If you satisfy these two conditions, you will not be exposed to any data loss while restoring a transaction log that was backed up under the bulk\-logged recovery model..  
  
> [!NOTE]  
>  If you switch to the full recovery model during a bulk operation, the logging of the bulk operation changes from minimal logging to full logging, and vice versa.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER permission on the database.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To view or change the recovery model  
  
1.  After connecting to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)], in Object Explorer, click the server name to expand the server tree.  
  
2.  Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.  
  
3.  Right\-click the database, and then click **Properties**, which opens the **Database Properties** dialog box.  
  
4.  In the **Select a page** pane, click **Options**.  
  
5.  The current recovery model is displayed in the **Recovery model** list box.  
  
6.  Optionally, to change the recovery model select a different model list. The choices are **Full**, **Bulk\-logged**, or **Simple**.  
  
7.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To view the recovery model  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to query the [sys.databases](../Topic/sys.databases%20\(Transact-SQL\).md) catalog view to learn the recovery model of the **model** database.  
  
```tsql  
SELECT name, recovery_model_desc  
   FROM sys.databases  
      WHERE name = 'model' ;  
GO  
  
```  
  
#### To change the recovery model  
  
1.  Connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
2.  From the Standard bar, click **New Query**.  
  
3.  Copy and paste the following example into the query window and click **Execute**. This example shows how to change the recovery model in the `model` database to `FULL` by using the `SET RECOVERY` option of the [ALTER DATABASE](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md) statement.  
  
```tsql  
USE master ;  
ALTER DATABASE model SET RECOVERY FULL ;  
```  
  
##  <a name="FollowUp"></a> Follow Up Recommendations: After You Change the Recovery Model  
  
-   **After switching between the full and bulk\-logged recovery models**  
  
    -   After completing the bulk operations, immediately switch back to full recovery mode.  
  
    -   After switching from the bulk\-logged recovery model back to the full recovery model, back up the log.  
  
        > [!NOTE]  
        >  Your backup strategy remains the same: continue performing periodic database, log, and differential backups.  
  
-   **After switching from the simple recovery model**  
  
    -   Immediately after switching to the full recovery model or bulk\-logged recovery model, take a full or differential database backup to start the log chain.  
  
        > [!NOTE]  
        >  The switch to the full or bulk\-logged recovery model takes effect only after the first data backup.  
  
    -   Schedule regular log backups, and update your restore plan accordingly.  
  
        > [!IMPORTANT]  
        >  If you do not back up the log frequently enough, the transaction log can expand until it runs out of disk space.  
  
-   **After switching to the simple recovery model**  
  
    -   Discontinue any scheduled jobs for backing up the transaction log.  
  
    -   Ensure periodic database backups are scheduled. Backing up your database is essential both to protect your data and to truncate the inactive portion of the transaction log.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Create a Full Database Backup &#40;SQL Server&#41;](../Topic/Create%20a%20Full%20Database%20Backup%20\(SQL%20Server\).md)  
  
-   [Back Up a Transaction Log &#40;SQL Server&#41;](../Topic/Back%20Up%20a%20Transaction%20Log%20\(SQL%20Server\).md)  
  
-   [Create a Job](../Topic/Create%20a%20Job.md)  
  
-   [Disable or Enable a Job](../Topic/Disable%20or%20Enable%20a%20Job.md)  
  
##  <a name="RelatedContent"></a> Related Content  
  
-   [Database Maintenance Plans](http://msdn.microsoft.com/library/ms187658.aspx) \(in [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] Books Online\)  
  
## See Also  
 [Recovery Models &#40;SQL Server&#41;](../Topic/Recovery%20Models%20\(SQL%20Server\).md)   
 [The Transaction Log &#40;SQL Server&#41;](../Topic/The%20Transaction%20Log%20\(SQL%20Server\).md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20\(Transact-SQL\).md)   
 [sys.databases &#40;Transact-SQL&#41;](../Topic/sys.databases%20\(Transact-SQL\).md)   
 [Recovery Models &#40;SQL Server&#41;](../Topic/Recovery%20Models%20\(SQL%20Server\).md)  
  
  