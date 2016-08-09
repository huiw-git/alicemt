---
title: "Monitor Availability Groups (Transact-SQL)"
ms.custom: na
ms.date: 2016-05-17
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 881a34de-8461-4811-8c62-322bf7226bed
caps.latest.revision: 50
caps.handback.revision: 0
manager: jhubbard
---
# Monitor Availability Groups (Transact-SQL)
For monitoring availability groups and replicas and the associated databases by using [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)], [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/tokens/ssHADR_md.md)] provides a set of catalog and dynamic management views and server properties. Using [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] SELECT statements, you can use the views to monitor availability groups and their replicas and databases. The information returned for a given availability group depends on whether you are connected to the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] that is hosting the primary replica or a secondary replica.  
  
> [!TIP]  
>  Many of these views can be joined using their ID columns to return information from multiple views in a single query.  
  
 **In This Topic:**  
  
-   [Permissions](#Permissions)  
  
-   **Using Transact-SQL to monitor:**  
  
     [Always On Availability Groups feature on a server instance](#AoAgFeatureOnSI)  
  
     [Availability groups on the WSFC cluster](#WSFC)  
  
     [Availability groups](#AvGroups)  
  
     [Availability replicas](#AvReplicas)  
  
     [Availability databases](#AvDbs)  
  
     [Availability group listeners](#AGlisteners)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="Permissions"></a> Permissions  
 [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/tokens/ssHADR_md.md)] catalog views require VIEW ANY DEFINITION permission on the server instance. [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/tokens/ssHADR_md.md)] dynamic management views require VIEW SERVER STATE permission on the server.  
  
##  <a name="AoAgFeatureOnSI"></a> Monitoring the Always On Availability Groups Feature on a Server Instance  
 To monitor the [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/tokens/ssHADR_md.md)] feature on a server instance, use the following built-in function:  
  
 [SERVERPROPERTY](assetId:///11e166fa-3dd2-42d8-ac4b-04f18c612c4a) function  
 Returns server property information about whether [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/tokens/ssHADR_md.md)] is enabled and, if so, whether it has started on the server instance.  
  
 **Column names:** IsHadrEnabled, HadrManagerStatus  
  
##  <a name="WSFC"></a> Monitoring Availability Groups on the WSFC Cluster  
 To monitor the Windows Server Failover Clustering (WSFC) cluster that hosts a local server instance that is enabled for [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/tokens/ssHADR_md.md)], use the following views:  
  
 [sys.dm_hadr_cluster](assetId:///13ce70e4-9d43-4a80-a826-099e6213bf85)  
 If the Windows Server Failover Clustering (WSFC) node that hosts an instance of SQL Server with [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/tokens/ssHADR_md.md)] enabled has WSFC quorum, **sys.dm_hadr_cluster** returns a row that exposes the cluster name and information about the quorum. If the WSFC node has no quorum, no rows are returned.  
  
 **Column names:** cluster_name, quorum_type, quorum_type_desc, quorum_state, quorum_state_desc  
  
 [sys.dm_hadr_cluster_members](assetId:///feb20b3a-8835-41d3-9a1c-91d3117bc170)  
 If the WSFC node that hosts the local Always On-enabled instance of SQL Server has WSFC quorum, returns a row for each of the members that constitute the quorum and the state of each of them.  
  
 **Column names:** member_name, member_type, member_type_desc, member_state, member_state_desc, number_of_quorum_votes  
  
 [sys.dm_hadr_cluster_networks](assetId:///ece32b15-d63f-4f93-92b7-e2930333e97a)  
 Returns a row for every member that is participating in an availability group's subnet configuration. You can use this dynamic management view to validate the network virtual IP that is configured for each availability replica.  
  
 **Column names:** member_name, network_subnet_ip, network_subnet_ipv4_mask, network_subnet_prefix_length, is_public, is_ipv4  
  
 **Primary key:** member_name + network_subnet_IP + network_subnet_prefix_length  
  
 [sys.dm_hadr_instance_node_map](assetId:///ccfaf62c-9f87-43cf-a5e7-8942e91dd041)  
 For every instance of SQL Server that hosts an availability replica that is joined to its Always On availability group, returns the name of the Windows Server Failover Clustering (WSFC) node that hosts the server instance. This dynamic management view has the following uses:  
  
-   This dynamic management view is useful for detecting an availability group with multiple availability replicas that are hosted on the same WSFC node, which is an unsupported configuration that could occur after an FCI failover if the availability group is incorrectly configured.  
  
-   When multiple SQL Server instances are hosted on the same WSFC node, the Resource DLL uses this dynamic management view to determine the instance of SQL Server to connect to.  
  
 **Column names:** ag_resource_id, instance_name, node_name  
  
 [sys.dm_hadr_name_id_map](assetId:///e07bb8a9-37de-4a39-a257-950d7c3ae8fb)  
 Shows the mapping of Always On availability groups that the current instance of SQL Server has joined to three unique IDs: an availability group ID, a WSFC resource ID, and a WSFC Group ID. The purpose of this mapping is to handle the scenario in which the WSFC resource/group is renamed.  
  
 **Column names:** ag_name, ag_id, ag_resource_id, ag_group_id  
  
> [!NOTE]  
>  Also see **sys.dm_hadr_availability_replica_cluster_nodes** and **sys.dm_hadr_availability_replica_cluster_states** in the [Monitoring Availability Replicas](#AvReplicas) section and **sys.availability_databases_cluster** and **sys.dm_hadr_database_replica_cluster_states** in the [Monitoring Availability Databases](#AvDbs) section, later in this topic.  
  
 For information about WSFC clusters and [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/tokens/ssHADR_md.md)], see [Windows Server Failover Clustering (WSFC) with SQL Server](../../Topics/TopicNameNotContainA/Windows-Server-Failover-Clustering--WSFC--with-SQL-Server.md) and [Failover Clustering and Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Failover-Clustering-and-Always-On-Availability-Groups--SQL-Server-.md).  
  
##  <a name="AvGroups"></a> Monitoring Availability Groups  
 To monitor the availability groups for which the server instance hosts an availability replica, use the following views:  
  
 [sys.availability_groups](assetId:///da7fa55f-c008-45d9-bcfc-3513b02d9e71)  
 Returns a row for each availability group for which the local instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] hosts an availability replica. Each row contains a cached copy of the availability group metadata.  
  
 **Column names:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc  
  
 [sys.availability_groups_cluster](assetId:///d0f4683f-cdf0-4227-8b68-720ffe58f158)  
 Returns a row for each availability group in the WSFC cluster. Each row contains the availability group metadata from the Windows Server Failover Clustering (WSFC) cluster.  
  
 **Column names:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc  
  
 [sys.dm_hadr_availability_group_states](assetId:///d18019dd-f8dc-4492-b035-b1a639369b65)  
 Returns a row for each availability group that possesses an availability replica on the local instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. Each row displays the states that define the health of a given availability group.  
  
 **Column names:** group_id, primary_replica, primary_recovery_health, primary_recovery_health_desc, secondary_recovery_health, secondary_recovery_health_desc, synchronization_health, synchronization_health_desc  
  
##  <a name="AvReplicas"></a> Monitoring Availability Replicas  
 To monitor availability replicas, use the following views and system function:  
  
 [sys.availability_replicas](assetId:///0a06e9b6-a1e4-4293-867b-5c3f5a8ff62c)  
 Returns a row for every availability replica in each availability group for which the local instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] hosts an availability replica.  
  
 **Column names:** replica_id, group_id, replica_metadata_id, replica_server_name, owner_sid, endpoint_url, availability_mode, availability_mode_desc, failover_mode, failover_mode_desc, session_timeout, primary_role_allow_connections, primary_role_allow_connections_desc, secondary_role_allow_connections, secondary_role_allow_connections_desc, create_date, modify_date, backup_priority, read_only_routing_url  
  
 [sys.availability_read_only_routing_lists](assetId:///0686bc5a-c206-41ef-b40a-79a8259d51d2)  
 Returns a row for the read only routing list of each availability replica in an Always On availability group in the WSFC failover cluster.  
  
 **Column names:** replica_id, routing_priority, read_only_replica_id  
  
 [sys.dm_hadr_availability_replica_cluster_nodes](assetId:///dbd7e416-badd-4332-a45c-438aa0145a99)  
 Returns a row for every availability replica (regardless of join state) of the Always On availability groups in the Windows Server Failover Clustering (WSFC) cluster.  
  
 **Column names:** group_name, replica_server_name, node_name  
  
 [sys.dm_hadr_availability_replica_cluster_states](assetId:///2e0dd780-6a71-4f4b-b7f7-6e063bec71d6)  
 Returns a row for each replica (regardless of join state) of all Always On availability groups (regardless of replica location) in the Windows Server Failover Clustering (WSFC) cluster.  
  
 **Column names:** replica_id, replica_server_name, group_id, join_state, join_state_desc  
  
 [sys.dm_hadr_availability_replica_states](assetId:///d2e678bb-51e8-4a61-b223-5c0b8d08b8b1)  
 Returns a row showing the state of each local availability replica and a row for each remote availability replica in the same availability group.  
  
 **Column names:** replica_id, group_id, is_local, role, role_desc, operational_state, operational_state_desc, connected_state, connected_state_desc, recovery_health, recovery_health_desc, synchronization_health, synchronization_health_desc, last_connect_error_number, last_connect_error_description, and last_connect_error_timestamp  
  
 [sys.fn_hadr_backup_is_preferred_replica](assetId:///61b9be77-e2f6-4da1-b2ae-a62cbe226145)  
 Determines whether the current replica is the preferred backup replica.  
  
> [!NOTE]  
>  For information about performance counters for availability replicas (the **SQLServer:Availability Replica**  performance object), see [SQL Server, Availability Replica](../../Topics/TopicNameNotContainA/SQL-Server--Availability-Replica.md).  
  
##  <a name="AvDbs"></a> Monitoring Availability Databases  
 To monitor availability databases, use the following views:  
  
 [sys.availability_databases_cluster](assetId:///8d9c57e5-7f39-4315-b466-92748231140a)  
 Contains one row for each database on the instance of SQL Server that are part of all Always On Availability Groups in the cluster, regardless of whether the local copy database has been joined to the availability group yet.  
  
> [!NOTE]  
>  When a database is added to an availability group, the primary database is automatically joined to the group. Secondary databases must be prepared on each secondary replica before they can be joined to the availability group.  
  
 **Column names:** group_id, group_database_id, database_name  
  
 [sys.databases](assetId:///46c288c1-3410-4d68-a027-3bbf33239289)  
 Contains one row per database in the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. If a database belongs to an availability replica, the row for that database displays the GUID of the replica and the unique identifier of the database within its availability group.  
  
 **[!INCLUDE[ssHADR](../../Topics/TopicNameContainA/tokens/ssHADR_md.md)] column names:** replica_id, group_database_id  
  
 [sys.dm_hadr_auto_page_repair](assetId:///d7840adf-4a1b-41ac-bc94-102c07ad1c79)  
 Returns a row for every automatic page-repair attempt on any availability database on an availability replica that is hosted for any availability group by the server instance. This view contains rows for the latest automatic page-repair attempts on a given primary or secondary database, with a maximum of 100 rows per database. As soon as a database reaches the maximum, the row for its next automatic page-repair attempt replaces one of the existing entries.  
  
 **Column names:** database_id, file_id, page_id, error_type, page_status, modification_time  
  
 [sys.dm_hadr_database_replica_states](assetId:///1a17b0c9-2535-4f3d-8013-cd0a6d08f773)  
 Returns a row for each database that is participating in any availability group for which the local instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is hosting an availability replica.  
  
 **Column names:** database_id, group_id, replica_id, group_database_id, is_local, synchronization_state, synchronization_state_desc, is_commit_participant, synchronization_health, synchronization_health_desc, database_state, database_state_desc, is_suspended, suspend_reason, suspend_reason_desc, recovery_lsn, truncation_lsn, last_sent_lsn, last_sent_time, last_received_lsn, last_received_time, last_hardened_lsn, last_hardened_time, last_redone_lsn, last_redone_time, log_send_queue_size, log_send_rate, redo_queue_size, redo_rate, filestream_send_rate, end_of_log_lsn, last_commit_lsn, last_commit_time, low_water_mark_for_ghosts  
  
 [sys.dm_hadr_database_replica_cluster_states](assetId:///6f719071-ebce-470d-aebd-1f55ee8cd70a)  
 Returns a row containing information intended to provide you with insight into the health of the availability databases in each availability group on the Windows Server Failover Clustering (WSFC) cluster. This dynamic management view is useful when planning or responding to a failover or for discovering which secondary replica in an availability group is holding up log truncation on a given primary database.  
  
 **Column names:** replica_id, group_database_id, database_name, is_failover_ready, is_pending_secondary_suspend, is_database_joined, recovery_lsn, truncation_lsn  
  
> [!NOTE]  
>  The primary replica location is the authoritative source for an availability group.  
  
> [!NOTE]  
>  For information about the [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/tokens/ssHADR_md.md)] performance counters for availability databases (the **SQLServer:Database Replica** performance object), see [SQL Server, Database Replica](../../Topics/TopicNameNotContainA/SQL-Server--Database-Replica.md). Also, to monitor transaction-log activity on availability databases, use the following counters of the **SQLServer:Databases** performance object: **Log Flush Write Time (ms)**, **Log Flushes/sec**, **Log Pool Cache Misses/sec**, **Log Pool Disk Reads/sec**, and **Log Pool Requests/sec**. For more information, see [SQL Server, Databases Object](../../Topics/TopicNameNotContainA/SQL-Server--Databases-Object.md).  
  
##  <a name="AGlisteners"></a> Monitoring Availability Group Listeners  
 To monitor the availability group listeners on subnets of the WSFC cluster, use the following views:  
  
 [sys.availability_group_listener_ip_addresses](assetId:///e515fa6b-1354-4110-9b70-ab2e6164c992)  
 Returns a row for every conformant virtual IP address that is currently online for an availability group listener.  
  
 **Column names:** listener_id, ip_address, ip_subnet_mask, is_dhcp, network_subnet_ip, network_subnet_prefix_length, network_subnet_ipv4_mask, state, state_desc  
  
 [sys.availability_group_listeners](assetId:///b5e7d1fb-3ffb-4767-8135-604c575016b1)  
 For a given availability group, returns either zero rows indicating that no network name is associated with the availability group, or returns a row for each availability-group listener configuration in the WSFC cluster.  
  
 **Column names:** group_id, listener_id, dns_name, port, is_conformant, ip_configuration_string_from_cluster  
  
 [sys.dm_tcp_listener_states](assetId:///9997ffed-a4c1-428f-8bac-3b9e4b16d7cf)  
 Returns a row containing dynamic-state information for each TCP listener.  
  
 **Column names:** listener_id, ip_address, is_ipv4, port, type, type_desc, state, state_desc, start_time  
  
 **Primary key:** listener_id  
  
 For information about availability group listeners, see [Availability Group Listeners, Client Connectivity, and Application Failover (SQL Server)](../../Topics/TopicNameNotContainA/Availability-Group-Listeners--Client-Connectivity--and-Application-Failover--SQL-Server-.md).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **Always On Availability Groups monitoring tasks:**  
  
-   [Use the Object Explorer Details to Monitor Availability Groups (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Use-the-Object-Explorer-Details-to-Monitor-Availability-Groups--SQL-Server-Management-Studio-.md)  
  
-   [View Availability Group Properties (SQL Server)](../../Topics/TopicNameNotContainA/View-Availability-Group-Properties--SQL-Server-.md)  
  
-   [View Availability Replica Properties (SQL Server)](../../Topics/TopicNameNotContainA/View-Availability-Replica-Properties--SQL-Server-.md)  
  
-   [View Availability Group Listener Properties (SQL Server)](../../Topics/TopicNameNotContainA/View-Availability-Group-Listener-Properties--SQL-Server-.md)  
  
 **Always On Availability Groups monitoring reference (Transact-SQL):**  
  
-   [SERVERPROPERTY (Transact-SQL)](assetId:///11e166fa-3dd2-42d8-ac4b-04f18c612c4a)  
  
-   [sys.availability_group_listener_ip_addresses (Transact-SQL)](assetId:///e515fa6b-1354-4110-9b70-ab2e6164c992)  
  
-   [sys.availability_group_listeners (Transact-SQL)](assetId:///b5e7d1fb-3ffb-4767-8135-604c575016b1)  
  
-   [sys.availability_databases_cluster (Transact-SQL)](assetId:///8d9c57e5-7f39-4315-b466-92748231140a)  
  
-   [sys.availability_groups (Transact-SQL)](assetId:///da7fa55f-c008-45d9-bcfc-3513b02d9e71)  
  
-   [sys.availability_read_only_routing_lists (Transact-SQL)](assetId:///0686bc5a-c206-41ef-b40a-79a8259d51d2)  
  
-   [sys.availability_replicas (Transact-SQL)](assetId:///0a06e9b6-a1e4-4293-867b-5c3f5a8ff62c)  
  
-   [sys.dm_hadr_availability_replica_cluster_nodes (Transact-SQL)](assetId:///dbd7e416-badd-4332-a45c-438aa0145a99)  
  
-   [sys.dm_hadr_availability_replica_cluster_states (Transact-SQL)](assetId:///2e0dd780-6a71-4f4b-b7f7-6e063bec71d6)  
  
-   [sys.database_mirroring_endpoints (Transact-SQL)](assetId:///f2285199-97ad-473c-a52d-270044dd862b)  
  
-   [sys.dm_hadr_auto_page_repair (Transact-SQL)](assetId:///d7840adf-4a1b-41ac-bc94-102c07ad1c79)  
  
-   [sys.dm_hadr_availability_group_states (Transact-SQL)](assetId:///d18019dd-f8dc-4492-b035-b1a639369b65)  
  
-   [sys.dm_hadr_availability_replica_cluster_states (Transact-SQL)](assetId:///2e0dd780-6a71-4f4b-b7f7-6e063bec71d6)  
  
-   [sys.dm_hadr_availability_replica_states (Transact-SQL)](assetId:///d2e678bb-51e8-4a61-b223-5c0b8d08b8b1)  
  
-   [sys.dm_hadr_database_replica_states (Transact-SQL)](assetId:///1a17b0c9-2535-4f3d-8013-cd0a6d08f773)  
  
-   [sys.dm_hadr_database_replica_cluster_states (Transact-SQL)](assetId:///6f719071-ebce-470d-aebd-1f55ee8cd70a)  
  
-   [sys.dm_hadr_cluster (Transact-SQL)](assetId:///13ce70e4-9d43-4a80-a826-099e6213bf85)  
  
-   [sys.dm_hadr_cluster_members (Transact-SQL)](assetId:///feb20b3a-8835-41d3-9a1c-91d3117bc170)  
  
-   [sys.dm_hadr_cluster_networks (Transact-SQL)](assetId:///ece32b15-d63f-4f93-92b7-e2930333e97a)  
  
-   [sys.dm_hadr_database_replica_cluster_states (Transact-SQL)](assetId:///6f719071-ebce-470d-aebd-1f55ee8cd70a)  
  
-   [sys.dm_hadr_database_replica_states (Transact-SQL)](assetId:///1a17b0c9-2535-4f3d-8013-cd0a6d08f773)  
  
-   [sys.dm_hadr_instance_node_map](assetId:///ccfaf62c-9f87-43cf-a5e7-8942e91dd041)  
  
-   [sys.dm_hadr_name_id_map](assetId:///e07bb8a9-37de-4a39-a257-950d7c3ae8fb)  
  
-   [sys.dm_os_performance_counters (Transact-SQL)](assetId:///a1c3e892-cd48-40d4-b6be-2a9246e8fbff)  
  
-   [sys.dm_tcp_listener_states (Transact-SQL)](assetId:///9997ffed-a4c1-428f-8bac-3b9e4b16d7cf)  
  
-   [sys.fn_hadr_backup_is_preferred_replica](assetId:///61b9be77-e2f6-4da1-b2ae-a62cbe226145)  
  
 **Always On performance counters:**  
  
-   [SQL Server, Availability Replica](../../Topics/TopicNameNotContainA/SQL-Server--Availability-Replica.md)  
  
-   [SQL Server, Database Replica](../../Topics/TopicNameNotContainA/SQL-Server--Database-Replica.md)  
  
-   [SQL Server, Databases Object](../../Topics/TopicNameNotContainA/SQL-Server--Databases-Object.md)  
  
 **Policy-based management for Always On Availability Groups**  
  
-   [Use Always On Policies to View the Health of an Availability Group (SQL Server)](../../Topics/TopicNameNotContainA/Use-Always-On-Policies-to-View-the-Health-of-an-Availability-Group--SQL-Server-.md)  
  
-   [Use the Always On Dashboard (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Use-the-Always-On-Dashboard--SQL-Server-Management-Studio-.md)  
  
## See Also  
 [Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Always-On-Availability-Groups--SQL-Server-.md)   
 [Overview of Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Overview-of-Always-On-Availability-Groups--SQL-Server-.md)   
 [Monitoring of Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Monitoring-of-Availability-Groups--SQL-Server-.md)