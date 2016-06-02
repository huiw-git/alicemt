---
title: Monitor Availability Groups (Transact-SQL)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 881a34de-8461-4811-8c62-322bf7226bed
---
# Monitor Availability Groups (Transact-SQL)
  For monitoring availability groups and replicas and the associated databases by using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] provides a set of catalog and dynamic management views and server properties. Using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] SELECT statements, you can use the views to monitor availability groups and their replicas and databases. The information returned for a given availability group depends on whether you are connected to the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that is hosting the primary replica or a secondary replica.  
  
> [!TIP]  
>  Many of these views can be joined using their ID columns to return information from multiple views in a single query.  
  
 **In This Topic:**  
  
-   [Permissions](#Permissions)  
  
-   **Using Transact\-SQL to monitor:**  
  
     [Always On Availability Groups feature on a server instance](#AoAgFeatureOnSI)  
  
     [Availability groups on the WSFC cluster](#WSFC)  
  
     [Availability groups](#AvGroups)  
  
     [Availability replicas](#AvReplicas)  
  
     [Availability databases](#AvDbs)  
  
     [Availability group listeners](#AGlisteners)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="Permissions"></a> Permissions  
 [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] catalog views require VIEW ANY DEFINITION permission on the server instance. [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] dynamic management views require VIEW SERVER STATE permission on the server.  
  
##  <a name="AoAgFeatureOnSI"></a> Monitoring the Always On Availability Groups Feature on a Server Instance  
 To monitor the [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] feature on a server instance, use the following built\-in function:  
  
 [SERVERPROPERTY](../Topic/SERVERPROPERTY%20\(Transact-SQL\).md) function  
 Returns server property information about whether [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] is enabled and, if so, whether it has started on the server instance.  
  
 **Column names:** IsHadrEnabled, HadrManagerStatus  
  
##  <a name="WSFC"></a> Monitoring Availability Groups on the WSFC Cluster  
 To monitor the Windows Server Failover Clustering \(WSFC\) cluster that hosts a local server instance that is enabled for [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)], use the following views:  
  
 [sys.dm\_hadr\_cluster](../Topic/sys.dm_hadr_cluster%20\(Transact-SQL\).md)  
 If the Windows Server Failover Clustering \(WSFC\) node that hosts an instance of SQL Server with [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] enabled has WSFC quorum, **sys.dm\_hadr\_cluster** returns a row that exposes the cluster name and information about the quorum. If the WSFC node has no quorum, no rows are returned.  
  
 **Column names:** cluster\_name, quorum\_type, quorum\_type\_desc, quorum\_state, quorum\_state\_desc  
  
 [sys.dm\_hadr\_cluster\_members](../Topic/sys.dm_hadr_cluster_members%20\(Transact-SQL\).md)  
 If the WSFC node that hosts the local Always On\-enabled instance of SQL Server has WSFC quorum, returns a row for each of the members that constitute the quorum and the state of each of them.  
  
 **Column names:** member\_name, member\_type, member\_type\_desc, member\_state, member\_state\_desc, number\_of\_quorum\_votes  
  
 [sys.dm\_hadr\_cluster\_networks](../Topic/sys.dm_hadr_cluster_networks%20\(Transact-SQL\).md)  
 Returns a row for every member that is participating in an availability group's subnet configuration. You can use this dynamic management view to validate the network virtual IP that is configured for each availability replica.  
  
 **Column names:** member\_name, network\_subnet\_ip, network\_subnet\_ipv4\_mask, network\_subnet\_prefix\_length, is\_public, is\_ipv4  
  
 **Primary key:** member\_name \+ network\_subnet\_IP \+ network\_subnet\_prefix\_length  
  
 [sys.dm\_hadr\_instance\_node\_map](../Topic/sys.dm_hadr_instance_node_map%20\(Transact-SQL\).md)  
 For every instance of SQL Server that hosts an availability replica that is joined to its Always On availability group, returns the name of the Windows Server Failover Clustering \(WSFC\) node that hosts the server instance. This dynamic management view has the following uses:  
  
-   This dynamic management view is useful for detecting an availability group with multiple availability replicas that are hosted on the same WSFC node, which is an unsupported configuration that could occur after an FCI failover if the availability group is incorrectly configured.  
  
-   When multiple SQL Server instances are hosted on the same WSFC node, the Resource DLL uses this dynamic management view to determine the instance of SQL Server to connect to.  
  
 **Column names:** ag\_resource\_id, instance\_name, node\_name  
  
 [sys.dm\_hadr\_name\_id\_map](../Topic/sys.dm_hadr_name_id_map%20\(Transact-SQL\).md)  
 Shows the mapping of Always On availability groups that the current instance of SQL Server has joined to three unique IDs: an availability group ID, a WSFC resource ID, and a WSFC Group ID. The purpose of this mapping is to handle the scenario in which the WSFC resource\/group is renamed.  
  
 **Column names:** ag\_name, ag\_id, ag\_resource\_id, ag\_group\_id  
  
> [!NOTE]  
>  Also see **sys.dm\_hadr\_availability\_replica\_cluster\_nodes** and **sys.dm\_hadr\_availability\_replica\_cluster\_states** in the [Monitoring Availability Replicas](#AvReplicas) section and **sys.availability\_databases\_cluster** and **sys.dm\_hadr\_database\_replica\_cluster\_states** in the [Monitoring Availability Databases](#AvDbs) section, later in this topic.  
  
 For information about WSFC clusters and [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)], see [Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../Topic/Windows%20Server%20Failover%20Clustering%20\(WSFC\)%20with%20SQL%20Server.md) and [Failover Clustering and Always On Availability Groups &#40;SQL Server&#41;](../Topic/Failover%20Clustering%20and%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md).  
  
##  <a name="AvGroups"></a> Monitoring Availability Groups  
 To monitor the availability groups for which the server instance hosts an availability replica, use the following views:  
  
 [sys.availability\_groups](../Topic/sys.availability_groups%20\(Transact-SQL\).md)  
 Returns a row for each availability group for which the local instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] hosts an availability replica. Each row contains a cached copy of the availability group metadata.  
  
 **Column names:** group\_id, name, resource\_id, resource\_group\_id, failure\_condition\_level, health\_check\_timeout, automated\_backup\_preference, automated\_backup\_preference\_desc  
  
 [sys.availability\_groups\_cluster](../Topic/sys.availability_groups_cluster%20\(Transact-SQL\).md)  
 Returns a row for each availability group in the WSFC cluster. Each row contains the availability group metadata from the Windows Server Failover Clustering \(WSFC\) cluster.  
  
 **Column names:** group\_id, name, resource\_id, resource\_group\_id, failure\_condition\_level, health\_check\_timeout, automated\_backup\_preference, automated\_backup\_preference\_desc  
  
 [sys.dm\_hadr\_availability\_group\_states](../Topic/sys.dm_hadr_availability_group_states%20\(Transact-SQL\).md)  
 Returns a row for each availability group that possesses an availability replica on the local instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Each row displays the states that define the health of a given availability group.  
  
 **Column names:** group\_id, primary\_replica, primary\_recovery\_health, primary\_recovery\_health\_desc, secondary\_recovery\_health, secondary\_recovery\_health\_desc, synchronization\_health, synchronization\_health\_desc  
  
##  <a name="AvReplicas"></a> Monitoring Availability Replicas  
 To monitor availability replicas, use the following views and system function:  
  
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
 Determines whether the current replica is the preferred backup replica.  
  
> [!NOTE]  
>  For information about performance counters for availability replicas \(the **SQLServer:Availability Replica**  performance object\), see [SQL Server, Availability Replica](../../Topics\TopicNameNotContainA/SQL-Server,-Availability-Replica.md).  
  
##  <a name="AvDbs"></a> Monitoring Availability Databases  
 To monitor availability databases, use the following views:  
  
 [sys.availability\_databases\_cluster](../Topic/sys.availability_databases_cluster%20\(Transact-SQL\).md)  
 Contains one row for each database on the instance of SQL Server that are part of all Always On Availability Groups in the cluster, regardless of whether the local copy database has been joined to the availability group yet.  
  
> [!NOTE]  
>  When a database is added to an availability group, the primary database is automatically joined to the group. Secondary databases must be prepared on each secondary replica before they can be joined to the availability group.  
  
 **Column names:** group\_id, group\_database\_id, database\_name  
  
 [sys.databases](../Topic/sys.databases%20\(Transact-SQL\).md)  
 Contains one row per database in the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. If a database belongs to an availability replica, the row for that database displays the GUID of the replica and the unique identifier of the database within its availability group.  
  
 **[!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] column names:** replica\_id, group\_database\_id  
  
 [sys.dm\_hadr\_auto\_page\_repair](../Topic/sys.dm_hadr_auto_page_repair%20\(Transact-SQL\).md)  
 Returns a row for every automatic page\-repair attempt on any availability database on an availability replica that is hosted for any availability group by the server instance. This view contains rows for the latest automatic page\-repair attempts on a given primary or secondary database, with a maximum of 100 rows per database. As soon as a database reaches the maximum, the row for its next automatic page\-repair attempt replaces one of the existing entries.  
  
 **Column names:** database\_id, file\_id, page\_id, error\_type, page\_status, modification\_time  
  
 [sys.dm\_hadr\_database\_replica\_states](../Topic/sys.dm_hadr_database_replica_states%20\(Transact-SQL\).md)  
 Returns a row for each database that is participating in any availability group for which the local instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is hosting an availability replica.  
  
 **Column names:** database\_id, group\_id, replica\_id, group\_database\_id, is\_local, synchronization\_state, synchronization\_state\_desc, is\_commit\_participant, synchronization\_health, synchronization\_health\_desc, database\_state, database\_state\_desc, is\_suspended, suspend\_reason, suspend\_reason\_desc, recovery\_lsn, truncation\_lsn, last\_sent\_lsn, last\_sent\_time, last\_received\_lsn, last\_received\_time, last\_hardened\_lsn, last\_hardened\_time, last\_redone\_lsn, last\_redone\_time, log\_send\_queue\_size, log\_send\_rate, redo\_queue\_size, redo\_rate, filestream\_send\_rate, end\_of\_log\_lsn, last\_commit\_lsn, last\_commit\_time, low\_water\_mark\_for\_ghosts  
  
 [sys.dm\_hadr\_database\_replica\_cluster\_states](../Topic/sys.dm_hadr_database_replica_cluster_states%20\(Transact-SQL\).md)  
 Returns a row containing information intended to provide you with insight into the health of the availability databases in each availability group on the Windows Server Failover Clustering \(WSFC\) cluster. This dynamic management view is useful when planning or responding to a failover or for discovering which secondary replica in an availability group is holding up log truncation on a given primary database.  
  
 **Column names:** replica\_id, group\_database\_id, database\_name, is\_failover\_ready, is\_pending\_secondary\_suspend, is\_database\_joined, recovery\_lsn, truncation\_lsn  
  
> [!NOTE]  
>  The primary replica location is the authoritative source for an availability group.  
  
> [!NOTE]  
>  For information about the [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] performance counters for availability databases \(the **SQLServer:Database Replica** performance object\), see [SQL Server, Database Replica](../../Topics\TopicNameNotContainA/SQL-Server,-Database-Replica.md). Also, to monitor transaction\-log activity on availability databases, use the following counters of the **SQLServer:Databases** performance object: **Log Flush Write Time \(ms\)**, **Log Flushes\/sec**, **Log Pool Cache Misses\/sec**, **Log Pool Disk Reads\/sec**, and **Log Pool Requests\/sec**. For more information, see [SQL Server, Databases Object](../../Topics\TopicNameNotContainA/SQL-Server,-Databases-Object.md).  
  
##  <a name="AGlisteners"></a> Monitoring Availability Group Listeners  
 To monitor the availability group listeners on subnets of the WSFC cluster, use the following views:  
  
 [sys.availability\_group\_listener\_ip\_addresses](../Topic/sys.availability_group_listener_ip_addresses%20\(Transact-SQL\).md)  
 Returns a row for every conformant virtual IP address that is currently online for an availability group listener.  
  
 **Column names:** listener\_id, ip\_address, ip\_subnet\_mask, is\_dhcp, network\_subnet\_ip, network\_subnet\_prefix\_length, network\_subnet\_ipv4\_mask, state, state\_desc  
  
 [sys.availability\_group\_listeners](../Topic/sys.availability_group_listeners%20\(Transact-SQL\).md)  
 For a given availability group, returns either zero rows indicating that no network name is associated with the availability group, or returns a row for each availability\-group listener configuration in the WSFC cluster.  
  
 **Column names:** group\_id, listener\_id, dns\_name, port, is\_conformant, ip\_configuration\_string\_from\_cluster  
  
 [sys.dm\_tcp\_listener\_states](../Topic/sys.dm_tcp_listener_states%20\(Transact-SQL\).md)  
 Returns a row containing dynamic\-state information for each TCP listener.  
  
 **Column names:** listener\_id, ip\_address, is\_ipv4, port, type, type\_desc, state, state\_desc, start\_time  
  
 **Primary key:** listener\_id  
  
 For information about availability group listeners, see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../Topic/Availability%20Group%20Listeners,%20Client%20Connectivity,%20and%20Application%20Failover%20\(SQL%20Server\).md).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **Always On Availability Groups monitoring tasks:**  
  
-   [Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Object%20Explorer%20Details%20to%20Monitor%20Availability%20Groups%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [View Availability Group Properties &#40;SQL Server&#41;](../Topic/View%20Availability%20Group%20Properties%20\(SQL%20Server\).md)  
  
-   [View Availability Replica Properties &#40;SQL Server&#41;](../Topic/View%20Availability%20Replica%20Properties%20\(SQL%20Server\).md)  
  
-   [View Availability Group Listener Properties &#40;SQL Server&#41;](../Topic/View%20Availability%20Group%20Listener%20Properties%20\(SQL%20Server\).md)  
  
 **Always On Availability Groups monitoring reference \(Transact\-SQL\):**  
  
-   [SERVERPROPERTY &#40;Transact-SQL&#41;](../Topic/SERVERPROPERTY%20\(Transact-SQL\).md)  
  
-   [sys.availability_group_listener_ip_addresses &#40;Transact-SQL&#41;](../Topic/sys.availability_group_listener_ip_addresses%20\(Transact-SQL\).md)  
  
-   [sys.availability_group_listeners &#40;Transact-SQL&#41;](../Topic/sys.availability_group_listeners%20\(Transact-SQL\).md)  
  
-   [sys.availability_databases_cluster &#40;Transact-SQL&#41;](../Topic/sys.availability_databases_cluster%20\(Transact-SQL\).md)  
  
-   [sys.availability_groups &#40;Transact-SQL&#41;](../Topic/sys.availability_groups%20\(Transact-SQL\).md)  
  
-   [sys.availability_read_only_routing_lists &#40;Transact-SQL&#41;](../Topic/sys.availability_read_only_routing_lists%20\(Transact-SQL\).md)  
  
-   [sys.availability_replicas &#40;Transact-SQL&#41;](../Topic/sys.availability_replicas%20\(Transact-SQL\).md)  
  
-   [sys.dm_hadr_availability_replica_cluster_nodes &#40;Transact-SQL&#41;](../Topic/sys.dm_hadr_availability_replica_cluster_nodes%20\(Transact-SQL\).md)  
  
-   [sys.dm_hadr_availability_replica_cluster_states &#40;Transact-SQL&#41;](../Topic/sys.dm_hadr_availability_replica_cluster_states%20\(Transact-SQL\).md)  
  
-   [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](../Topic/sys.database_mirroring_endpoints%20\(Transact-SQL\).md)  
  
-   [sys.dm_hadr_auto_page_repair &#40;Transact-SQL&#41;](../Topic/sys.dm_hadr_auto_page_repair%20\(Transact-SQL\).md)  
  
-   [sys.dm_hadr_availability_group_states &#40;Transact-SQL&#41;](../Topic/sys.dm_hadr_availability_group_states%20\(Transact-SQL\).md)  
  
-   [sys.dm_hadr_availability_replica_cluster_states &#40;Transact-SQL&#41;](../Topic/sys.dm_hadr_availability_replica_cluster_states%20\(Transact-SQL\).md)  
  
-   [sys.dm_hadr_availability_replica_states &#40;Transact-SQL&#41;](../Topic/sys.dm_hadr_availability_replica_states%20\(Transact-SQL\).md)  
  
-   [sys.dm_hadr_database_replica_states &#40;Transact-SQL&#41;](../Topic/sys.dm_hadr_database_replica_states%20\(Transact-SQL\).md)  
  
-   [sys.dm_hadr_database_replica_cluster_states &#40;Transact-SQL&#41;](../Topic/sys.dm_hadr_database_replica_cluster_states%20\(Transact-SQL\).md)  
  
-   [sys.dm_hadr_cluster &#40;Transact-SQL&#41;](../Topic/sys.dm_hadr_cluster%20\(Transact-SQL\).md)  
  
-   [sys.dm_hadr_cluster_members &#40;Transact-SQL&#41;](../Topic/sys.dm_hadr_cluster_members%20\(Transact-SQL\).md)  
  
-   [sys.dm_hadr_cluster_networks &#40;Transact-SQL&#41;](../Topic/sys.dm_hadr_cluster_networks%20\(Transact-SQL\).md)  
  
-   [sys.dm_hadr_database_replica_cluster_states &#40;Transact-SQL&#41;](../Topic/sys.dm_hadr_database_replica_cluster_states%20\(Transact-SQL\).md)  
  
-   [sys.dm_hadr_database_replica_states &#40;Transact-SQL&#41;](../Topic/sys.dm_hadr_database_replica_states%20\(Transact-SQL\).md)  
  
-   [sys.dm_hadr_instance_node_map &#40;Transact-SQL&#41;](../Topic/sys.dm_hadr_instance_node_map%20\(Transact-SQL\).md)  
  
-   [sys.dm_hadr_name_id_map &#40;Transact-SQL&#41;](../Topic/sys.dm_hadr_name_id_map%20\(Transact-SQL\).md)  
  
-   [sys.dm_os_performance_counters &#40;Transact-SQL&#41;](../Topic/sys.dm_os_performance_counters%20\(Transact-SQL\).md)  
  
-   [sys.dm_tcp_listener_states &#40;Transact-SQL&#41;](../Topic/sys.dm_tcp_listener_states%20\(Transact-SQL\).md)  
  
-   [sys.fn_hadr_backup_is_preferred_replica  &#40;Transact-SQL&#41;](../Topic/sys.fn_hadr_backup_is_preferred_replica%20%20\(Transact-SQL\).md)  
  
 **Always On performance counters:**  
  
-   [SQL Server, Availability Replica](../../Topics\TopicNameNotContainA/SQL-Server,-Availability-Replica.md)  
  
-   [SQL Server, Database Replica](../../Topics\TopicNameNotContainA/SQL-Server,-Database-Replica.md)  
  
-   [SQL Server, Databases Object](../../Topics\TopicNameNotContainA/SQL-Server,-Databases-Object.md)  
  
 **Policy\-based management for Always On Availability Groups**  
  
-   [Use Always On Policies to View the Health of an Availability Group &#40;SQL Server&#41;](../Topic/Use%20Always%20On%20Policies%20to%20View%20the%20Health%20of%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Use the Always On Dashboard &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Always%20On%20Dashboard%20\(SQL%20Server%20Management%20Studio\).md)  
  
## See Also  
 [Always On Availability Groups &#40;SQL Server&#41;](../Topic/Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Monitoring of Availability Groups &#40;SQL Server&#41;](../Topic/Monitoring%20of%20Availability%20Groups%20\(SQL%20Server\).md)  
  
  