---
title: Remove a Secondary Replica from an Availability Group (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 35ddc8b6-3e7c-4417-9a0a-d4987a09ddf7
---
# Remove a Secondary Replica from an Availability Group (SQL Server)
  This topic describes how to remove a secondary replica from an Always On availability group by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Prerequisites](#Prerequisites)  
  
     [Security](#Security)  
  
-   **To remove a secondary replica, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   **Follow Up:**  [After Removing a Secondary Replica](#PostBestPractices)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   This task is supported only on the primary replica.  
  
-   Only a secondary replica can be removed from an availability group.  
  
###  <a name="Prerequisites"></a> Prerequisites  
  
-   You must be connected to the server instance that hosts the primary replica of the availability group.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 **To remove a secondary replica**  
  
1.  In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.  
  
2.  Expand the **Always On High Availability** node and the **Availability Groups** node.  
  
3.  Select the availability group, and expand the **Availability Replicas** node.  
  
4.  This step depends on whether you want to remove multiple replicas or only one replica, as follows:  
  
    -   To remove multiple replicas, use the **Object Explorer Details** pane to view and select all the replicas that you want to remove. For more information, see [Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Object%20Explorer%20Details%20to%20Monitor%20Availability%20Groups%20\(SQL%20Server%20Management%20Studio\).md).  
  
    -   To remove a single replica, select it in either the **Object Explorer** pane or the **Object Explorer Details** pane.  
  
5.  Right\-click the selected secondary replica or replicas, and select **Remove from Availability Group** in the command menu.  
  
6.  In the **Remove Secondary Replicas from Availability Group** dialog box, to remove all the listed secondary replicas, click **OK**. If you do not want to remove all the listed replicas, click **Cancel**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 **To remove a secondary replica**  
  
1.  Connect to the server instance that hosts the primary replica.  
  
2.  Use the [ALTER AVAILABILITY GROUP](../Topic/ALTER%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md) statement, as follows:  
  
     ALTER AVAILABILITY GROUP *group\_name* REMOVE REPLICA ON '*instance\_name*' \[,...*n*\]  
  
     where *group\_name* is the name of the availability group and *instance\_name* is the server instance where the secondary replica is located.  
  
     The following example removes a secondary replica from the *MyAG* availability group. The target secondary replica is located on a server instance named *HADR\_INSTANCE* on a computer named *COMPUTER02*.  
  
    ```  
    ALTER AVAILABILITY GROUP MyAG REMOVE REPLICA ON 'COMPUTER02\HADR_INSTANCE';  
    ```  
  
##  <a name="PowerShellProcedure"></a> Using PowerShell  
 **To remove a secondary replica**  
  
1.  Change directory \(**cd**\) to the server instance that hosts the primary replica.  
  
2.  Use the **Remove\-SqlAvailabilityReplica** cmdlet.  
  
     For example, the following command removes the availability replica on the server `MyReplica` from the availability group named `MyAg`.  This command must be run on the server instance that hosts the primary replica of the availability group.  
  
    ```  
    Remove-SqlAvailabilityReplica `   
    -Path SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  To view the syntax of a cmdlet, use the **Get\-Help** cmdlet in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell environment. For more information, see [Get Help SQL Server PowerShell](../../Topics\TopicNameNotContainA/Get-Help-SQL-Server-PowerShell.md).  
  
 **To set up and use the SQL Server PowerShell provider**  
  
-   [SQL Server PowerShell Provider](../../Topics\TopicNameNotContainA/SQL-Server-PowerShell-Provider.md)  
  
##  <a name="PostBestPractices"></a> Follow Up: After Removing a Secondary Replica  
 If you specify a replica that is currently unavailable, when the replica comes online, it will discover that it has been removed.  
  
 Removing a replica causes it to stop receiving data. After a secondary replica confirms that it has been removed from the global store, the replica removes the availability group settings from its databases, which remain on the local server instance in the RECOVERING state.  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](../Topic/Add%20a%20Secondary%20Replica%20to%20an%20Availability%20Group%20\(SQL%20Server\).md)   
 [Remove an Availability Group &#40;SQL Server&#41;](../Topic/Remove%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
  