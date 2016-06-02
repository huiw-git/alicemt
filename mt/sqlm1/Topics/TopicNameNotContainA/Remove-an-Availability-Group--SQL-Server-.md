---
title: Remove an Availability Group (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4b7f7f62-43a3-49db-a72e-22d4d7c2ddbb
---
# Remove an Availability Group (SQL Server)
  This topic describes how to delete \(drop\) an Always On availability group by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. If a server instance that hosts one of the availability replicas is offline when you delete an availability group, after coming online, the server instance will drop the local availability replica. Dropping an availability group deletes any associated availability group listener.  
  
 Note that, if necessary, you can drop an availability group from any Windows Server Failover Clustering \(WSFC\) node that possesses the correct security credentials for the availability group. This enables you to delete an availability group when none of its availability replicas remain.  
  
> [!IMPORTANT]  
>  If possible, remove the availability group only while connected to the server instance that hosts the primary replica. When the availability group is dropped from the primary replica, changes are allowed in the former primary databases \(without high availability protection\). Deleting an availability group from a secondary replica leaves the primary replica in the RESTORING state, and changes are not allowed on the databases.  
  
-   **Before you begin:**  
  
     [Limitations and Recommendations](#Restrictions)  
  
     [Security](#Security)  
  
-   **To delete an availability group, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   [Related Content](#RelatedContent)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Recommendations  
  
-   When the availability group is online, deleting it from a secondary replica causes the primary replica to transition to the RESTORING state. Therefore, if possible, remove the availability group only from the server instance that hosts the primary replica.  
  
-   If you delete an availability group from a computer that has been removed or evicted from the WSFC failover cluster, the availability group is only deleted locally.  
  
-   Avoid dropping an availability group when the Windows Server Failover Clustering \(WSFC\) cluster has no quorum. If you must drop an availability group while the cluster lacks quorum, the metadata availability group that is stored in the cluster is not removed. After the cluster regains quorum, you will need to drop the availability group again to remove it from the WSFC cluster.  
  
-   On a secondary replica, DROP AVAILABILITY GROUP should only be used only for emergency purposes. This is because dropping an availability group takes the availability group offline. If you drop the availability group from a secondary replica, the primary replica cannot determine whether the OFFLINE state occurred because of quorum loss, a forced failover, or a DROP AVAILABILITY GROUP command. The primary replica transitions to the RESTORING state to prevent a possible split\-brain situation. For more information, see [How It Works: DROP AVAILABILITY GROUP Behaviors](http://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) \(CSS SQL Server Engineers blog\).  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission. To drop an availability group that is not hosted by the local server instance you need CONTROL SERVER permission or CONTROL permission on that Availability Group.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 **To delete an availability group**  
  
1.  In Object Explorer, connect to the server instance that hosts primary replica, if possible, or connect to another server instance that is enabled for Always On Availability Groups on a WSFC node that possess the correct security credentials for the availability group. Expand the server tree.  
  
2.  Expand the **Always On High Availability** node and the **Availability Groups** node.  
  
3.  This step depends on whether you want to delete multiple availability groups or only one availability group, as follows:  
  
    -   To delete multiple availability groups \(whose primary replicas are on the connected server instance\), use the **Object Explorer Details** pane to view and select all the availability groups that you want to delete. For more information, see [Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Object%20Explorer%20Details%20to%20Monitor%20Availability%20Groups%20\(SQL%20Server%20Management%20Studio\).md).  
  
    -   To delete a single availability group, select it in either the **Object Explorer** pane or the **Object Explorer Details** pane.  
  
4.  Right\-click the selected availability group or groups, and select the **Delete** command.  
  
5.  In the **Remove Availability Group** dialog box, to delete all the listed availability groups, click **OK**. If you do not want to remove all the listed availability groups, click **Cancel**.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 **To delete an availability group**  
  
1.  Connect to the server instance that hosts the primary replica, if possible, or connect to another server instance that is enabled for Always On Availability Groups on a WSFC node that possess the correct security credentials for the availability group.  
  
2.  Use the [DROP AVAILABILITY GROUP](../Topic/DROP%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md) statement, as follows  
  
     DROP AVAILABILITY GROUP *group\_name*  
  
     where *group\_name* is the name of the availability group to be dropped.  
  
     The following example deletes the `MyAG` availability group.  
  
    ```  
    DROP AVAILABILITY GROUP MyAG;  
    ```  
  
##  <a name="PowerShellProcedure"></a> Using PowerShell  
 **To delete an availability group**  
  
 In the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell provider:  
  
1.  Change directory \(**cd**\) to the server instance that hosts the primary replica, if possible, or connect to another server instance that is enabled for Always On Availability Groups on a WSFC node that possess the correct security credentials for the availability group.  
  
2.  Use the **Remove\-SqlAvailabilityGroup** cmdlet.  
  
     For example, the following command removes the availability group named `MyAg`. This command can be executed on any server instance that hosts an availability replica for the availability group.  
  
    ```  
    Remove-SqlAvailabilityGroup `   
    -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg  
    ```  
  
    > [!NOTE]  
    >  To view the syntax of a cmdlet, use the **Get\-Help** cmdlet in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell environment. For more information, see [Get Help SQL Server PowerShell](../../Topics\TopicNameNotContainA/Get-Help-SQL-Server-PowerShell.md).  
  
 **To set up and use the SQL Server PowerShell provider**  
  
-   [SQL Server PowerShell Provider](../../Topics\TopicNameNotContainA/SQL-Server-PowerShell-Provider.md)  
  
##  <a name="RelatedContent"></a> Related Content  
  
-   [How It Works: DROP AVAILABILITY GROUP Behaviors](http://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) \(CSS SQL Server Engineers blog\)  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Creation and Configuration of Availability Groups &#40;SQL Server&#41;](../Topic/Creation%20and%20Configuration%20of%20Availability%20Groups%20\(SQL%20Server\).md)  
  
  