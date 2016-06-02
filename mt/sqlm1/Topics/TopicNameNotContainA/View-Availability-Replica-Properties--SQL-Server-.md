---
title: View Availability Replica Properties (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 14fed3c4-8ecc-4e1c-931d-a7ec1e9f9e90
---
# View Availability Replica Properties (SQL Server)
  This topic describes how to view the properties of an availability replica for an Always On availability group by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
-   **To view availability replica properties, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 **To view and change properties an availability replica**  
  
1.  In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.  
  
2.  Expand the **Always On High Availability** node and the **Availability Groups** node.  
  
3.  Expand the availability group to which the availability replica belongs, and expand the **Availability Replicas** node.  
  
4.  Right\-click the availability replica whose properties you want to view, and select the **Properties** command.  
  
5.  In the **Availability Replica Properties** dialog box, use the **General** page to view the properties of this replica. If you are connected to the primary replica, you can change the following properties: availability mode, failover mode, connection access for the primary role, read\-access for the secondary role \(readable\-secondary\), and the session\-timeout value. For more information, see [Availability Replica Properties &#40;General Page&#41;](../Topic/Availability%20Replica%20Properties%20\(General%20Page\).md).  
  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 **To view properties and states of availability replicas**  
  
 To view the properties and states of availability replicas, use the following views and system function:  
  
 [sys.availability\_replicas](../Topic/sys.availability_replicas%20\(Transact-SQL\).md)  
 Returns a row for every availability replica in each availability group for which the local instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] hosts an availability replica.  
  
 **Column names:** replica\_id, group\_id, replica\_metadata\_id, replica\_server\_name, owner\_sid, endpoint\_url, availability\_mode, availability\_mode\_desc, failover\_mode, failover\_mode\_desc, session\_timeout, primary\_role\_allow\_connections, primary\_role\_allow\_connections\_desc, secondary\_role\_allow\_connections, secondary\_role\_allow\_connections\_desc, create\_date, modify\_date, backup\_priority, read\_only\_routing\_url  
  
 [sys.availability\_read\_only\_routing\_lists](../Topic/sys.availability_read_only_routing_lists%20\(Transact-SQL\).md)  
 Returns a row for the read only routing list of each availability replica in an Always On availability group in the WSFC failover cluster.  
  
 **Column names:** replica\_id, routing\_priority, read\_only\_replica\_id  
  
 [sys.dm\_hadr\_availability\_replica\_cluster\_nodes](../Topic/sys.dm_hadr_availability_replica_cluster_nodes%20\(Transact-SQL\).md)  
 Returns a row for every availability replica \(regardless of join state\) of the Always On availability groups in the Windows Server Failover Clustering \(WSFC\) cluster.  
  
 **Column names:** group\_name, replica\_server\_name, node\_name  
  
 [sys.dm\_hadr\_availability\_replica\_cluster\_states](../Topic/sys.dm_hadr_availability_replica_cluster_states%20\(Transact-SQL\).md)  
 Returns a row for each replica \(regardless of join state\) of all Always On availability groups \(regardless of replica location\) in the Windows Server Failover Clustering \(WSFC\) cluster.  
  
 **Column names:** replica\_id, replica\_server\_name, group\_id, join\_state, join\_state\_desc  
  
 [sys.dm\_hadr\_availability\_replica\_states](../Topic/sys.dm_hadr_availability_replica_states%20\(Transact-SQL\).md)  
 Returns a row showing the state of each local availability replica and a row for each remote availability replica in the same availability group.  
  
 **Column names:** replica\_id, group\_id, is\_local, role, role\_desc, operational\_state, operational\_state\_desc, connected\_state, connected\_state\_desc, recovery\_health, recovery\_health\_desc, synchronization\_health, synchronization\_health\_desc, last\_connect\_error\_number, last\_connect\_error\_description, and last\_connect\_error\_timestamp  
  
 [sys.fn\_hadr\_backup\_is\_preferred\_replica](../Topic/sys.fn_hadr_backup_is_preferred_replica%20%20\(Transact-SQL\).md)  
 Determines whether the current replica is the preferred backup replica. Returns 1 if the database on the current server instance is the preferred replica. Otherwise, it returns 0.  
  
> [!NOTE]  
>  For information about performance counters for availability replicas \(the **SQLServer:Availability Replica**  performance object\), see [SQL Server, Availability Replica](../../Topics\TopicNameNotContainA/SQL-Server,-Availability-Replica.md).  
  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To view information about availability groups**  
  
-   [View Availability Group Properties &#40;SQL Server&#41;](../Topic/View%20Availability%20Group%20Properties%20\(SQL%20Server\).md)  
  
-   [View Availability Group Listener Properties &#40;SQL Server&#41;](../Topic/View%20Availability%20Group%20Listener%20Properties%20\(SQL%20Server\).md)  
  
-   [Always On Policies for Operational Issues with Always On Availability Groups &#40;SQL Server&#41;](../Topic/Always%20On%20Policies%20for%20Operational%20Issues%20with%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)  
  
-   [Use the Always On Dashboard &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Always%20On%20Dashboard%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [Monitor Availability Groups &#40;Transact-SQL&#41;](../Topic/Monitor%20Availability%20Groups%20\(Transact-SQL\).md)  
  
 **To manage availability replicas**  
  
-   [Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](../Topic/Add%20a%20Secondary%20Replica%20to%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](../Topic/Join%20a%20Secondary%20Replica%20to%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;](../Topic/Configure%20Read-Only%20Access%20on%20an%20Availability%20Replica%20\(SQL%20Server\).md)  
  
-   [Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;](../Topic/Change%20the%20Availability%20Mode%20of%20an%20Availability%20Replica%20\(SQL%20Server\).md)  
  
-   [Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;](../Topic/Change%20the%20Failover%20Mode%20of%20an%20Availability%20Replica%20\(SQL%20Server\).md)  
  
-   [Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;](../Topic/Change%20the%20Session-Timeout%20Period%20for%20an%20Availability%20Replica%20\(SQL%20Server\).md)  
  
-   [Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;](../Topic/Remove%20a%20Secondary%20Replica%20from%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
 **To manage an availability database**  
  
-   [Add a Database to an Availability Group &#40;SQL Server&#41;](../Topic/Add%20a%20Database%20to%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](../Topic/Join%20a%20Secondary%20Database%20to%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Suspend an Availability Database &#40;SQL Server&#41;](../Topic/Suspend%20an%20Availability%20Database%20\(SQL%20Server\).md)  
  
-   [Resume an Availability Database &#40;SQL Server&#41;](../Topic/Resume%20an%20Availability%20Database%20\(SQL%20Server\).md)  
  
-   [Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;](../Topic/Remove%20a%20Secondary%20Database%20from%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Remove a Primary Database from an Availability Group &#40;SQL Server&#41;](../Topic/Remove%20a%20Primary%20Database%20from%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Monitor Availability Groups &#40;Transact-SQL&#41;](../Topic/Monitor%20Availability%20Groups%20\(Transact-SQL\).md)   
 [Always On Policies for Operational Issues with Always On Availability Groups &#40;SQL Server&#41;](../Topic/Always%20On%20Policies%20for%20Operational%20Issues%20with%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Administration of an Availability Group &#40;SQL Server&#41;](../Topic/Administration%20of%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
  