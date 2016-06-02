---
title: View Availability Group Properties (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 61243c87-bd62-4510-863f-2a8f347caf1f
---
# View Availability Group Properties (SQL Server)
  This topic describes how to view the properties of an availability group for an Always On availability group by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
-   **To view availability group properties, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 **To view and change the properties an availability group**  
  
1.  In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.  
  
2.  Expand the **Always On High Availability** node and the **Availability Groups** node.  
  
3.  Right\-click the availability group whose properties you want to view, and select the **Properties** command.  
  
4.  In the **Availability Group Properties** dialog box, use the **General** and **Backup Preferences** pages to view and, in some cases, change properties of the selected availability group. For more information, see [Availability Group Properties: New Availability Group &#40;General Page&#41;](../Topic/Availability%20Group%20Properties:%20New%20Availability%20Group%20\(General%20Page\).md) and [Availability Group Properties: New Availability Group &#40;Backup Preferences Page&#41;](../Topic/Availability%20Group%20Properties:%20New%20Availability%20Group%20\(Backup%20Preferences%20Page\).md).  
  
     Use the **Permissions** page to view the current logins, roles, and explicit permissions associated with the availability group. For more information, see [Permissions or Securables Page](../../Topics\TopicNameNotContainA/Permissions-or-Securables-Page.md).  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 **To view the properties and state of an availability group**  
  
 To query the properties and states of the availability groups for which the server instance hosts an availability replica, use the following views:  
  
 [sys.availability\_groups](../Topic/sys.availability_groups%20\(Transact-SQL\).md)  
 Returns a row for each availability group for which the local instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] hosts an availability replica. Each row contains a cached copy of the availability group metadata.  
  
 **Column names:** group\_id, name, resource\_id, resource\_group\_id, failure\_condition\_level, health\_check\_timeout, automated\_backup\_preference, automated\_backup\_preference\_desc  
  
 [sys.availability\_groups\_cluster](../Topic/sys.availability_groups_cluster%20\(Transact-SQL\).md)  
 Returns a row for each availability group in the WSFC cluster. Each row contains the availability group metadata from the Windows Server Failover Clustering \(WSFC\) cluster.  
  
 **Column names:** group\_id, name, resource\_id, resource\_group\_id, failure\_condition\_level, health\_check\_timeout, automated\_backup\_preference, automated\_backup\_preference\_desc  
  
 [sys.dm\_hadr\_availability\_group\_states](../Topic/sys.dm_hadr_availability_group_states%20\(Transact-SQL\).md)  
 Returns a row for each availability group that possesses an availability replica on the local instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Each row displays the states that define the health of a given availability group.  
  
 **Column names:** group\_id, primary\_replica, primary\_recovery\_health, primary\_recovery\_health\_desc, secondary\_recovery\_health, secondary\_recovery\_health\_desc, synchronization\_health, synchronization\_health\_desc  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To view information about availability groups**  
  
-   [View Availability Replica Properties &#40;SQL Server&#41;](../Topic/View%20Availability%20Replica%20Properties%20\(SQL%20Server\).md)  
  
-   [View Availability Group Listener Properties &#40;SQL Server&#41;](../Topic/View%20Availability%20Group%20Listener%20Properties%20\(SQL%20Server\).md)  
  
-   [Always On Policies for Operational Issues with Always On Availability Groups &#40;SQL Server&#41;](../Topic/Always%20On%20Policies%20for%20Operational%20Issues%20with%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)  
  
-   [Use the Always On Dashboard &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Always%20On%20Dashboard%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [Monitor Availability Groups &#40;Transact-SQL&#41;](../Topic/Monitor%20Availability%20Groups%20\(Transact-SQL\).md)  
  
 **To configure an existing availability group**  
  
-   [Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](../Topic/Add%20a%20Secondary%20Replica%20to%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;](../Topic/Remove%20a%20Secondary%20Replica%20from%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Add a Database to an Availability Group &#40;SQL Server&#41;](../Topic/Add%20a%20Database%20to%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;](../Topic/Remove%20a%20Secondary%20Database%20from%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Create or Configure an Availability Group Listener &#40;SQL Server&#41;](../Topic/Create%20or%20Configure%20an%20Availability%20Group%20Listener%20\(SQL%20Server\).md)  
  
-   [Remove an Availability Group Listener &#40;SQL Server&#41;](../Topic/Remove%20an%20Availability%20Group%20Listener%20\(SQL%20Server\).md)  
  
-   [Remove a Primary Database from an Availability Group &#40;SQL Server&#41;](../Topic/Remove%20a%20Primary%20Database%20from%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Remove an Availability Group &#40;SQL Server&#41;](../Topic/Remove%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
 **To manually fail over an availability group**  
  
-   [Perform a Planned Manual Failover of an Availability Group &#40;SQL Server&#41;](../Topic/Perform%20a%20Planned%20Manual%20Failover%20of%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;](../Topic/Perform%20a%20Forced%20Manual%20Failover%20of%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Monitor Availability Groups &#40;Transact-SQL&#41;](../Topic/Monitor%20Availability%20Groups%20\(Transact-SQL\).md)   
 [Always On Policies for Operational Issues with Always On Availability Groups &#40;SQL Server&#41;](../Topic/Always%20On%20Policies%20for%20Operational%20Issues%20with%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)  
  
  