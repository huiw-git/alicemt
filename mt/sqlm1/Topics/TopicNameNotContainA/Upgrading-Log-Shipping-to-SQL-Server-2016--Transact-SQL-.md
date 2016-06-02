---
title: Upgrading Log Shipping to SQL Server 2016 (Transact-SQL)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b1289cc3-f5be-40bb-8801-0e3eed40336e
---
# Upgrading Log Shipping to SQL Server 2016 (Transact-SQL)
  When upgrading from a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] log shipping configuration to a new [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] version, a new [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]service pack, or a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]cumulative update, upgrading your log shipping servers in the appropriate order will preserve your log shipping disaster recovery solution.  
  
> [!NOTE]  
>  [Backup compression](../Topic/Backup%20Compression%20\(SQL%20Server\).md) was introduced in [!INCLUDE[ssEnterpriseEd10](../../Token\Other/ssEnterpriseEd10_md.md)]. An upgraded log shipping configuration uses the **backup compression default** server\-level configuration option to control whether backup compression is used for the transaction log backup files. The backup compression behavior of log backups can be specified for each log shipping configuration. For more information, see [Configure Log Shipping &#40;SQL Server&#41;](../Topic/Configure%20Log%20Shipping%20\(SQL%20Server\).md).  
  
 **In This Topic:**  
  
-   [Prerequisites](#Prerequisites)  
  
-   [Protect Your Data Before the Upgrade](#ProtectData)  
  
-   [Upgrading the Monitor Server Instance](#UpgradeMonitor)  
  
-   [Upgrading the Secondary Server Instances](#UpgradeSecondaries)  
  
-   [Upgrading the Primary Instance](#UpgradePrimary)  
  
##  <a name="Prerequisites"></a> Prerequisites  
 Before you begin, review the following important information:  
  
-   [Supported Version and Edition Upgrades](../../Topics\TopicNameNotContainA/Supported-Version-and-Edition-Upgrades.md): Verify that you can upgrade to SQL Server 2016 from your version of the Windows operating system and version of SQL Server. For example, you cannot upgrade directly from a SQL Server 2005 instance to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
-   [Choose a Database Engine Upgrade Method](../../Topics\TopicNameContainA/Choose-a-Database-Engine-Upgrade-Method.md): Select the appropriate upgrade method and steps based on your review of supported version and edition upgrades and also based on other components installed in your environment to upgrade components in the correct order.  
  
-   [Plan and Test the Database Engine Upgrade Plan](../../Topics\TopicNameNotContainA/Plan-and-Test-the-Database-Engine-Upgrade-Plan.md): Review the release notes and known upgrade issues, the pre\-upgrade checklist, and develop and test the upgrade plan.  
  
-   [Hardware and Software Requirements for Installing SQL Server 2016](../../Topics\TopicNameNotContainA/Hardware-and-Software-Requirements-for-Installing-SQL-Server-2016.md):  Review the software requirements for installing [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. If additional software is required, install it on each node before you begin the upgrade process to minimize any downtime.  
  
##  <a name="ProtectData"></a> Protect Your Data Before the Upgrade  
 As a best practice, we recommend that you protect your data before a log shipping upgrade.  
  
 **To protect your data**  
  
1.  Perform a full database backup on every primary database.  
  
     For more information, see [Create a Full Database Backup &#40;SQL Server&#41;](../Topic/Create%20a%20Full%20Database%20Backup%20\(SQL%20Server\).md).  
  
2.  Run the [DBCC CHECKDB](../Topic/DBCC%20CHECKDB%20\(Transact-SQL\).md) command on every primary database.  
  
> [!IMPORTANT]  
>  Ensure that you have sufficient space on your primary server to hold the log backup copies for as long as the upgrade of the secondaries is expected to take.  If you are failing over to a secondary, this same concern applies to the secondary \(the new primary\).  
  
##  <a name="UpgradeMonitor"></a> Upgrading the \(Optional\) Monitor Server Instance  
 The monitor server instance, if any, can be upgraded at any time. However, you do not need to upgrade the optional monitor server when you upgrade the primary and secondary servers.  
  
 While the monitor server is being upgraded, the log shipping configuration continues to work, but its status is not recorded in the tables on the monitor. Any alerts that have been configured will not be triggered while the monitor server is being upgraded. After the upgrade, you can update the information in the monitor tables by executing the [sp\_refresh\_log\_shipping\_monitor](../Topic/sp_refresh_log_shipping_monitor%20\(Transact-SQL\).md) system stored procedure.   For more information about a monitor server, see [About Log Shipping &#40;SQL Server&#41;](../Topic/About%20Log%20Shipping%20\(SQL%20Server\).md).  
  
##  <a name="UpgradeSecondaries"></a> Upgrading the Secondary Server Instances  
 The upgrade process involves upgrading the secondary server instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] before upgrading the primary server instance. Always upgrade the secondary [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instances first. Log shipping continues throughout the upgrade process because the upgraded secondary server instances continue to restore the log backups from [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] primary server instance. If the primary server instance is upgraded before the secondary server instance, log shipping will fail because a backup created on a newer version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] cannot be restored on an older version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. You can upgrade the secondary instances simultanously or serially, but all secondary instance must be upgraded before the primary instance is upgraded to avoid a log shipping failure.  
  
 While a secondary server instance is being upgraded, the log shipping copy and restore jobs do not run. This means that unrestored transaction log backups will accumulate on the primary and you need to have sufficient space to hold these unrestored backups. The amount of accumulation depends on the frequency of scheduled backup on the primary server instance and the sequence in which you upgrade the secondary instances. Also, if a separate monitor server has been configured, alerts might be raised indicating restores have not been performed for longer than the configured interval.  
  
 Once the secondary server instances have been upgraded, the log shipping agents jobs resume and continue to copy and restore log backups from the primary server instance to the secondary server instances. The amount of time required for the secondary server instances to bring the secondary database up to date varies, depending on the time taken to upgrade the secondary server instance and the frequency of the backups on the primary server.  
  
> [!NOTE]  
>  During the server upgrade, the secondary database itself is not upgraded to a [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] database. It will get upgraded only if it is brought online by initiating a failover of the log shipped database. In theory, this condition could persist indefinitely. The amount of time to upgrade the database metadata when a failover is initiated is small.  
  
> [!IMPORTANT]  
>  The RESTORE WITH STANDBY option is not supported for a database that requires upgrading. If an upgraded secondary database has been configured by using RESTORE WITH STANDBY, transaction logs can no longer be restored after upgrade. To resume log shipping on that secondary database, you will need to set up log shipping again on that standby server. For more information about the STANDBY option, see [Restore a Transaction Log Backup &#40;SQL Server&#41;](../Topic/Restore%20a%20Transaction%20Log%20Backup%20\(SQL%20Server\).md).  
  
##  <a name="UpgradePrimary"></a> Upgrading the Primary Server Instance  
 Since log shipping is primarily a disaster recovery solution, the simplest and most common scenario is to upgrade the primary instance in\-place and the database is simply unavailable during this upgrade. Once the server is upgraded, the database is automatically brought back online, which causes it to be upgraded. After the database is upgraded, the log shipping jobs resume.  
  
> [!NOTE]  
>  Log shipping also supports the option to [Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;](../Topic/Fail%20Over%20to%20a%20Log%20Shipping%20Secondary%20\(SQL%20Server\).md), and optionally [Change Roles Between Primary and Secondary Log Shipping Servers &#40;SQL Server&#41;](../Topic/Change%20Roles%20Between%20Primary%20and%20Secondary%20Log%20Shipping%20Servers%20\(SQL%20Server\).md). However, since log shipping is rarely configured as a high availability solution anymore \(newer options are much more robust\), failing over generally will not minimize downtime because system database objects will not be synchronized and enabling clients to easily locate and connect to a promoted secondary can be an ordeal.  
  
## See Also  
 [Upgrade to SQL Server 2016 Using the Installation Wizard &#40;Setup&#41;](../Topic/Upgrade%20to%20SQL%20Server%202016%20Using%20the%20Installation%20Wizard%20\(Setup\).md)   
 [Install SQL Server 2016 from the Command Prompt](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016-from-the-Command-Prompt.md)   
 [Configure Log Shipping &#40;SQL Server&#41;](../Topic/Configure%20Log%20Shipping%20\(SQL%20Server\).md)   
 [Monitor Log Shipping &#40;Transact-SQL&#41;](../Topic/Monitor%20Log%20Shipping%20\(Transact-SQL\).md)   
 [Log Shipping Tables and Stored Procedures](../../Topics\TopicNameNotContainA/Log-Shipping-Tables-and-Stored-Procedures.md)  
  
  