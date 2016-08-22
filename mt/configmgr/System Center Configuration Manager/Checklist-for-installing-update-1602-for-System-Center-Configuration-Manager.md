---
title: "Checklist for installing update 1602 for System Center Configuration Manager"
ms.custom: na
ms.date: 2016-07-22
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: b63ef197-01f0-4894-b929-5ef8403c5195
caps.latest.revision: 13
---
# Checklist for installing update 1602 for System Center Configuration Manager
Before updating from [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] version 1511 to  version 1602, review the following information and checklist for actions to take before starting the update.  
  
 **About installing update 1602:**  
  
 Update 1602 can only be installed at the top-level site of your hierarchy. This means you initiate the install from your central administration site if you have one, or from your stand-alone primary site.  
  
-   Child primary sites install the update automatically after the central administration site completes installing the update. You can use maintenance windows  to control when a site installs updates. Beginning with the release of  the  1602 update, maintenance windows are renamed as service windows. For more information, see [Service Windows for site servers](../System Center Configuration Manager/Install-in-console-updates-for-System-Center-Configuration-Manager.md#bkmk_ServiceWindow).  
  
-   You must manually update secondary sites from within the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console after the primary parent site completes the update installation. Automatic update of secondary site servers is not supported.  
  
 When the site server installs the update, site system roles installed on the site server and those installed on remote computers automatically update. Therefore, before installing the update, make sure each site system server meets any new prerequisites for operation with the new update version.  
  
 The first time you use a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] consoles after the update completes, you will be prompted to update that console.  To do so you must run [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Setup on the computer that hosts the console, and select the option to update the console. We recommend that you do not delay installing the update to the console.  
  
 **Checklist:**  
  
 **Ensure all sites run a supported version of System Center Configuration Manager:**  Each site server in the hierarchy must run [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] version 1511 before you can start the installation of update 1602.  
  
 **Review installed .NET versions on site system servers:** When a site installs update 1602, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] automatically installs .NET Framework 4.5.2 on each computer that hosts one of the following site system roles when .NET Framework 4.5 or later is not already installed:  
  
-   enrollment proxy point  
  
-   enrollment point  
  
-   management point  
  
-   service connection point  
  
 This installation can put the site system server into a reboot pending state, and report errors to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] component status viewer. Additionally, .NET applications on the server might have random failures until the server is rebooted.  
  
 For more information see [Site and site system prerequisites](../System Center Configuration Manager/Site-and-site-system-prerequisites-for-System-Center-Configuration-Manager.md)  
  
 **Review the site and hierarchy status and verify that there are no unresolved issues:** Before you update a site, resolve all operational issues for the site server, the site database server, and site system roles that are installed on remote computers. A site update can fail due to existing operational problems.  
 For more information, see [Use alerts and the status system for System Center Configuration Manager](../System Center Configuration Manager/Use-alerts-and-the-status-system-for-System-Center-Configuration-Manager.md)  
  
 **Review file and data replication between sites:**  Ensure that file and database replication between sites is operational and current. Delays or backlogs in either can prevent a smooth or successful update.    
For database replication, you can use the Replication Link Analyzer to help resolve issues prior to starting the update.    
 For more information, see   
[About the Replication Link Analyzer](../System Center Configuration Manager/Monitor-hierarchy-and-replication-infrastructure-in-System-Center-Configuration-Manager.md#BKMK_RLA) in the [Monitor hierarchy and replication infrastructure in System Center Configuration Manager](../System Center Configuration Manager/Monitor-hierarchy-and-replication-infrastructure-in-System-Center-Configuration-Manager.md) topic.  
  
 **Install all applicable critical updates  for operating systems on computers that host the site, the site database server, and remote site system roles:** Before you install an update for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], install any critical updates for each applicable site system. If an update that you install requires a restart, restart the applicable computers before you start the upgrade.  
  
 **Disable database replicas for management points at primary sites:** [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] cannot successfully update a primary site that has a database replica for management points enabled. Disable database replication before you:  
  
-   Create a backup of the site database to test the database upgrade  
  
-   Install an update for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]  
  
 For more information, see   
[Database replicas for management points for System Center Configuration Manager](../System Center Configuration Manager/Database-replicas-for-management-points-for-System-Center-Configuration-Manager.md)  
  
 **Reconfigure software update points that use NLBs:** [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] cannot update a site that uses a Network Load Balancing (NLB) cluster to host software update points.  
If you use NLB clusters for software update points, use PowerShell to remove the NLB cluster.    
 For more information, see [Plan for software updates in System Center Configuration Manager](../System Center Configuration Manager/Plan-for-software-updates-in-System-Center-Configuration-Manager.md)  
  
 **Disable all site maintenance tasks at each site for the duration of the update installation on that site:** Before you install update, disable any site maintenance task that might run during the time the update process is active. This includes but is not limited to the following:  
  
-   Backup Site Server  
  
