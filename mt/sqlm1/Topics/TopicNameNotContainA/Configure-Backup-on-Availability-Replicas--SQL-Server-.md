---
title: Configure Backup on Availability Replicas (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 74bc40bb-9f57-44e4-8988-1d69c0585eb6
---
# Configure Backup on Availability Replicas (SQL Server)
  This topic describes how to configure backup on secondary replicas for an Always On availability group by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
> [!NOTE]  
>  For an introduction to backup on secondary replicas, see [Active Secondaries: Backup on Secondary Replicas &#40;Always On Availability Groups&#41;](../Topic/Active%20Secondaries:%20Backup%20on%20Secondary%20Replicas%20\(Always%20On%20Availability%20Groups\).md).  
  
-   **Before you begin:**  
  
     [Prerequisites](#Prerequisites)  
  
     [Security](#Security)  
  
-   **To configure backup on secondary replicas , using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   **Follow Up:**  [After configuring backup on secondary replicas](#FollowUp)  
  
-   [To Obtain Information About Backup Preference Settings](#ForInfoAboutBuPref)  
  
-   [Related Content](#RelatedContent)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Prerequisites"></a> Prerequisites  
 You must be connected to the server instance that hosts the primary replica.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
  
|Task|Permissions|  
|----------|-----------------|  
|To configure backup on secondary replicas when creating an availability group|Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.|  
|To modify an availability group or availability replica|Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.|  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 **To configure backup on secondary replicas**  
  
1.  In Object Explorer, connect to the server instance that hosts the primary replica, and click the server name to expand the server tree.  
  
2.  Expand the **Always On High Availability** node and the **Availability Groups** node.  
  
3.  Click the availability group whose backup preferences you want to configure, and select the **Properties** command.  
  
4.  In the **Availability Group Properties** dialog box, select **Backup Preferences** page.  
  
5.  On the **Where should backups occur?** panel, select the automated backup preference for the availability group, one of:  
  
     **Prefer Secondary**  
     Specifies that backups should occur on a secondary replica except when the primary replica is the only replica online. In that case, the backup should occur on the primary replica. This is the default option.  
  
     **Secondary only**  
     Specifies that backups should never be performed on the primary replica. If the primary replica is the only replica online, the backup should not occur.  
  
     **Primary**  
     Specifies that the backups should always occur on the primary replica. This option is useful if you need backup features, such as creating differential backups, that are not supported when backup is run on a secondary replica.  
  
    > [!IMPORTANT]  
    >  If you plan to use log shipping to prepare any secondary databases for an availability group, set the automated backup preference to **Primary** until all the secondary databases have been prepared and joined to the availability group.  
  
     **Any Replica**  
     Specifies that you prefer that backup jobs ignore the role of the availability replicas when choosing the replica to perform backups. Note backup jobs might evaluate other factors such as backup priority of each availability replica in combination with its operational state and connected state.  
  
    > [!IMPORTANT]  
    >  There is no enforcement of the automated backup preference setting. The interpretation of this preference depends on the logic, if any, that you script into backup jobs for the databases in a given availability group. The automated backup preference setting has no impact on ad\-hoc backups. For more information, see see [Follow Up: After Configuring Backup on Secondary Replicas](#FollowUp) later in this topic.  
  
6.  Use the **Replica backup priorities** grid to change the backup priority of the availability replicas. This grid displays the current backup priority of each server instance that hosts a replica for the availability group. The grid columns are as follows:  
  
     **Server Instance**  
     The name of the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that hosts the availability replica.  
  
     **Backup Priority \(Lowest\=1, Highest\=100\)**  
     Specifies your priority for performing backups on this replica relative to the other replicas in the same availability group. The value is an integer in the range of 0..100. 1 indicates the lowest priority, and 100 indicates the highest priority. If **Backup Priority** \= 1, the availability replica would be chosen for performing backups only if no higher priority availability replicas are currently available.  
  
     **Exclude Replica**  
     Select if you never want this availability replica to be chosen for performing backups. This is useful, for example, for a remote availability replica to which you never want backups to fail over.  
  
7.  To commit your changes, click **OK**.  
  
 **Alternative ways to access the Backup Preferences page**  
  
-   [Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20New%20Availability%20Group%20Dialog%20Box%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Add%20Replica%20to%20Availability%20Group%20Wizard%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20New%20Availability%20Group%20Dialog%20Box%20\(SQL%20Server%20Management%20Studio\).md)  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 **To configure backup on secondary replicas**  
  
1.  Connect to the server instance that hosts the primary replica.  
  
2.  For a new availability group, use the [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../Topic/CREATE%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md) statement. If you are modifying an existing availability group, use the [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../Topic/ALTER%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md) statement.  
  
##  <a name="PowerShellProcedure"></a> Using PowerShell  
 **To configure backup on secondary replicas**  
  
1.  Set default \(**cd**\) to the server instance that hosts the primary replica.  
  
2.  Optionally, configure the backup priority of each availability replica that you are adding or modifying. This priority is used by the server instance that hosts the primary replica to decide which replica should service an automated backup request on a database in the availability group \(the replica with highest priority is chosen\). This priority can be any number between 0 and 100, inclusive. A priority of 0 indicates that the replica should not be considered as a candidate for servicing backup requests.  The default setting is 50.  
  
     When adding an availability replica to an availability group, use the **New\-SqlAvailabilityReplica** cmdlet. When modifying an existing availability replica, use the **Set\-SqlAvailabilityReplica** cmdlet. In either case, specify the **BackupPriority***n* parameter, where *n* is a value from 0 to 100.  
  
     For example, the following command sets the backup priority of the availability replica `MyReplica` to **60**.  
  
    ```  
    Set-SqlAvailabilityReplica -BackupPriority 60 `  
    -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
3.  Optionally, configure the automated backup preference for the availability group that you are creating  or modifying. This preference indicates how a backup job should evaluate the primary replica when choosing where to perform backups. The default setting is to prefer secondary replicas.  
  
     When creating an availability group, use the **New\-SqlAvailabilityGroup** cmdlet. When modifying an existing availability group, use the **Set\-SqlAvailabilityGroup** cmdlet. In either case, specify the **AutomatedBackupPreference** parameter.  
  
     where,  
  
     **Primary**  
     Specifies that the backups should always occur on the primary replica. This option is useful if you need backup features, such as creating differential backups, that are not supported when backup is run on a secondary replica.  
  
    > [!IMPORTANT]  
    >  If you plan to use log shipping to prepare any secondary databases for an availability group, set the automated backup preference to **Primary** until all the secondary databases have been prepared and joined to the availability group.  
  
     **SecondaryOnly**  
     Specifies that backups should never be performed on the primary replica. If the primary replica is the only replica online, the backup should not occur.  
  
     **Secondary**  
     Specifies that backups should occur on a secondary replica except when the primary replica is the only replica online. In that case, the backup should occur on the primary replica. This is the default behavior.  
  
     **None**  
     Specifies that you prefer that backup jobs ignore the role of the availability replicas when choosing the replica to perform backups. Note backup jobs might evaluate other factors such as backup priority of each availability replica in combination with its operational state and  connected state.  
  
    > [!IMPORTANT]  
    >  There is no enforcement of **AutomatedBackupPreference**. The interpretation of this preference depends on the logic, if any, that you script into backup jobs for the databases in a given availability group. The automated backup preference setting has no impact on ad\-hoc backups. For more information, see [Follow Up: After Configuring Backup on Secondary Replicas](#FollowUp) later in this topic.  
  
     For example, the following command sets the **AutomatedBackupPreference** property on the availability group `MyAg` to **SecondaryOnly**. Automated backups of databases in this availability group will never occur on the primary replica, but will be redirected to the secondary replica with the highest backup priority setting.  
  
    ```  
    Set-SqlAvailabilityGroup `  
    -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg `  
    -AutomatedBackupPreference SecondaryOnly  
    ```  
  
> [!NOTE]  
>  To view the syntax of a cmdlet, use the **Get\-Help** cmdlet in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell environment. For more information, see [Get Help SQL Server PowerShell](../../Topics\TopicNameNotContainA/Get-Help-SQL-Server-PowerShell.md).  
  
 **To set up and use the SQL Server PowerShell provider**  
  
-   [SQL Server PowerShell Provider](../../Topics\TopicNameNotContainA/SQL-Server-PowerShell-Provider.md)  
  
-   [Get Help SQL Server PowerShell](../../Topics\TopicNameNotContainA/Get-Help-SQL-Server-PowerShell.md)  
  
##  <a name="FollowUp"></a> Follow Up: After Configuring Backup on Secondary Replicas  
 To take the automated backup preference into account for a given availability group, on each server instance that hosts an availability replica whose backup priority is greater than zero \(\>0\), you need to script backup jobs for the databases in the availability group. To determine whether the current replica is the preferred backup replica, use the [sys.fn\_hadr\_backup\_is\_preferred\_replica](../Topic/sys.fn_hadr_backup_is_preferred_replica%20%20\(Transact-SQL\).md) function in your backup script. If the availability replica that is hosted by the current server instance is the preferred replica for backups, this function returns 1. If not, the function returns 0. By running a simple script on each availability replica that queries this function, you can determine which replica should run a given backup job. For example, a typical snippet of a backup\-job script would look like:  
  
```  
IF (NOT sys.fn_hadr_backup_is_preferred_replica(@DBNAME))  
BEGIN  
      Select ‘This is not the preferred replica, exiting with success’;  
      RETURN 0 – This is a normal, expected condition, so the script returns success  
END  
BACKUP DATABASE @DBNAME TO DISK=<disk>  
   WITH COPY_ONLY;  
```  
  
 Scripting a backup job with this logic enables you to schedule the job to run on every availability replica on the same schedule. Each of these jobs looks at the same data to determine which job should run, so only one of the scheduled job actually proceeds to the backup stage.  In the event of a failover, none of the scripts or jobs needs to be modified. Also, if you reconfigure an availability group to add an availability replica, managing the backup job requires simply copying or scheduling the backup job. If you remove an availability replica, simply delete the backup job from the server instance that hosted that replica.  
  
> [!TIP]  
>  If you use the[Maintenance Plan Wizard](../../Topics\TopicNameNotContainA/Use-the-Maintenance-Plan-Wizard.md)to create a given backup job, the job will automatically include the scripting logic that calls and checks the **sys.fn\_hadr\_backup\_is\_preferred\_replica** function. However, the backup job will not return the “This is not the preferred replica…” message.Be sure to create the job\(s\) for each availability database on every server instance that hosts an availability replica for the availability group.  
  
##  <a name="ForInfoAboutBuPref"></a> To Obtain Information About Backup Preference Settings  
 The following are useful for obtaining information that is relevant for backup on secondary.  
  
|View|Information|Relevant Columns|  
|----------|-----------------|----------------------|  
|[sys.fn\_hadr\_backup\_is\_preferred\_replica](../Topic/sys.fn_hadr_backup_is_preferred_replica%20%20\(Transact-SQL\).md)|Is the current replica the preferred backup replica?|Not applicable.|  
|[sys.availability\_groups](../Topic/sys.availability_groups%20\(Transact-SQL\).md)|Automated backup preference|**automated\_backup\_preference**<br /><br /> **automated\_backup\_preference\_desc**|  
|[sys.availability\_replicas](../Topic/sys.availability_replicas%20\(Transact-SQL\).md)|Backup priority of a given availability replica|**backup\_priority**|  
|[sys.dm\_hadr\_availability\_replica\_states](../Topic/sys.dm_hadr_availability_replica_states%20\(Transact-SQL\).md)|Is replica local to the server instance?<br /><br /> Current role<br /><br /> Operational state<br /><br /> Connected state<br /><br /> Synchronization health of an availability replica|**is\_local**<br /><br /> **role**, **role\_desc**<br /><br /> **operational\_state**, **operational\_state\_desc**<br /><br /> **connected\_state**, **connected\_state\_desc**<br /><br /> **synchronization\_health**, **synchronization\_health\_desc**|  
  
##  <a name="RelatedContent"></a> Related Content  
  
-   [Microsoft SQL Server Always On Solutions Guide for High Availability and Disaster Recovery](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
-   [SQL Server Always On Team Blog: The official SQL Server Always On Team Blog](http://blogs.msdn.com/b/sqlAlways%20On/)  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Active Secondaries: Backup on Secondary Replicas &#40;Always On Availability Groups&#41;](../Topic/Active%20Secondaries:%20Backup%20on%20Secondary%20Replicas%20\(Always%20On%20Availability%20Groups\).md)  
  
  