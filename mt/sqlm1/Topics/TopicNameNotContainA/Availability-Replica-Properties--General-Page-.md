---
title: Availability Replica Properties (General Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8318fefb-e045-4fab-8507-e1951fc7cec6
---
# Availability Replica Properties (General Page)
  Use this dialog box to viewthe properties of an availability replica.  
  
## Task List  
 **To view availability replica properties**  
  
-   [View Availability Replica Properties &#40;SQL Server&#41;](../Topic/View%20Availability%20Replica%20Properties%20\(SQL%20Server\).md)  
  
-   [Use the Always On Dashboard &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Always%20On%20Dashboard%20\(SQL%20Server%20Management%20Studio\).md)  
  
## UIElement List  
 **Availability group name**  
 Name of the availability group. This is a user\-specified name that must be unique within the Windows Server Failover Cluster \(WSFC\).  
  
 **Server instance**  
 Server name of the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that is hosting this replica and, for a non\-default instance, its instance name.  
  
 **Role**  
 **Primary**  
 Currently the primary replica.  
  
 **Secondary**  
 Currently a secondary replica.  
  
 **Resolving**  
 Currently the replica role is in the process of being resolved to either the primary or secondary role.  
  
 **Availability mode**  
 The availability mode of the replica, one of:  
  
 **Asynchronous commit**  
 The primary replica can commit transactions without waiting for the secondary to write the log to disk.  
  
 **Synchronous commit**  
 The primary replica waits to commit a given transaction until the secondary replica has written the transaction to disk.  
  
 For more information, see [Availability Modes &#40;Always On Availability Groups&#41;](../Topic/Availability%20Modes%20\(Always%20On%20Availability%20Groups\).md).  
  
 **Failover mode**  
 The failover mode of the replica, one of:  
  
 **Automatic**  
 Automatic failover. The replica is a target for automatic failovers. This is supported only if the availability mode is set to synchronous commit.  
  
 **Manual**  
 Manual failover. The replica can only be failed over to manually by the database administrator.  
  
 **Connections in primary role**  
 The type of client connections supported when the replica owns the primary role.  
  
 **Allow all connections**  
 All connections are allowed to the databases in the primary replica. This is the default setting.  
  
 **Allow read\/write connections**  
 Connections where the Application Intent connection property is set to **ReadOnly** are disallowed. When the Application Intent property is set to **ReadWrite** or the application intent connection property is not set, the connection is allowed.  
  
 **Readable Secondary**  
 Whether an availability replica that is performing the secondary role \(that is, a secondary replica\) can accept connections from clients, one of:  
  
 **No**  
 No direct connections are allowed to secondary databases of this replica. They are not available for read access. This is the default setting.  
  
 **Read\-intent only**  
 Only direct read\-only connections are allowed to secondary databases of this replica. The secondary database\(s\) are all available for read access.  
  
 **Yes**  
 All connections are allowed to secondary databases of this replica, but only for read access. The secondary database\(s\) are all available for read access.  
  
 For more information, see [Active Secondaries: Readable Secondary Replicas &#40;Always On Availability Groups&#41;](../Topic/Active%20Secondaries:%20Readable%20Secondary%20Replicas%20\(Always%20On%20Availability%20Groups\).md).  
  
 **Session timeout \(seconds\)**  
 The time\-out period, in seconds. The time\-out period is the maximum time that the replica waits to receive a message from another replica before considering connection between the primary and secondary replica have failed. Session timeout detects whether secondaries are connected the primary replica. On detecting a failed connection with a secondary replica, the primary replica considers the secondary replica to be NOT\_SYNCHRONIZED. On detecting a failed connection with the primary replica, a secondary replica simply attempts to reconnect.  
  
> [!NOTE]  
>  Session timeouts do not cause automatic failovers.  
  
 **Endpoint URL**  
 String representation of the user\-specified database mirroring endpoint that is used by connections between primary and secondary replicas for data synchronization. For information about the syntax of endpoint URLs, see [Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;](../Topic/Specify%20the%20Endpoint%20URL%20When%20Adding%20or%20Modifying%20an%20Availability%20Replica%20\(SQL%20Server\).md).  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)  
  
  