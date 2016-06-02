---
title: Perform a Planned Manual Failover of an Availability Group (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 419f655d-3f9a-4e7d-90b9-f0bab47b3178
---
# Perform a Planned Manual Failover of an Availability Group (SQL Server)
  This topic describes how to perform a manual failover without data loss \(a *planned manual failover*\) on an Always On availability group by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. An availability group fails over at the level of an availability replica. A planned manual failover, like any [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] failover, transitions a secondary replica to primary role and, concurrently, transitions the former primary replica to the secondary role.  
  
 A planned manual failover, which is supported only when the primary replica and the target secondary replica are running in synchronous\-commit mode and are currently synchronized, preserves all the data in the secondary databases that are joined to the availability group on the target secondary replica. Once the former primary replica transitions to the secondary role, its databases become secondary databases and begin synchronizing with the new primary databases. After they all transition into the SYNCHRONIZED state, the new secondary replica becomes eligible to serve as the target of a future planned manual failover.  
  
> [!NOTE]  
>  If the secondary and primary replicas are both configured for automatic failover mode, once the secondary replica is synchronized, it can also serve as the target for an automatic failover. For more information, see [Availability Modes &#40;Always On Availability Groups&#41;](../Topic/Availability%20Modes%20\(Always%20On%20Availability%20Groups\).md).  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Prerequisites and Restrictions](#Prerequisites)  
  
     [Security](#Security)  
  
-   **To manually fail over an availability group, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   **Follow Up:**  [After Manually Failing Over an Availability Group](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   A failover command returns as soon as the target secondary replica has accepted the command. However, database recovery occurs asynchronously after the availability group has finished failing over.  
  
-   Cross\-database consistency across databases within the availability group might not be maintained on failover.  
  
    > [!NOTE]  
    >  Support for cross\-database and distributed transactions vary by SQL Server and operating system versions. For more information, see [Cross-Database Transactions and Distributed Transactions for Always On Availability Groups and Database Mirroring &#40;SQL Server&#41;](../Topic/Cross-Database%20Transactions%20and%20Distributed%20Transactions%20for%20Always%20On%20Availability%20Groups%20and%20Database%20Mirroring%20\(SQL%20Server\).md).  
  
###  <a name="Prerequisites"></a> Prerequisites and Restrictions  
  
-   The target secondary replica and the primary replica must both be running in synchronous\-commit availability mode.  
  
-   The target secondary replica must currently be synchronized with the primary replica. This requires that all the secondary databases on this secondary replica must have been joined to the availability group and be synchronized with their corresponding primary databases \(that is, the local secondary databases must be SYNCHRONIZED\).  
  
    > [!TIP]  
    >  To determine the failover readiness of an secondary replica, query the **is\_failover\_ready** column in the [sys.dm\_hadr\_database\_cluster\_states](../Topic/sys.dm_hadr_database_replica_cluster_states%20\(Transact-SQL\).md) dynamic management view, or look at the **Failover Readiness** column of the [Always On Group Dashboard](../Topic/Use%20the%20Always%20On%20Dashboard%20\(SQL%20Server%20Management%20Studio\).md).  
  
-   This task is supported only on the target secondary replica. You must be connected to the server instance that hosts the target secondary replica.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 **To manually fail over an availability group**  
  
1.  In Object Explorer, connect to a server instance that hosts a secondary replica of the availability group that needs to be failed over, and expand the server tree.  
  
2.  Expand the **Always On High Availability** node and the **Availability Groups** node.  
  
3.  Right\-click the availability group to be failed over, and select the **Failover** command.  
  
4.  This launches the Failover Availability Group Wizard. For more information, see [Use the Fail Over Availability Group Wizard &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Fail%20Over%20Availability%20Group%20Wizard%20\(SQL%20Server%20Management%20Studio\).md).  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 **To manually fail over an availability group**  
  
1.  Connect to the server instance that hosts the target secondary replica.  
  
2.  Use the [ALTER AVAILABILITY GROUP](../Topic/ALTER%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md) statement, as follows:  
  
     ALTER AVAILABILITY GROUP *group\_name* FAILOVER  
  
     where *group\_name* is the name of the availability group.  
  
     The following example manually fails over the *MyAg* availability group to the connected secondary replica.  
  
    ```  
    ALTER AVAILABILITY GROUP MyAg FAILOVER;  
    ```  
  
##  <a name="PowerShellProcedure"></a> Using PowerShell  
 **To manually fail over an availability group**  
  
1.  Change directory \(**cd**\) to the server instance that hosts the target secondary replica.  
  
2.  Use the **Switch\-SqlAvailabilityGroup** cmdlet.  
  
    > [!NOTE]  
    >  To view the syntax of a cmdlet, use the **Get\-Help** cmdlet in the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] PowerShell environment. For more information, see [Get Help SQL Server PowerShell](../../Topics\TopicNameNotContainA/Get-Help-SQL-Server-PowerShell.md).  
  
     The following example manually fails over the *MyAg* availability group to the secondary replica with the specified path.  
  
    ```  
    Switch-SqlAvailabilityGroup -Path SQLSERVER:\Sql\SecondaryServer\InstanceName\AvailabilityGroups\MyAg  
    ```  
  
 **To set up and use the SQL Server PowerShell provider**  
  
-   [SQL Server PowerShell Provider](../../Topics\TopicNameNotContainA/SQL-Server-PowerShell-Provider.md)  
  
-   [Get Help SQL Server PowerShell](../../Topics\TopicNameNotContainA/Get-Help-SQL-Server-PowerShell.md)  
  
##  <a name="FollowUp"></a> Follow Up: After Manually Failing Over an Availability Group  
 If you failed over outside of the [!INCLUDE[ssFosAuto](../../Token\Other/ssFosAuto_md.md)] of the availability group, adjust the quorum votes of the WSFC nodes to reflect your new availability group configuration. For more information, see [Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../Topic/Windows%20Server%20Failover%20Clustering%20\(WSFC\)%20with%20SQL%20Server.md).  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Failover and Failover Modes &#40;Always On Availability Groups&#41;](../Topic/Failover%20and%20Failover%20Modes%20\(Always%20On%20Availability%20Groups\).md)   
 [Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;](../Topic/Perform%20a%20Forced%20Manual%20Failover%20of%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
  