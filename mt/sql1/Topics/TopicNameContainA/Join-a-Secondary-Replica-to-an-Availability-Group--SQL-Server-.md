---
title: "Join a Secondary Replica to an Availability Group (SQL Server)"
ms.custom: na
ms.date: 2016-05-17
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e5bd2489-097a-490e-8ea1-34fe48378ad1
caps.latest.revision: 41
caps.handback.revision: 0
manager: jhubbard
---
# Join a Secondary Replica to an Availability Group (SQL Server)
This topic describes how to join a secondary replica to an Always On availability group by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)]. After a secondary replica is added to an Always On availability group, the secondary replica must be joined to the availability group. The join-replica operation must be performed on the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] that is hosting the secondary replica.  
  
-   **Before you begin:**  
  
     [Prerequisites](#Prerequisites)  
  
     [Security](#Security)  
  
-   **To prepare a secondary database, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   **Follow Up:** [Configure Secondary Databases](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Prerequisites"></a> Prerequisites  
  
-   The primary replica of the availability group must currently be online.  
  
-   You must be connected to the server instance that hosts a secondary replica that has not yet have been joined to the availability group.  
  
-   The local server instance must be able to connect to the database mirroring endpoint of the server instance that is hosting the primary replica.  
  
> [!IMPORTANT]  
>  If any prerequisite is not met, the join operation fails. After a failed join attempt, you might need to connect to the server instance that hosts the primary replica to remove and re-add the secondary replica before you can join it to the availability group. For more information, see [Remove a Secondary Replica from an Availability Group (SQL Server)](../../Topics/TopicNameContainA/Remove-a-Secondary-Replica-from-an-Availability-Group--SQL-Server-.md) and [Add a Secondary Replica to an Availability Group (SQL Server)](../../Topics/TopicNameContainA/Add-a-Secondary-Replica-to-an-Availability-Group--SQL-Server-.md).  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 **To join an availability replica to an availability group**  
  
1.  In Object Explorer, connect to the server instance that hosts the secondary replica, and click the server name to expand the server tree.  
  
2.  Expand the **Always On High Availability** node and the **Availability Groups** node.  
  
3.  Select the availability group of the secondary replica to which you are connected.  
  
4.  Right-click the secondary replica, and click **Join to Availability Group**.  
  
5.  This opens the **Join Replica to Availability Group** dialog box.  
  
6.  To join the secondary replica to the availability group, click **OK**.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
 **To join an availability replica to an availability group**  
  
1.  Connect to the server instance that hosts the secondary replica.  
  
2.  Use the [ALTER AVAILABILITY GROUP](assetId:///f039d0de-ade7-4aaf-8b7b-d207deb3371a) statement, as follows:  
  
     ALTER AVAILABILITY GROUP *group_name* JOIN  
  
     where *group_name* is the name of the availability group.  
  
     The following example, joins the secondary replica to the `MyAG` availability group.  
  
    ```  
    ALTER AVAILABILITY GROUP MyAG JOIN;  
    ```  
  
    > [!NOTE]  
    >  To see this [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statement used in context, see [Create an Availability Group (Transact-SQL)](../../Topics/TopicNameNotContainA/Create-an-Availability-Group--Transact-SQL-.md).  
  
##  <a name="PowerShellProcedure"></a> Using PowerShell  
 **To join an availability replica to an availability group**  
  
 In the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] PowerShell provider:  
  
1.  Change directory (**cd**) to the server instance that hosts the secondary replica.  
  
2.  Join the secondary replica to the availability group by executing the **Join-SqlAvailabilityGroup** cmdlet with the name of the availability group.  
  
     For example, the following command joins a secondary replica hosted by the server instance located at the specified path to the availability group named `MyAg`.  This server instance must host a secondary replica in this availability group.  
  
    ```  
    Join-SqlAvailabilityGroup -Path SQLSERVER:\SQL\SecondaryServer\InstanceName -Name 'MyAg'  
    ```  
  
    > [!NOTE]  
    >  To view the syntax of a cmdlet, use the **Get-Help** cmdlet in the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] PowerShell environment. For more information, see [Get Help SQL Server PowerShell](../../Topics/TopicNameNotContainA/Get-Help-SQL-Server-PowerShell.md).  
  
 **To set up and use the SQL Server PowerShell provider**  
  
-   [SQL Server PowerShell Provider](../../Topics/TopicNameNotContainA/SQL-Server-PowerShell-Provider.md)  
  
##  <a name="FollowUp"></a> Follow Up: Configure Secondary Databases  
 For every database in the availability group, you need a secondary database on the server instance that is hosting the secondary replica. You can configure secondary databases either before or after you join a secondary replica to an availability group, as follows:  
  
1.  Restore recent database and log backups of each primary database onto the server instance that hosts the secondary replica, using RESTORE WITH NORECOVERY for every restore operation. For more information, see [Manually Prepare a Secondary Database for an Availability Group (SQL Server)](../../Topics/TopicNameContainA/Manually-Prepare-a-Secondary-Database-for-an-Availability-Group--SQL-Server-.md).  
  
2.  Join each secondary database to the availability group. For more information, see [Join a Secondary Database to an Availability Group (SQL Server)](../../Topics/TopicNameContainA/Join-a-Secondary-Database-to-an-Availability-Group--SQL-Server-.md).  
  
## See Also  
 [Creation and Configuration of Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Creation-and-Configuration-of-Availability-Groups--SQL-Server-.md)   
 [Overview of Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Overview-of-Always-On-Availability-Groups--SQL-Server-.md)   
 [Troubleshoot Always On Availability Groups Configuration (SQL Server)](../../Topics/TopicNameNotContainA/Troubleshoot-Always-On-Availability-Groups-Configuration--SQL-Server-.md)