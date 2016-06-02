---
title: Always On Policies for Operational Issues with Always On Availability Groups (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: afa5289c-641a-4c03-8749-44862384ec5f
---
# Always On Policies for Operational Issues with Always On Availability Groups (SQL Server)
  The [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] health model evaluates a set of predefined policy based management \(PBM\) policies. You can use theses for viewing the health of an availability group and its availability replicas and databases in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
 **In this Topic:**  
  
-   [Terms and Definitions](#TermsAndDefinitions)  
  
-   [Predefined Policies and Issues](#Always OnPBM)  
  
-   [Always On Dashboard](#Dashboard)  
  
-   [Extending the Always On Health Model](#ExtendHealthModel)  
  
-   [Related Tasks](#RelatedTasks)  
  
-   [Related Content](#RelatedContent)  
  
##  <a name="TermsAndDefinitions"></a> Terms and Definitions  
 Always On predefined policies  
 A set of built\-in policies that allow a database administrator to check an availability group and its availability replicas and databases for compliance with the states that are defined by the Always On policies.  
  
 [Always On Availability Groups](../Topic/Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)  
 A high\-availability and disaster\-recovery solution that provides an enterprise\-level alternative to database mirroring.  
  
 availability group  
 A container for a discrete set of user databases, known as *availability databases*, that fail over together.  
  
 availability replica  
 An instantiation of an availability group that is hosted by a specific instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and that maintains a local copy of each availability database that belongs to the availability group. Two types of availability replicas exist: a single *primary replica* and one to four *secondary replicas*. The server instances that host the availability replicas for a given availability group must reside on different nodes of a single Windows Server Failover Clustering \(WSFC\) cluster.  
  
 availability database  
 A database that belongs to an availability group. For each availability database, the availability group maintains a single read\-write copy \(the *primary database*\) and one to four read\-only copies \(*secondary databases*\).  
  
 Always On Dashboard  
 A [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] dashboard that provides an at\-a\-glance view of the health of an availability group. For more information, see [Always On Dashboard](#Dashboard), later in this topic.  
  
##  <a name="Always OnPBM"></a> Predefined Policies and Issues  
 The following table summarizes the predefined policies.  
  
|Policy name|Issue|Category**\***|Facet|  
|-----------------|-----------|--------------------|-----------|  
|WSFC Cluster State|[WSFC cluster service is offline](../../Topics\TopicNameNotContainA/WSFC-cluster-service-is-offline.md).|Critical|Instance of SQL Server|  
|Availability Group Online State|[Availability group is offline](../../Topics\TopicNameNotContainA/Availability-group-is-offline.md).|Critical|Availability group|  
|Availability Group Automatic Failover Readiness|[Availability group is not ready for automatic failover](../../Topics\TopicNameNotContainA/Availability-group-is-not-ready-for-automatic-failover.md).|Critical|Availability group|  
|Availability Replicas Data Synchronization State|[Some availability replicas are not synchronizing data](../../Topics\TopicNameNotContainA/Some-availability-replicas-are-not-synchronizing-data.md).|Warning|Availability group|  
|Synchronous Replicas Data Synchronization State|[Some synchronous replicas are not synchronized](../../Topics\TopicNameNotContainA/Some-synchronous-replicas-are-not-synchronized.md).|Warning|Availability group|  
|Availability Replicas Role State|[Some availability replicas do not have a healthy role](../../Topics\TopicNameContainA/Some-availability-replicas-do-not-have-a-healthy-role.md).|Warning|Availability group|  
|Availability Replicas Connection State|[Some availability replicas are disconnected](../../Topics\TopicNameNotContainA/Some-availability-replicas-are-disconnected.md).|Warning|Availability group|  
|Availability Replica Role State|[Availability replica does not have a healthy role](../../Topics\TopicNameContainA/Availability-replica-does-not-have-a-healthy-role.md).|Critical|Availability replica|  
|Availability Replica Connection State|[Availability replica is disconnected](../../Topics\TopicNameNotContainA/Availability-replica-is-disconnected.md).|Critical|Availability replica|  
|Availability Replica Join State|[Availability replica is not joined](../../Topics\TopicNameNotContainA/Availability-replica-is-not-joined.md).|Warning|Availability replica|  
|Availability Replica Data Synchronization State|[Data synchronization state of some availability database is not healthy](../../Topics\TopicNameNotContainA/Data-synchronization-state-of-some-availability-database-is-not-healthy.md).|Warning|Availability replica|  
|Availability Database Suspension State|[Availability database is suspended](../../Topics\TopicNameNotContainA/Availability-database-is-suspended.md).|Warning|Availability database|  
|Availability Database Join State|[Secondary database is not joined](../../Topics\TopicNameNotContainA/Secondary-database-is-not-joined.md).|Warning|Availability database|  
|Availability Database Data Synchronization State|[Data synchronization state of availability database is not healthy](../../Topics\TopicNameNotContainA/Data-synchronization-state-of-availability-database-is-not-healthy.md).|Warning|Availability database|  
  
> [!IMPORTANT]  
>  **\*** For Always On policies, the category names are used as IDs. Changing the name of an Always On category would break its health\-evaluation functionality. Therefore, do not modify the names of Always On categories.  
  
##  <a name="Dashboard"></a> Always On Dashboard  
 The Always On Dashboard gives you an at\-a\-glance view of the health of an availability group. The Always On Dashboard includes the following features:  
  
-   Enables you to easily display details about a given availability group, its availability replicas, and its databases.  
  
-   Displays visual indications of key states to help database administrators make quick operational decisions.  
  
-   Provides launch points for troubleshooting scenarios.  
  
-   For a given operational issue, populates the **Policy Evaluation Result** dialog box with information about specific Always On health policy violations and with links to remediation help.  
  
-   Provides an health extended event viewer to show previous events for Always On\-specific issues.  
  
-   If failing over the availability group is a possible remediation for an issue, provides a launch point for the links[Fail Over Availability Group Wizard](../Topic/Use%20the%20Fail%20Over%20Availability%20Group%20Wizard%20\(SQL%20Server%20Management%20Studio\).md). This wizard takes a database administrator through the manual failover process.  
  
##  <a name="ExtendHealthModel"></a> Extending the Always On Health Model  
 Extending the [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] health model is simply a matter of creating your own user\-defined policies and putting them into certain categories based on the type of object that you are monitoring.  After you a alter few settings, the Always On dashboard will automatically evaluate your own user\-defined policies, as well as the Always On predefined policies.  
  
 A user\-defined policy can use any of the available PBM facets, including those used by the Always On predefined policies \(see [Predefined Policies and Issues](#Always OnPBM), earlier in this topic\). The Server facet provides the following properties for monitoring [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] health: \(**IsHadrEnabled** and **HadrManagerStatus**\). The Server facet also provides properties the following policies for monitoring the WSFC cluster configuration: **ClusterQuorumType**, and **ClusterQuorumState**.  
  
 For more information, see [The Always On Health Model Part 2 \-\- Extending the Health Model](http://blogs.msdn.com/b/sqlAlways On/archive/2012/02/13/extending-the-Always) \(a SQL Server Always On Team blog\).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Use Always On Policies to View the Health of an Availability Group &#40;SQL Server&#41;](../Topic/Use%20Always%20On%20Policies%20to%20View%20the%20Health%20of%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Use the Always On Dashboard &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Always%20On%20Dashboard%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [WSFC Disaster Recovery through Forced Quorum &#40;SQL Server&#41;](../Topic/WSFC%20Disaster%20Recovery%20through%20Forced%20Quorum%20\(SQL%20Server\).md)  
  
-   [Force a WSFC Cluster to Start Without a Quorum](../../Topics\TopicNameContainA/Force-a-WSFC-Cluster-to-Start-Without-a-Quorum.md)  
  
-   [Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;](../Topic/Perform%20a%20Forced%20Manual%20Failover%20of%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Troubleshoot a Failed Add-File Operation &#40;Always On Availability Groups&#41;](../Topic/Troubleshoot%20a%20Failed%20Add-File%20Operation%20\(Always%20On%20Availability%20Groups\).md)  
  
##  <a name="RelatedContent"></a> Related Content  
  
-   [The Always On Health Model Part 1 \-\- Health Model Architecture](http://blogs.msdn.com/b/sqlAlways On/archive/2012/02/13/extending-the-Always)  
  
-   [The Always On Health Model Part 2 \-\- Extending the Health Model](http://blogs.msdn.com/b/sqlAlways On/archive/2012/02/13/extending-the-Always)  
  
-   [Microsoft SQL Server Always On Solutions Guide for High Availability and Disaster Recovery](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
## See Also  
 [Always On Availability Groups &#40;SQL Server&#41;](../Topic/Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Administration of an Availability Group &#40;SQL Server&#41;](../Topic/Administration%20of%20an%20Availability%20Group%20\(SQL%20Server\).md)   
 [Monitoring of Availability Groups &#40;SQL Server&#41;](../Topic/Monitoring%20of%20Availability%20Groups%20\(SQL%20Server\).md)  
  
  