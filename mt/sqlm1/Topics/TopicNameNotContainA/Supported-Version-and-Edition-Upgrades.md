---
title: Supported Version and Edition Upgrades
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 702359c4-6ca9-42a8-860c-a95a802898a1
---
# Supported Version and Edition Upgrades
  You can upgrade from [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], and [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)]. This topic lists the supported upgrade paths from these [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] versions, and the supported edition upgrades for [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
## Pre upgrade Checklist  
  
-   Before upgrading from one edition of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] to another, verify that the functionality you are currently using is supported in the edition to which you are moving.  
  
-   Before upgrading [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], enable Windows Authentication for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent and verify the default configuration: that the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent service account is a member of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] sysadmin group.  
  
-   To upgrade to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], you must be running a supported operating system. For more information, see [Hardware and Software Requirements for Installing SQL Server 2016](../../Topics\TopicNameNotContainA/Hardware-and-Software-Requirements-for-Installing-SQL-Server-2016.md).  
  
-   Upgrade will be blocked if there is a pending restart.  
  
-   Upgrade will be blocked if the Windows Installer service is not running.  
  
## Unsupported Scenarios  
  
-   Cross\-version instances of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] are not supported. Version numbers of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)], [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)], and [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] components must be the same in an instance of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
-   Cross\-platform upgrade is not supported. You cannot upgrade a 32\-bit instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to native 64\-bit using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup. However, you can back up or detach databases from a 32\-bit instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], and then restore or attach them to a new instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] \(64\-bit\) if the databases are not published in replication. You must re\-create any logins and other user objects in master, msdb, and model system databases.  
  
-   You cannot add new features during the upgrade of your existing instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. After you upgrade an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], you can add features by using the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Setup. For more information, see [Add Features to an Instance of SQL Server 2016 &#40;Setup&#41;](../Topic/Add%20Features%20to%20an%20Instance%20of%20SQL%20Server%202016%20\(Setup\).md).  
  
-   Failover Clusters are not supported in WOW mode.  
  
-   Upgrade from an Evaluation edition of a previous [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] version is not supported.  
  
## Upgrades from Earlier Versions to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]  
  
> [!NOTE]  
>  Support for [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] is described in more detail in the next section, '[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] support for [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)]'.  
  
-   [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] 32\-bit editions can be upgraded to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] on the 32\-bit subsystem \(WOW64\) of a 64\-bit server.  
  
-   [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] 64\-bit versions can be upgraded to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] 64\-bit server only.  
  
> [!NOTE]  
>  When you upgrade to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] from a prior version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Enterprise edition, choose between Enterprise Edition: Core\-based Licensing and Enterprise Edition. These Enterprise editions differ only with respect to the licensing modes and the maximum number of cores supported. For more information, see [Compute Capacity Limits by Edition of SQL Server](../../Topics\TopicNameNotContainA/Compute-Capacity-Limits-by-Edition-of-SQL-Server.md).  
  
 [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] supports upgrade from the following versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]:  
  
-   [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] SP3 or later  
  
-   [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] SP2 or later  
  
-   [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] SP1 or later  
  
-   [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] or later  
  
 The table below lists the supported upgrade scenarios from earlier versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
|Upgrade from|Supported upgrade path|  
|------------------|----------------------------|  
|[!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] SP3 Enterprise|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence|  
|[!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] SP3 Developer|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Developer|  
|[!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] SP3 Standard|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard|  
|[!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] SP3 Small Business|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard|  
|[!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] SP3 Web|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Web|  
|[!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] SP3 Workgroup|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard|  
|[!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] SP3 Express,<br /><br /> [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] SP3 Express with Tools, and<br /><br /> [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] SP3 Express with Advanced Services|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Web<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Express|  
|[!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] SP2 Datacenter|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence|  
|[!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] SP2 Enterprise|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence|  
|[!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] SP2 Developer|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Developer|  
|[!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] SP2 Small Business|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard|  
|[!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] SP2 Standard|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard|  
|[!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] SP2 Web|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Web|  
|[!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] SP2 Workgroup|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard|  
|[!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] SP2 Express,<br /><br /> [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] SP2 Express with Tools, and<br /><br /> [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] SP2 Express with Advanced Services|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Web<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Express|  
|[!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] SP1 Enterprise|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence|  
|[!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] SP1 Developer|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Developer<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Web<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence|  
|[!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] SP1 Standard|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard|  
|[!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] SP1 Web|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Web|  
|[!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] SP1 Express,<br /><br /> [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] SP1 Express with Tools, and<br /><br /> [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] SP1 Express Management Studio, and<br /><br /> [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] SP1 Express with Advanced Services|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Web<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Express<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Developer|  
|[!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] SP1 Business Intelligence|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence|  
|[!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] SP1 Evaluation|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Evaluation<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Web<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Developer|  
|[!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] Enterprise|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence|  
|[!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] Developer|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Developer<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Web<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence|  
|[!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] Standard|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard|  
|[!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] Web|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Web|  
|[!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] Express,<br /><br /> [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] Express with Tools, and<br /><br /> [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] Express Management Studio, and<br /><br /> [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] Express with Advanced Services|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Web<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Express<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Developer|  
|[!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] Business Intelligence|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence|  
|[!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] Evaluation|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Evaluation<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Web<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Developer|  
  
