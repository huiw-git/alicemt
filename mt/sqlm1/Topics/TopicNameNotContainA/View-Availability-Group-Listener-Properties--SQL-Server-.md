---
title: View Availability Group Listener Properties (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aca0d016-3228-40b8-bdc3-285ed6d9b280
---
# View Availability Group Listener Properties (SQL Server)
  This topic describes how to view the properties of an Always On *availability group listener* by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
-   **To view listener properties, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 **To view listener properties**  
  
1.  In Object Explorer, connect to a server instance that hosts any availability replica of the availability group whose listener you want to view. Click the server name to expand the server tree.  
  
2.  Expand the **Always On High Availability** node and the **Availability Groups** node.  
  
3.  Expand the node of the availability group, and expand the **Availability Groups Listeners** node.  
  
4.  Right\-click the listener that you want to view, and select the **Properties** command.  
  
5.  This opens the **Availability Group Listener Properties** dialog box. For more information, see [Availability Group Listener Properties \(Dialog Box\)](#AgListenerPropertiesDialog), later in this topic.  
  
###  <a name="AgListenerPropertiesDialog"></a> Availability Group Listener Properties \(Dialog Box\)  
 **Listener DNS Name**  
 The network name of the availability group listener.  
  
 **Port**  
 The TPC port used by this listener.  
  
> [!NOTE]  
>  If you are connected the primary replica, you can use this field to modify the port number of the listener. This requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.  
  
 **Network Mode**  
 Indicates the TCP protocol used by the listener, one of:  
  
 **DHCP**  
 The listener uses an dynamic IP address that is assigned by a server running the Dynamic Host Configuration Protocol \(DHCP\).  
  
 **Static IP**  
 The listener uses one or more Static IP addresses. To access the different subnets, an availability group listener must use static IP addresses.  
  
 The grid displays each of the subnets on which the listener listens and the IP address associated with that subnet.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 **To view listener properties**  
  
 To monitor the availability group listeners, use the following views:  
  
 [sys.availability\_group\_listener\_ip\_addresses](../Topic/sys.availability_group_listener_ip_addresses%20\(Transact-SQL\).md)  
 Returns a row for every conformant virtual IP address that is currently online for an availability group listener.  
  
 **Column names:** listener\_id, ip\_address, ip\_subnet\_mask, is\_dhcp, network\_subnet\_ip, network\_subnet\_prefix\_length, network\_subnet\_ipv4\_mask, state, state\_desc  
  
 [sys.availability\_group\_listeners](../Topic/sys.availability_group_listeners%20\(Transact-SQL\).md)  
 For a given availability group, returns either zero rows indicating that no network name is associated with the availability group, or returns a row for each availability\-group listener configuration in the WSFC cluster.  
  
 **Column names:** group\_id, listener\_id, dns\_name, port, is\_conformant, ip\_configuration\_string\_from\_cluster  
  
 [sys.dm\_tcp\_listener\_states](../Topic/sys.dm_tcp_listener_states%20\(Transact-SQL\).md)  
 Returns a row containing dynamic\-state information for each TCP listener.  
  
 **Column names:** listener\_id, ip\_address, is\_ipv4, port, type, type\_desc, state, state\_desc, start\_time  
  
> [!NOTE]  
>  For more information about using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] to monitor your [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] environment, see [Monitor Availability Groups &#40;Transact-SQL&#41;](../Topic/Monitor%20Availability%20Groups%20\(Transact-SQL\).md).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Create or Configure an Availability Group Listener &#40;SQL Server&#41;](../Topic/Create%20or%20Configure%20an%20Availability%20Group%20Listener%20\(SQL%20Server\).md)  
  
-   [Remove an Availability Group Listener &#40;SQL Server&#41;](../Topic/Remove%20an%20Availability%20Group%20Listener%20\(SQL%20Server\).md)  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../Topic/Availability%20Group%20Listeners,%20Client%20Connectivity,%20and%20Application%20Failover%20\(SQL%20Server\).md)   
 [Monitor Availability Groups &#40;Transact-SQL&#41;](../Topic/Monitor%20Availability%20Groups%20\(Transact-SQL\).md)  
  
  