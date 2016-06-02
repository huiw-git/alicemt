---
title: Add a Secondary Replica to an Availability Group (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6669dcce-85f9-495f-aadf-7f62cff4a9da
---
# Add a Secondary Replica to an Availability Group (SQL Server)
  This topic describes how to add a secondary replica to an existing Always On availability group by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
-   **Before you begin:**  
  
     [Prerequisites and Restrictions](#PrerequisitesRestrictions)  
  
     [Security](#Security)  
  
-   **To add a replica, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   **Follow Up:**  [After Adding a Secondary Replica](#FollowUp)  
  
## Before You Begin  
 We strongly recommend that you read this section before attempting to create your first availability group.  
  
##  <a name="PrerequisitesRestrictions"></a> Prerequisites and Restrictions  
  
-   You must be connected to the server instance that hosts the primary replica.  
  
 For more information, see [Prerequisites, Restrictions, and Recommendations for Always On Availability Groups &#40;SQL Server&#41;](../Topic/Prerequisites,%20Restrictions,%20and%20Recommendations%20for%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md).  
  
##  <a name="Security"></a> Security  
  
###  <a name="Permissions"></a> Permissions  
 Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 **To add a replica**  
  
1.  In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.  
  
2.  Expand the **Always On High Availability** node and the **Availability Groups** node.  
  
3.  Right\-click the availability group, and select one of the following commands:  
  
    -   Select the **Add Replica** command to launch the Add Replica to Availability Group Wizard. For more information, see [Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Add%20Replica%20to%20Availability%20Group%20Wizard%20\(SQL%20Server%20Management%20Studio\).md).  
  
    -   Alternatively, select the **Properties** command to open the **Availability Group Properties** dialog box. The steps for adding a replica in this dialog box are as follows:  
  
        1.  In the **Availability Replicas** pane of the dialog box, click the **Add** button. This creates and selects a replica entry in which the blank Server Instance field is selected.  
  
        2.  Enter the name of a server instance that meets the prerequisites for hosting an availability replica.  
  
         To add an additional replicas, repeat the preceding steps. When you are done specifying replicas, click **OK** to complete the operation.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 **To add a replica**  
  
1.  Connect to the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that hosts the primary replica.  
  
2.  Add the new secondary replica to the availability group by using the ADD REPLICA ON clause of the ALTER AVAILABILITY GROUP statement. The ENDPOINT\_URL, AVAILABILITY\_MODE, and FAILOVER\_MODE options are required in an ADD REPLICA ON clause. The other replica options— BACKUP\_PRIORITY, SECONDARY\_ROLE, PRIMARY\_ROLE, and SESSION\_TIMEOUT—are optional. For more information, see [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../Topic/ALTER%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md).  
  
     For example, the following [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement creates a new replica to an availability group named `MyAG` on the default server instance hosted by `COMPUTER04`, whose endpoint URL is `TCP://COMPUTER04.Adventure-Works.com:5022'`. This replica supports manual failover and asynchronous\-commit availability mode.  
  
    ```  
    ALTER AVAILABILITY GROUP MyAG ADD REPLICA ON 'COMPUTER04'   
       WITH (  
             ENDPOINT_URL = 'TCP://COMPUTER04.Adventure-Works.com:5022',  
             AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,  
             FAILOVER_MODE = MANUAL  
             );  
    ```  
  
##  <a name="PowerShellProcedure"></a> Using PowerShell  
 **To add a replica**  
  
1.  Change directory \(**cd**\) to the server instance that hosts the primary replica.  
  
2.  Use the **New\-SqlAvailabilityReplica** cmdlet.  
  
     For example, the following command adds an availability replica to an existing availability group named `MyAg`. This replica supports manual failover and asynchronous\-commit availability mode. In the secondary role, this replica will support read access connections, allowing you to offload read\-only processing to this replica.  
  
    ```  
    $agPath = "SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg"  
    $endpointURL = "TCP://PrimaryServerName.domain.com:5022"  
    $failoverMode = "Manual"  
    $availabilityMode = "AsynchronousCommit"  
    $secondaryReadMode = "AllowAllConnections"  
  
    New-SqlAvailabilityReplica -Name SecondaryServer\Instance `   
    -EndpointUrl $endpointURL `   
    -FailoverMode $failoverMode `   
    -AvailabilityMode $availabilityMode `   
    -ConnectionModeInSecondaryRole $secondaryReadMode `   
    -Path $agPath  
    ```  
  
    > [!NOTE]  
    >  To view the syntax of a cmdlet, use the **Get\-Help** cmdlet in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell environment. For more information, see [Get Help SQL Server PowerShell](../../Topics\TopicNameNotContainA/Get-Help-SQL-Server-PowerShell.md).  
  
 **To set up and use the SQL Server PowerShell provider**  
  
-   [SQL Server PowerShell Provider](../../Topics\TopicNameNotContainA/SQL-Server-PowerShell-Provider.md)  
  
##  <a name="FollowUp"></a> Follow Up: After Adding a Secondary Replica  
 To add a replica for an existing availability group, you must perform the following steps:  
  
1.  Connect to the server instance that is going to host the new secondary replica.  
  
2.  Join the new secondary replica to the availability group. For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](../Topic/Join%20a%20Secondary%20Replica%20to%20an%20Availability%20Group%20\(SQL%20Server\).md).  
  
3.  For each database in the availability group, create a secondary database on the server instance that is hosting the secondary replica. For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](../Topic/Manually%20Prepare%20a%20Secondary%20Database%20for%20an%20Availability%20Group%20\(SQL%20Server\).md).  
  
4.  Join each of the new secondary databases to the availability group. For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](../Topic/Join%20a%20Secondary%20Database%20to%20an%20Availability%20Group%20\(SQL%20Server\).md).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To manage an availability replica**  
  
-   [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](../Topic/Join%20a%20Secondary%20Replica%20to%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;](../Topic/Remove%20a%20Secondary%20Replica%20from%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;](../Topic/Configure%20Read-Only%20Access%20on%20an%20Availability%20Replica%20\(SQL%20Server\).md)  
  
-   [Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;](../Topic/Change%20the%20Availability%20Mode%20of%20an%20Availability%20Replica%20\(SQL%20Server\).md)  
  
-   [Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;](../Topic/Change%20the%20Failover%20Mode%20of%20an%20Availability%20Replica%20\(SQL%20Server\).md)  
  
-   [Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;](../Topic/Change%20the%20Session-Timeout%20Period%20for%20an%20Availability%20Replica%20\(SQL%20Server\).md)  
  
-   [Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;](../Topic/Change%20the%20Session-Timeout%20Period%20for%20an%20Availability%20Replica%20\(SQL%20Server\).md)  
  
## See Also  
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../Topic/ALTER%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md)   
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Creation and Configuration of Availability Groups &#40;SQL Server&#41;](../Topic/Creation%20and%20Configuration%20of%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Use the Always On Dashboard &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Always%20On%20Dashboard%20\(SQL%20Server%20Management%20Studio\).md)   
 [Monitor Availability Groups &#40;Transact-SQL&#41;](../Topic/Monitor%20Availability%20Groups%20\(Transact-SQL\).md)  
  
  