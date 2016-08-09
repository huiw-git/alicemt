---
title: "View Availability Group Listener Properties (SQL Server)"
ms.custom: na
ms.date: 2016-05-17
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aca0d016-3228-40b8-bdc3-285ed6d9b280
caps.latest.revision: 18
caps.handback.revision: 0
manager: jhubbard
---
# View Availability Group Listener Properties (SQL Server)
This topic describes how to view the properties of an Always On *availability group listener* by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)].  
  
-   **To view listener properties, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 **To view listener properties**  
  
1.  In Object Explorer, connect to a server instance that hosts any availability replica of the availability group whose listener you want to view. Click the server name to expand the server tree.  
  
2.  Expand the **Always On High Availability** node and the **Availability Groups** node.  
  
3.  Expand the node of the availability group, and expand the **Availability Groups Listeners** node.  
  
4.  Right-click the listener that you want to view, and select the **Properties** command.  
  
5.  This opens the **Availability Group Listener Properties** dialog box. For more information, see [Availability Group Listener Properties (Dialog Box)](#AgListenerPropertiesDialog), later in this topic.  
  
###  <a name="AgListenerPropertiesDialog"></a> Availability Group Listener Properties (Dialog Box)  
 **Listener DNS Name**  
 The network name of the availability group listener.  
  
 **Port**  
 The TPC port used by this listener.  
  
> [!NOTE]  
>  If you are connected the primary replica, you can use this field to modify the port number of the listener. This requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.  
  
 **Network Mode**  
 Indicates the TCP protocol used by the listener, one of:  
  
 **DHCP**  
 The listener uses an dynamic IP address that is assigned by a server running the Dynamic Host Configuration Protocol (DHCP).  
  
 **Static IP**  
 The listener uses one or more Static IP addresses. To access the different subnets, an availability group listener must use static IP addresses.  
  
 The grid displays each of the subnets on which the listener listens and the IP address associated with that subnet.  
  
##  <a name="TsqlProcedure"></a> Using Transact-SQL  
 **To view listener properties**  
  
 To monitor the availability group listeners, use the following views:  
  
 [sys.availability_group_listener_ip_addresses](assetId:///e515fa6b-1354-4110-9b70-ab2e6164c992)  
 Returns a row for every conformant virtual IP address that is currently online for an availability group listener.  
  
 **Column names:** listener_id, ip_address, ip_subnet_mask, is_dhcp, network_subnet_ip, network_subnet_prefix_length, network_subnet_ipv4_mask, state, state_desc  
  
 [sys.availability_group_listeners](assetId:///b5e7d1fb-3ffb-4767-8135-604c575016b1)  
 For a given availability group, returns either zero rows indicating that no network name is associated with the availability group, or returns a row for each availability-group listener configuration in the WSFC cluster.  
  
 **Column names:** group_id, listener_id, dns_name, port, is_conformant, ip_configuration_string_from_cluster  
  
 [sys.dm_tcp_listener_states](assetId:///9997ffed-a4c1-428f-8bac-3b9e4b16d7cf)  
 Returns a row containing dynamic-state information for each TCP listener.  
  
 **Column names:** listener_id, ip_address, is_ipv4, port, type, type_desc, state, state_desc, start_time  
  
> [!NOTE]  
>  For more information about using [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] to monitor your [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/tokens/ssHADR_md.md)] environment, see [Monitor Availability Groups (Transact-SQL)](../../Topics/TopicNameNotContainA/Monitor-Availability-Groups--Transact-SQL-.md).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Create or Configure an Availability Group Listener (SQL Server)](../../Topics/TopicNameNotContainA/Create-or-Configure-an-Availability-Group-Listener--SQL-Server-.md)  
  
-   [Remove an Availability Group Listener (SQL Server)](../../Topics/TopicNameNotContainA/Remove-an-Availability-Group-Listener--SQL-Server-.md)  
  
## See Also  
 [Overview of Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Overview-of-Always-On-Availability-Groups--SQL-Server-.md)   
 [Availability Group Listeners, Client Connectivity, and Application Failover (SQL Server)](../../Topics/TopicNameNotContainA/Availability-Group-Listeners--Client-Connectivity--and-Application-Failover--SQL-Server-.md)   
 [Monitor Availability Groups (Transact-SQL)](../../Topics/TopicNameNotContainA/Monitor-Availability-Groups--Transact-SQL-.md)