-   Delete Aged Client Operations  
  
-   Delete Aged Discovery Data  
  
 When a site database maintenance task runs during the update installation, the update installation can fail. Before you disable a task, record the schedule of the task so you can restore its configuration after the update has installed.  
 For more information, see [Maintenance tasks for System Center Configuration Manager](../System Center Configuration Manager/Maintenance-tasks-for-System-Center-Configuration-Manager.md) and [Reference for maintenance tasks for System Center Configuration Manager](../System Center Configuration Manager/Reference-for-maintenance-tasks-for-System-Center-Configuration-Manager.md)  
  
 **Create a backup of the site database at the central administration site and primary sites:** Before you update a site, back up the site database to ensure that you have a successful backup to use for disaster recovery.   
For more information, see [Backup and recovery for System Center Configuration Manager](../System Center Configuration Manager/Backup-and-recovery-for-System-Center-Configuration-Manager.md)  
  
 **Backup a customized Configuration.mof file:** If you use a customized Configuration.mof file to define data classes you use with hardware inventory, create a backup of this file before updating the site. Then after the update, restore this file to your version 1602 site. When updating a site, the current file is overwritten with the original (default) version of the file. For more information  about using this file see [How to extend hardware inventory in System Center Configuration Manager](../System Center Configuration Manager/How-to-extend-hardware-inventory-in-System-Center-Configuration-Manager.md)  
  
 **Test the database upgrade on a copy of the most recent site database backup:** Before you update a [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] central administration site or primary site, test the site database upgrade process on a copy of the site database.  
  
-   You should test the site database upgrade process because when you upgrade a site, the site database might be modified  
  
-   Although a test database upgrade is not required, it can identify problems for the upgrade before your production database is affected  
  
-   A failed site database upgrade can render your site database inoperable and might require a site recovery to restore functionality  
  
-   Although the site database is shared between sites in a hierarchy, plan to test the database at each applicable site before you upgrade that site  
  
-   If you use database replicas for management points at a primary site, disable replication before you create the backup of the site database  
  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not support the backup of secondary sites nor the test upgrade of a secondary site database.   
It is not supported to run a test database upgrade on the production site database. Doing so updates the site database and could render your site inoperable. For more information, see the [Test the site database upgrade](../System Center Configuration Manager/Upgrade-to-System-Center-Configuration-Manager.md#bkmk_test) section in [Upgrade to System Center Configuration Manager](../System Center Configuration Manager/Upgrade-to-System-Center-Configuration-Manager.md).  
  
 **Plan for client piloting:** When you install an update that updates the client, you can test that new client update in pre-production before it deploys and upgrades all your active client.   
 To take advantage of this option, before beginning installation of the update you must configure your site to support automatic upgrades for preproduction. For more information, see [Upgrade clients in System Center Configuration Manager](../System Center Configuration Manager/Upgrade-clients-in-System-Center-Configuration-Manager.md) and   
[How to test client upgrades in a preproduction collection in System Center Configuration Manager](../System Center Configuration Manager/How-to-test-client-upgrades-in-a-preproduction-collection-in-System-Center-Configuration-Manager.md)  
  
 **Plan to use Maintenance windows**  
 **to control when site servers install updates:** You can use the Maintenance windows to define a period of time that applies to a primary site server during which updates to that site can be installed.   
This can help you control when sites in your hierarchy install the update.   
Beginning with the release of  the  1602 update, maintenance windows are renamed as service windows. For more information, see [Service Windows for site servers](../System Center Configuration Manager/Install-in-console-updates-for-System-Center-Configuration-Manager.md#bkmk_ServiceWindow).  
  
 **Run Setup Prerequisite Checker:**  Before you install update 1602, you can run the Prerequisite Checker independently from the update installation. When you install the update on the site, Prerequisite Checker runs again.  
For more information, see **Step 3: Run the prerequisite checker before installing an update** in the [Updates for System Center Configuration Manager](../System Center Configuration Manager/Updates-for-System-Center-Configuration-Manager.md) topic.  
  
> [!IMPORTANT]  
>  When the prerequisite checker runs as part of an update install or independently, the process updates some product source files that are used for site maintenance tasks. Therefore, after running the prerequisite checker but before installing the 1602 update, if you must perform a site maintenance task, run **Setupwfe.exe** ([!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Setup) from the CD.Latest folder on the site server.  
  
 **Update sites:** You are now ready to start the update installation for your hierarchy.  
  We recommend you plan to install the update outside of normal business hours for each site when the process of installing the update and its actions to reinstall site components and site system roles will have the least effect on your business operations. For more information, see [Updates for System Center Configuration Manager](../System Center Configuration Manager/Updates-for-System-Center-Configuration-Manager.md).  
  
## See Also  
 [Updates for System Center Configuration Manager](../System Center Configuration Manager/Updates-for-System-Center-Configuration-Manager.md)