###  <a name="SupportFor2005"></a> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Support for [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)]  
 This section discusses [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] support for [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)]. In [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], you will be able to do the following:  
  
-   Attach a [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] database \(mdf\/ldf files\) to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] instance of database engine.  
  
-   Restore a [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] database to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] instance of database engine from a backup.  
  
-   Back up a [!INCLUDE[ssASversion2005](../../Token\Other/ssASversion2005_md.md)] cube and restoring on [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
 When a [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] database is upgraded to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], the database compatibility level will be changed from 90 to 100. \(In [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], valid values for the database compatibility level are 100, 110, 120, and 130.\) [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20Compatibility%20Level%20\(Transact-SQL\).md) discusses how the compatibility level change could affect [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] applications.  
  
 Any scenarios not specified in the list above are not supported, including but not limited to the following:  
  
-   Installing [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] and [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] on same computer \(side by side\).  
  
-   Using a [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] instance as a member of the replication topology that involves a [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] instance.  
  
-   Configuring database mirroring between [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] and [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] instances.  
  
-   Backing up the transaction log with log shipping between [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] and [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] instances.  
  
-   Configuring linked servers between [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] and [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] instances.  
  
-   Managing a [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] instance from a [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Management Studio.  
  
-   Attaching a [!INCLUDE[ssASversion2005](../../Token\Other/ssASversion2005_md.md)] cube in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Management Studio.  
  
-   Connecting to [!INCLUDE[ssISversion2005](../../Token\Other/ssISversion2005_md.md)] from [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Management Studio.  
  
-   Managing a [!INCLUDE[ssISversion2005](../../Token\Other/ssISversion2005_md.md)] service from [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Management Studio.  
  
-   Support for [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] third party custom Integration Services components, such as execute and upgrade.  
  
## [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Edition Upgrade  
 The following table lists the supported edition upgrade scenarios in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
 For step\-by\-step instructions on how to perform an edition upgrade, see [Upgrade to a Different Edition of SQL Server 2016 &#40;Setup&#41;](../Topic/Upgrade%20to%20a%20Different%20Edition%20of%20SQL%20Server%202016%20\(Setup\).md).  
  
|Upgrade From|Upgrade To|  
|------------------|----------------|  
|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise \(Server\+CAL and Core\)\*\*|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence|  
|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise \(Server\+CAL or Core License\)|  
|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Evaluation Enterprise\*\*|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise \(Server\+CAL or Core License\)<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Developer<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Web<br /><br /> Upgrading from Evaluation Enterprise \(a free edition\) to any of the paid editions is supported for stand\-alone installations, but is not supported for clustered installations.|  
|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard\*\*|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise \(Server\+CAL or Core License\)|  
|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Developer\*\*|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise \(Server\+CAL or Core License\)<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Web<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard|  
|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Web|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise \(Server\+CAL or Core License\)<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard|  
|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Express\*|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise \(Server\+CAL or Core License\)<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Developer<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard<br /><br /> [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Web|  
  
 Additionally you can also perform an edition upgrade between [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise \(Server\+CAL license\) and [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise \(Core License\):  
  
|Edition Upgrade From|Edition Upgrade To|  
|--------------------------|------------------------|  
|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise \(Server\+CAL License\)\*\*|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise \(Core License\)|  
|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise \(Core License\)|[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise \(Server\+CAL License\)|  
  
 \* Also applies to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Express with Tools and [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Express with Advanced Services.  
  
 \*\* Changing the edition of a [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] failover cluster is limited. The following scenarios are not supported for [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] failover clusters:  
  
-   [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Developer, Standard, or Enterprise Evaluation.  
  
-   [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Developer to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard or Enterprise Evaluation.  
  
-   [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise Evaluation.  
  
-   [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Enterprise Evaluation to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Standard.  
  
## See Also  
 [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md)   
 [Hardware and Software Requirements for Installing SQL Server 2016](../../Topics\TopicNameNotContainA/Hardware-and-Software-Requirements-for-Installing-SQL-Server-2016.md)   
 [Upgrade to SQL Server 2016](../../Topics\TopicNameNotContainA/Upgrade-to-SQL-Server-2016.md)  
  
  