---
title: Upgrade a SQL Server Failover Cluster Instance
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: daac41fe-7d0b-4f14-84c2-62952ad8cbfa
---
# Upgrade a SQL Server Failover Cluster Instance
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] supports upgrading a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster to a new version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], to a new [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]service pack or cumulative update, or when installing to a new Windows service pack or cumulative update  separately on all failover cluster nodes with downtime limited to a single manual failover \(or two manual failovers if failing back to the original primary\).  
  
 Upgrading the Windows operating system of a failover cluster is not supported for operating systems before Windows Server 2012 R2. To upgrade a cluster node running on Windows Server 2012 R2, see [Cluster Operating System Rolling Upgrade](https://technet.microsoft.com/en-us/library/dn850430.aspx)  
  
 Support details are as follows:  
  
-   [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]upgrade is supported both through the user interface and from the command prompt. You can run upgrade from the command prompt on each failover cluster node, or by using the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup UI  to upgrade each cluster node.  For more information, see [Upgrade a SQL Server Failover Cluster Instance &#40;Setup&#41;](../Topic/Upgrade%20a%20SQL%20Server%20Failover%20Cluster%20Instance%20\(Setup\).md) and [Install SQL Server 2016 from the Command Prompt](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016-from-the-Command-Prompt.md).  
  
-   The following scenarios are not supported as part of a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] upgrade:  
  
    -   You cannot upgrade from a stand\-alone instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to a failover cluster.  
  
    -   You cannot add features to a failover cluster. For example, you cannot add the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] to an existing [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]\-only failover cluster.  
  
    -   You cannot downgrade a failover cluster node to a stand\-alone instance.  
  
    -   Changing the edition of the failover cluster is limited to certain scenarios. For more information, see [Supported Version and Edition Upgrades](../../Topics\TopicNameNotContainA/Supported-Version-and-Edition-Upgrades.md).  
  
-   During the failover cluster upgrade, downtime is limited to failover time and the time that is required for upgrade scripts to run. If you follow the failover cluster rolling upgrade process below and meet all prerequisites on all nodes before you begin the upgrade process, your downtime is minimal. Upgrading SQL Server 2014 when memory\-optimized tables are in use will take some extra time. For more information, see [Plan and Test the Database Engine Upgrade Plan](../../Topics\TopicNameNotContainA/Plan-and-Test-the-Database-Engine-Upgrade-Plan.md).  
  
## Prerequisites  
 Before you begin, review the following important information:  
  
-   [Supported Version and Edition Upgrades](../../Topics\TopicNameNotContainA/Supported-Version-and-Edition-Upgrades.md): Verify that you can upgrade to SQL Server 2016 from your version of the Windows operating system and version of SQL Server. For example, you cannot upgrade directly from a SQL Server 2005 failover clustering instance to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] or upgrade a failover cluster running on Windows Server 2003.  
  
-   [Choose a Database Engine Upgrade Method](../../Topics\TopicNameContainA/Choose-a-Database-Engine-Upgrade-Method.md): Select the appropriate upgrade method and steps based on your review of supported version and edition upgrades and also based on other components installed in your environment to upgrade components in the correct order.  
  
-   [Plan and Test the Database Engine Upgrade Plan](../../Topics\TopicNameNotContainA/Plan-and-Test-the-Database-Engine-Upgrade-Plan.md): Review the release notes and known upgrade issues, the pre\-upgrade checklist, and develop and test the upgrade plan.  
  
-   [Hardware and Software Requirements for Installing SQL Server 2016](../../Topics\TopicNameNotContainA/Hardware-and-Software-Requirements-for-Installing-SQL-Server-2016.md):  Review the software requirements for installing [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. If additional software is required, install it on each node before you begin the upgrade process to minimize any downtime.  
  
## Performing a Rolling Upgrade or Update  
 To upgrade a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup to upgrade each failover cluster node, one at a time, starting with the passive nodes. As you upgrade each node, it is left out of the possible owners of the failover cluster. If there is an unexpected failover, the upgraded nodes do not participate in the failover until cluster resource group ownership is moved to an upgraded node by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup.  
  
 By default, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup automatically determines when to fail over to an upgraded node. This depends on the total number of nodes in the failover cluster instance and the number of nodes that have already been upgraded. When half of the nodes or more have already been upgraded, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup causes a failover to an upgraded node when you perform upgrade on the next node. Upon failover to an upgraded node, the cluster group is moved to an upgraded node. All the upgraded nodes are put in the possible owners list and all the nodes that are not yet upgraded are removed from the possible owners list. As you upgrade each remaining node, it is added to the possible owners of the failover cluster.  
  
 This process results in downtime limited to one failover time and database upgrade script execution time during the whole failover cluster upgrade.  
  
 To control the failover behavior of cluster nodes during the upgrade process, run the upgrade operation at the command prompt and use the \/FAILOVERCLUSTERROLLOWNERSHIP parameter. For more information, see [Install SQL Server 2016 from the Command Prompt](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016-from-the-Command-Prompt.md).  
  
## See Also  
 [Upgrade to SQL Server 2016 Using the Installation Wizard &#40;Setup&#41;](../Topic/Upgrade%20to%20SQL%20Server%202016%20Using%20the%20Installation%20Wizard%20\(Setup\).md)   
 [Install SQL Server 2016 from the Command Prompt](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016-from-the-Command-Prompt.md)   
 [Upgrade a SQL Server Failover Cluster Instance &#40;Setup&#41;](../Topic/Upgrade%20a%20SQL%20Server%20Failover%20Cluster%20Instance%20\(Setup\).md)  
  
  