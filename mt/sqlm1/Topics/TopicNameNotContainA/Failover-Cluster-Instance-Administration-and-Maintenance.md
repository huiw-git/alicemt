---
title: Failover Cluster Instance Administration and Maintenance
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2d5c63e9-8061-45c3-94db-8dd3100b8a91
---
# Failover Cluster Instance Administration and Maintenance
  Maintenance tasks like adding or removing nodes from an existing Always On Failover Cluster Instance \(FCI\) are accomplished using the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup program. Other administration tasks like changing the IP address resource, recovering from certain FCI scenarios are accomplished using the Failover Cluster Manager snap\-in, which is the management snap\-in for the Windows Server Failover Clustering \(WSFC\) service.  
  
## Maintaining a Failover Cluster Instance  
 After you have installed an FCI, you can change or repair it using the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup program. For example, you can add additional nodes to an FCI, run an FCI as a stand\-alone instance, or remove a node from a FCI configuration.  
  
### Adding a Node to an Existing Failover Cluster Instance  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup gives you the option of maintaining an existing FCI. If you choose this option, you can add other nodes to your FCI by running [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup on the computer that you want to add to the FCI. For more information, see [Create a New SQL Server Failover Cluster &#40;Setup&#41;](../Topic/Create%20a%20New%20SQL%20Server%20Failover%20Cluster%20\(Setup\).md) and [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](../Topic/Add%20or%20Remove%20Nodes%20in%20a%20SQL%20Server%20Failover%20Cluster%20\(Setup\).md).  
  
### Removing a Node from an Existing Failover Cluster Instance  
 You can remove a node from an FCI by running [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup on the computer that you want to remove from the FCI. Each node in an FCI is considered a peer without dependencies on other nodes on the FCI, and you can remove any node. A damaged node does not have to be available to be removed, and the removal process does not uninstall the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] binaries from the unavailable node. A removed node can be added back to a FCI at any time. For more information, see [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](../Topic/Add%20or%20Remove%20Nodes%20in%20a%20SQL%20Server%20Failover%20Cluster%20\(Setup\).md).  
  
### Changing Service Accounts  
 You should not change passwords for any of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service accounts when an FCI node is down or offline. If you must do this, you must reset the password again by using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager when all nodes are back online.  
  
 If the service account for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is not an administrator in your cluster, the administrative shares cannot be deleted on any nodes of the cluster. The administrative shares must be available in a cluster for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to function.  
  
> [!IMPORTANT]  
>  Do not use the same account for the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service account and the WSFC service account. If the password changes for the WSFC service account, your [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installation will fail.  
  
 On [!INCLUDE[nextref_longhorn](../../Token\Other/nextref_longhorn_md.md)], service SIDs are used for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service accounts. For more information, see [Configure Windows Service Accounts and Permissions](../../Topics\TopicNameNotContainA/Configure-Windows-Service-Accounts-and-Permissions.md).  
  
## Administering a Failover Cluster Instance  
  
|Task Description|Topic Link|  
|----------------------|----------------|  
|Describes how to add dependencies to a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] resource.|[Add Dependencies to a SQL Server Resource](../../Topics\TopicNameContainA/Add-Dependencies-to-a-SQL-Server-Resource.md)|  
|Kerberos is a network authentication protocol designed to provide strong authentication for client\/server applications. Kerberos provides a foundation for interoperability and helps to enhance the security of enterprise\-wide network authentication. You can use Kerberos authentication with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] stand\-alone instances or with Always On FCIs.|[Register a Service Principal Name for Kerberos Connections](../../Topics\TopicNameContainA/Register-a-Service-Principal-Name-for-Kerberos-Connections.md).|  
|Provides links to content that describes how to enable Kerberos authentication||  
|Describes the procedure used to recover from a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster failure.|[Recover from Failover Cluster Instance Failure](../../Topics\TopicNameNotContainA/Recover-from-Failover-Cluster-Instance-Failure.md)|  
|Describe the procedure used to change the IP address resource for a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster instance.|[Change the IP Address of a Failover Cluster Instance](../../Topics\TopicNameContainA/Change-the-IP-Address-of-a-Failover-Cluster-Instance.md)|  
  
## See Also  
 [Configure HealthCheckTimeout Property Settings](../../Topics\TopicNameNotContainA/Configure-HealthCheckTimeout-Property-Settings.md)   
 [Configure FailureConditionLevel Property Settings](../../Topics\TopicNameNotContainA/Configure-FailureConditionLevel-Property-Settings.md)   
 [View and Read Failover Cluster Instance Diagnostics Log](../../Topics\TopicNameNotContainA/View-and-Read-Failover-Cluster-Instance-Diagnostics-Log.md)  
  
  