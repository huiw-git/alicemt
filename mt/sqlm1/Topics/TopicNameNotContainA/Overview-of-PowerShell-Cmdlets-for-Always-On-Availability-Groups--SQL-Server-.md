---
title: Overview of PowerShell Cmdlets for Always On Availability Groups (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b3fef0d5-b6d7-4386-a0f0-d06c165ad4de
---
# Overview of PowerShell Cmdlets for Always On Availability Groups (SQL Server)
  [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] PowerShell is a task\-based command\-line shell and scripting language designed especially for system administration. [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] provides a set of PowerShell cmdlets in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] that enable you to deploy, manage, and monitor availability groups, availability replicas, and availability databases.  
  
> [!NOTE]  
>  A PowerShell cmdlet can complete by successfully initiating an action. This does not indicate that the intended work, such as the fail over of an availability group, has completed. When scripting a sequence of actions, you might have to check the status of actions, and wait for them to complete.  
  
 This topic introduces the cmdlets for the following sets of tasks:  
  
-   [Configuring a server instance for Always On Availability Groups](#ConfiguringServerInstance)  
  
-   [Backing up and restoring databases and transaction logs](#BnRcmdlets)  
  
-   [Creating and managing an availability group](#DeployManageAGs)  
  
-   [Creating and managing an availability group listener](#AGlisteners)  
  
-   [Creating and managing an availability replica](#DeployManageARs)  
  
-   [Adding and managing an availability database](#DeployManageDbs)  
  
-   [Monitoring availability group health](#MonitorTblshtAGs)  
  
> [!NOTE]  
>  For a list of topics in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Books Online that describe how to use cmdlets to perform [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] tasks, see the "Related Tasks" section of [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md).  
  
##  <a name="ConfiguringServerInstance"></a> Configuring a Server Instance for Always On Availability Groups  
  
|Cmdlets|Description|Supported on|  
|-------------|-----------------|------------------|  
|**Disable\-SqlAlways On**|Disables the [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] feature on a server instance.|The server instance that is specified by the **Path**, **InputObject**, or **Name** parameter. \(Must be an edition of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that supports [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)].\)|  
|**Enable\-SqlAlways On**|Enables [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] on an instance of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] that supports the [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] feature. For information about support for [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)], see [Prerequisites, Restrictions, and Recommendations for Always On Availability Groups &#40;SQL Server&#41;](../Topic/Prerequisites,%20Restrictions,%20and%20Recommendations%20for%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md).|Any edition of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that supports [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)].|  
|**New\-SqlHadrEndPoint**|Creates a new database mirroring endpoint on a server instance. This endpoint is required for data movement between primary and secondary databases.|Any instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]|  
|**Set\-SqlHadrEndpoint**|Changes the properties of an existing database mirroring endpoint, such as the name, state, or authentication properties.|A server instance that supports [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] and lacks a database mirroring endpoint|  
  
##  <a name="BnRcmdlets"></a> Backing Up and Restoring Databases and Transaction Logs  
  
|Cmdlets|Description|Supported on|  
|-------------|-----------------|------------------|  
|**Backup\-SqlDatabase**|Creates a data or log backup.|Any online database \(for [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)], a database on the server instance that hosts the primary replica\)|  
|**Restore\-SqlDatabase**|Restores a backup.|Any instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] \(for [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)], a server instance that hosts a secondary replica\)<br /><br /> **\*\* Important \*\*** When preparing a secondary database, you must use the **\-NoRecovery** parameter in every **Restore\-SqlDatabase** command.|  
  
 For information about using these cmdlets to prepare a secondary database, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](../Topic/Manually%20Prepare%20a%20Secondary%20Database%20for%20an%20Availability%20Group%20\(SQL%20Server\).md).  
  
##  <a name="DeployManageAGs"></a> Creating and Managing an Availability Group  
  
|Cmdlets|Description|Supported on|  
|-------------|-----------------|------------------|  
|**New\-SqlAvailabilityGroup**|Creates a new availability group.|Server instance to host primary replica|  
|**Remove\-SqlAvailabilityGroup**|Deletes availability group.|HADR\-enabled server instance|  
|**Set\-SqlAvailabilityGroup**|Sets the properties of an availability group; take an availability group online\/offline|Server instance that hosts primary replica|  
|**Switch\-SqlAvailabilityGroup**|Initiates one of the following forms of failover:<br /><br /> A forced failover of an availability group \(with possible data loss\).<br /><br /> A manual failover of an availability group.|Server instance that hosts target secondary replica|  
  
