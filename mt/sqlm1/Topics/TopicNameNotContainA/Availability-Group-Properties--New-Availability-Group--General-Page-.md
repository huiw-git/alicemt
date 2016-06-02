---
title: Availability Group Properties: New Availability Group (General Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9af5379f-91b8-4729-9f75-4a80242a30e9
---
# Availability Group Properties: New Availability Group (General Page)
  This topic applies to the **General** tab of both the **New Availability Group** dialog box and the **Availability Group Properties** dialog box.  The **New Availability Group** dialog box enables you to create a new availability group without using the [!INCLUDE[ssAoNewAgWiz](../../Token\Other/ssAoNewAgWiz_md.md)]. The **Availability Group Properties** dialog box enables you to view and alter the configuration of an existing availability group.  
  
 **To view availability group properties**  
  
-   [View Availability Group Properties &#40;SQL Server&#41;](../Topic/View%20Availability%20Group%20Properties%20\(SQL%20Server\).md)  
  
-   [Use the Always On Dashboard &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Always%20On%20Dashboard%20\(SQL%20Server%20Management%20Studio\).md)  
  
## UIElement List  
 **Availability group name**  
 Name of the availability group. This is a user\-specified name that must be unique within the Windows Server Failover Cluster \(WSFC\).  
  
## Availability Databases  
 **Database Name**  
 Name of a database that has been added to the availability group.  
  
 **Add**  
 Click to add a database to the availability group.  
  
 **Remove**  
 Click to remove a selected database from the availability group.  
  
## Availability Replicas  
 **Server instance**  
 Server name of the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that is hosting this replica and, for a non\-default instance, its instance name.  
  
 **Role**  
 **Primary**  
 Currently the primary replica.  
  
 **Secondary**  
 Currently a secondary replica.  
  
 **Resolving**  
 Currently the replica role is in the process of being resolved to either the primary or secondary role.  
  
 **Availability Mode**  
 The availability mode of the replica, one of:  
  
 **Asynchronous commit**  
 The primary replica can commit transactions without waiting for the secondary to write the log to disk.  
  
 **Synchronous commit**  
 The primary replica waits to commit a given transaction until the secondary replica has written the transaction to disk.  
  
 For more information, see [Availability Modes &#40;Always On Availability Groups&#41;](../Topic/Availability%20Modes%20\(Always%20On%20Availability%20Groups\).md).  
  
 **Failover Mode**  
 The failover mode of the replica, one of:  
  
 **Automatic**  
 Automatic failover. The replica is a target for automatic failovers. This is supported only if the availability mode is set to synchronous commit.  
  
 **Manual**  
 Manual failover. The replica can only be failed over to manually by the database administrator.  
  
 **Connections in Primary Role**  
 The type of client connections supported when the replica owns the primary role.  
  
 **Allow all connections**  
 All connections are allowed to the databases in the primary replica. This is the default setting.  
  
 **Allow read\/write connections**  
 Connections where the Application Intent connection property is set to **ReadOnly** are disallowed. When the Application Intent property is set to **ReadWrite** or the Application Intent connection property is not set, the connection is allowed. For more information about Application Intent connection property, see [Using Connection String Keywords with SQL Server Native Client](../Topic/Using%20Connection%20String%20Keywords%20with%20SQL%20Server%20Native%20Client.md).  
  
 **Readable Secondary**  
 Whether an availability replica that is performing the secondary role \(that is, a secondary replica\) can accept connections from clients, one of:  
  
 **No**  
 No direct connections are allowed to secondary databases of this replica. They are not available for read access. This is the default setting.  
  
 **Read\-intent only**  
 Only direct read\-only connections are allowed to secondary databases of this replica. The secondary database\(s\) are all available for read access.  
  
 **Yes**  
 All connections are allowed to secondary databases of this replica, but only for read access. The secondary database\(s\) are all available for read access.  
  
 **Session Timeout \(seconds\)**  
 The number of seconds for the session\-timeout period on this replica.  
  
 **Endpoint URL**  
 The URL of the endpoint. For information the format of these URLs, see [Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;](../Topic/Specify%20the%20Endpoint%20URL%20When%20Adding%20or%20Modifying%20an%20Availability%20Replica%20\(SQL%20Server\).md).  
  
 **Add**  
 Click to add a secondary replica to the availability group.  
  
 **Remove**  
 Click to remove a secondary replica from the availability group.  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)  
  
  