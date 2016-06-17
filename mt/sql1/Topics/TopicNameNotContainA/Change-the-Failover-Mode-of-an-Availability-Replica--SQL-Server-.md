---
title: Change the Failover Mode of an Availability Replica (SQL Server)
H1: na
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 619a826f-8e65-48eb-8c34-39497d238279
---
# Change the Failover Mode of an Availability Replica (SQL Server)
  This topic describes how to change the failover mode of an availability replica in an Always On availability group in [!INCLUDE[ssCurrent](../../Token/Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token/Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token/Other/tsql_md.md)], or PowerShell. The failover mode is a replica property that determines the failover mode for replicas that run under synchronous-commit availability mode. For more information, see [Failover and Failover Modes &#40;Always On Availability Groups&#41;](../../Topics/TopicNameNotContainA/Failover-and-Failover-Modes--Always-On-Availability-Groups-.md) and [Availability Modes &#40;Always On Availability Groups&#41;](../../Topics/TopicNameNotContainA/Availability-Modes--Always-On-Availability-Groups-.md).  
  
-   **Before you begin:**  
  
     [Prerequisites and Restrictions](#Prerequisites)  
  
     [Security](#Security)  
  
-   **To change the availability mode of an availability replica, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Prerequisites"></a> Prerequisites and Restrictions  
  
-   This task is supported only on primary replicas. You must be connected to the server instance that hosts the primary replica.  
  
-   SQL Server Failover Cluster Instances (FCIs) do not support automatic failover by availability groups, so any availability replica that is hosted by an FCI can only be configured for manual failover.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 **To change the failover mode of an availability replica**  
  
1.  In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.  
  
2.  Expand the **Always On High Availability** node and the **Availability Groups** node.  
  
3.  Click the availability group whose replica you want to change.  
  
4.  Right-click the replica, and click **Properties**.  
  
5.  In the **Availability Replica Properties** dialog box, use the **Failover mode** drop list to change the failover mode of this replica.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
 **To change the failover mode of an availability replica**  
  
1.  Connect to the server instance that hosts the primary replica.  
  
2.  Use the [ALTER AVAILABILITY GROUP](../Topic/ALTER%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md) statement, as follows:  
  
     ALTER AVAILABILITY GROUP *group_name* MODIFY REPLICA ON '*server_name*'  
  
     WITH ( {  
  
     AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }  
  
     | FAILOVER_MODE = { AUTOMATIC | MANUAL }  
  
     }  )  
  
     where  
  
    -   *group_name* is the name of the availability group.  
  
    -   { '*system_name*[\\*instance_name*]' | '*FCI_network_name*[\\*instance_name*]' }  
  
         Specifies the address of the instance of [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] that hosts the availability replica to be altered. The components of this address are as follows:  
  
         *system_name*  
         Is the NetBIOS name of the computer system on which a stand-alone server instance resides.  
  
         *FCI_network_name*  
         Is the network name that is used to access a [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] failover cluster in which a target server instance is a [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] failover partner (an FCI).  
  
         *instance_name*  
         Is the name of the instance of [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] that hosts the target availability replica. For a default server instance, *instance_name* is optional.  
  
     For more information about these parameters, see [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../Topic/ALTER%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md).  
  
     The following example, entered on the primary replica of the *MyAG* availability group, changes the failover mode to automatic failover on the availability replica that is located on the default server instance on a computer named *COMPUTER01*.  
  
    ```  
    ALTER AVAILABILITY GROUP MyAG MODIFY REPLICA ON 'COMPUTER01' WITH  
       (FAILOVER_MODE = AUTOMATIC);  
    ```  
  
##  <a name="PowerShellProcedure"></a> Using PowerShell  
 **To change the failover mode of an availability replica**  
  
1.  Change directory (**cd**) to the server instance that hosts the primary replica.  
  
2.  Use the **Set-SqlAvailabilityReplica** cmdlet with the **FailoverMode** parameter. When setting a replica to automatic failover, you might need to use the **AvailabilityMode** parameter to change the replica to synchronous-commit availability mode.  
  
     For example, the following command modifies the replica `MyReplica` in the availability group `MyAg` to use synchronous-commit availability mode and to support automatic failover.  
  
    ```  
    Set-SqlAvailabilityReplica -AvailabilityMode "SynchronousCommit" -FailoverMode "Automatic" `   
    -Path SQLSERVER:SqlPrimaryServerInstanceNameAvailabilityGroupsMyAgReplicasMyReplica  
    ```  
  
    > [!NOTE]  
    >  To view the syntax of a cmdlet, use the **Get-Help** cmdlet in the [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] PowerShell environment. For more information, see [Get Help SQL Server PowerShell](../../Topics/TopicNameNotContainA/Get-Help-SQL-Server-PowerShell.md).  
  
 **To set up and use the SQL Server PowerShell provider**  
  
-   [SQL Server PowerShell Provider](../../Topics/TopicNameNotContainA/SQL-Server-PowerShell-Provider.md)  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Overview-of-Always-On-Availability-Groups--SQL-Server-.md)   
 [Availability Modes &#40;Always On Availability Groups&#41;](../../Topics/TopicNameNotContainA/Availability-Modes--Always-On-Availability-Groups-.md)   
 [Failover and Failover Modes &#40;Always On Availability Groups&#41;](../../Topics/TopicNameNotContainA/Failover-and-Failover-Modes--Always-On-Availability-Groups-.md)  
  
  