##  <a name="AGlisteners"></a> Creating and Managing an Availability Group Listener  
  
|Cmdlet|Description|Supported on|  
|------------|-----------------|------------------|  
|**New\-SqlAvailabilityGroupListener**|Creates a new availability group listener and attaches it to an existing availability group.|Server instance that hosts primary replica|  
|**Set\-SqlAvailabilityGroupListener**|Modifies the port setting on an existing availability group listener.|Server instance that hosts primary replica|  
|**Add\-SqlAvailabilityGroupListenerStaticIp**|Adds a static IP address to an existing availability group listener configuration. The IP address can be an IPv4 address with subnet, or an IPv6 address.|Server instance that hosts primary replica|  
  
##  <a name="DeployManageARs"></a> Creating and Managing an Availability Replica  
  
|Cmdlets|Description|Supported on|  
|-------------|-----------------|------------------|  
|**New\-SqlAvailabilityReplica**|Creates a new availability replica. You can Use the **\-AsTemplate** parameter to create an in\-memory availability\-replica object for each new availability replica.|Server instance that hosts primary replica|  
|**Join\-SqlAvailabilityGroup**|Joins a secondary replica to the availability group.|Server instance that hosts secondary replica|  
|**Remove\-SqlAvailabilityReplica**|Deletes an availability replica.|Server instance that hosts primary replica|  
|**Set\-SqlAvailabilityReplica**|Sets the properties of an availability replica.|Server instance that hosts primary replica|  
  
##  <a name="DeployManageDbs"></a> Adding and Managing an Availability Database  
  
|Cmdlets|Description|Supported on|  
|-------------|-----------------|------------------|  
|**Add\-SqlAvailabilityDatabase**|On the primary replica, adds a database to an availability group.<br /><br /> On a secondary replica, joins a secondary database to an availability group.|Any server instance that hosts an availability replica \(behavior differs for primary and secondary replicas\)|  
|**Remove\-SqlAvailabilityDatabase**|On the primary replica, removes the database from the availability group.<br /><br /> On a secondary replica, removes the local secondary database from the local secondary replica.|Any server instance that hosts an availability replica \(behavior differs for primary and secondary replicas\)|  
|**Resume\-SqlAvailabilityDatabase**|Resumes the data movement for a suspended availability database.|The server instance on which the database was suspended.|  
|**Suspend\-SqlAvailabilityDatabase**|Suspends the data movement for an availability database.|Any server instance that hosts an availability replica.|  
  
##  <a name="MonitorTblshtAGs"></a> Monitoring Availability Group Health  
 The following [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] cmdlets enable you to monitor the health of an availability group and its replicas and databases.  
  
> [!IMPORTANT]  
>  You must have CONNECT, VIEW SERVER STATE, and VIEW ANY DEFINITION permissions to execute these cmdlets.  
  
|Cmdlet|Description|Supported on|  
|------------|-----------------|------------------|  
|**Test\-SqlAvailabilityGroup**|Assesses the health of an availability group by evaluating SQL Server policy based management \(PBM\) policies.|Any server instance that hosts an availability replica.\*|  
|**Test\-SqlAvailabilityReplica**|Assesses the health of availability replicas by evaluating SQL Server policy based management \(PBM\) policies.|Any server instance that hosts an availability replica.\*|  
|**Test\-SqlDatabaseReplicaState**|Assesses the health of an availability database on all joined availability replicas by evaluating SQL Server policy based management \(PBM\) policies.|Any server instance that hosts an availability replica.\*|  
  
 \*To view information about all of the availability replicas in an availability group, use to the server instance that hosts the primary replica.  
  
 For more information, see [Use Always On Policies to View the Health of an Availability Group &#40;SQL Server&#41;](../Topic/Use%20Always%20On%20Policies%20to%20View%20the%20Health%20of%20an%20Availability%20Group%20\(SQL%20Server\).md).  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Get Help SQL Server PowerShell](../../Topics\TopicNameNotContainA/Get-Help-SQL-Server-PowerShell.md)  
  
  