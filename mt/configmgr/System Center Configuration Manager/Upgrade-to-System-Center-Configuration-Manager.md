---
title: "Upgrade to System Center Configuration Manager"
ms.custom: na
ms.date: 2016-07-22
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: c64e7483-b4bb-4738-95f4-ecdaeb6a2ba6
caps.latest.revision: 21
---
# Upgrade to System Center Configuration Manager
You can run an in-place upgrade to upgrade to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] from a site and hierarchy that runs [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)].  
  
 Before upgrading from [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)], you must prepare sites which requires you to remove specific configurations that can prevent a successful upgrade, and then follow the upgrade sequence when more than a single site is involved.  
  
-   [In-place upgrade paths](#bkmk_path)  
  
-   [Upgrade checklists](#bkmk_checklist)  
  
-   [Considerations for upgrading](#bkmk_considerations)  
  
-   [Test the site database upgrade](#bkmk_test)  
  
-   [Upgrade sites](#bkmk_upgrade)  
  
-   [Perform post-upgrade tasks](#BKMK_PostUpgrade)  
  
##  <a name="bkmk_path"></a> In-place upgrade paths  
 **You can upgrade the following to a fully licensed  version of [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]:**  
  
-   An evaluation install of [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]  
  
-   A release candidate install of [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]  
  
-   [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] with Service Pack 1  
  
-   [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] with Service Pack 2  
  
-   [!INCLUDE[sccm2012r2_1](../System Center Configuration Manager/itokens/sccm2012r2_1_md.md)]  
  
-   [!INCLUDE[sccm2012r2_1](../System Center Configuration Manager/itokens/sccm2012r2_1_md.md)] with Service Pack 1  
  
> [!TIP]  
>  When you upgrade from a [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] version might be able to streamline your upgrade process. For more information, see the following:  
>   
>  -   The [Baseline and update versions](../System Center Configuration Manager/Updates-for-System-Center-Configuration-Manager.md#bkmk_Baselines) section in [Updates for System Center Configuration Manager](../System Center Configuration Manager/Updates-for-System-Center-Configuration-Manager.md)  
> -   [The CD.Latest folder for System Center Configuration Manager](../System Center Configuration Manager/The-CD.Latest-folder-for-System-Center-Configuration-Manager.md)  
  
 **The following is not supported:**  
  
-   It is not supported to upgrade a Technical Preview for [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] to a fully licensed installation.  A Technical Preview version can  only upgrade to a later version of the Technical Preview.  
  
-   Migration from a Technical Preview to a fully licensed  version is not supported  
  
##  <a name="bkmk_checklist"></a> Upgrade checklists  
 The following check lists can help you plan a successful upgrade to  [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)].  
  
### Before you upgrade  
 **Ensure that your computing environment meets the supported configurations** that are required for upgrading to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]:  
  
 Review the server operating systems in use to host site system roles:  
  
-   Some older operating systems supported by [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] are not supported by [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], and site system roles on those operating systems must be relocated or removed before the upgrade  
  
-   Prerequisite Checker for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not verify the prerequisites for site system roles on the site server or on remote computers  
  
 Review required prerequisites for each computer that hosts a site system role:  
  
-   For example, to deploy an operating system, [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] uses the Windows 10 Assessment and Deployment Kit (Windows ADK). Before you run Setup, you must download and install Windows 10 ADK on the site server and on each computer that runs an instance of the SMS Provider.  
  
 For general information about supported platforms and prerequisite configurations, see [Supported configurations for System Center Configuration Manager](../System Center Configuration Manager/Supported-configurations-for-System-Center-Configuration-Manager.md).  
  
 For information about using the Windows ADK with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], see [Infrastructure requirements for operating system deployment in System Center Configuration Manager](../System Center Configuration Manager/Infrastructure-requirements-for-operating-system-deployment-in-System-Center-Configuration-Manager.md).  
  
 **Review the site and hierarchy status** and verify that there are no unresolved issues:  
  
 Before you upgrade a site, resolve all operational issues for the site server, the site database server, and site system roles that are installed on remote computers. A site upgrade can fail due to existing operational problems.  
  
 **Install all applicable critical updates** for operating systems on computers that host the site, the site database server, and remote site system roles:  
  
 Before you upgrade a site, install any critical updates for each applicable site system. If an update that you install requires a restart, restart the applicable computers before you start the service pack update.  
  
 For more information, see [Windows Update](http://go.microsoft.com/fwlink/p/?LinkId=105851)  
  
 **Uninstall the site system roles** not supported by [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]:  
  
 The following site system roles are no longer used in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] and must be uninstalled before you upgrade from [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)]:  
  
-   Out of Band Management point  
  
-   Service Health Validator point  
  
 **Disable database replicas** for management points at primary sites:  
  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] cannot successfully upgrade a primary site that has a database replica for management points enabled. Disable database replication before you:  
  
-   Create a backup of the site database to test the database upgrade  
  
-   Upgrade the production site to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]  
  
 For more information, see the following:  
  
-   [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)]:  [Configure Database Replicas for Management Points](https://technet.microsoft.com/library/hh846234.aspx)  
  
-   [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]: [Database replicas for management points for System Center Configuration Manager](../System Center Configuration Manager/Database-replicas-for-management-points-for-System-Center-Configuration-Manager.md)  
  
 **Reconfigure software update points that use NLBs**:  
  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] cannot upgrade a site that uses a Network Load Balancing (NLB) cluster to host software update points.  
  
 If you use NLB clusters for software update points, use PowerShell to remove the NLB cluster. (Beginning with [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] SP1, there was no option in the [!INCLUDE[cmconsole](../System Center Configuration Manager/itokens/cmconsole_md.md)] to configure an NLB cluster)  
  
 **Disable all site maintenance tasks** at each site for the duration of that site’s upgrade:  
  
 Before you upgrade to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], disable any site maintenance task that might run during the time the upgrade process is active. This includes but is not limited to the following:  
  
-   Backup Site Server  
  
-   Delete Aged Client Operations  
  
-   Delete Aged Discovery Data  
  
 When a site database maintenance task runs during the upgrade process, the site upgrade can fail.  
  
 Before you disable a task, record the schedule of the task so you can restore its configuration after the site upgrade completes.  
  
 For more information about site maintenance tasks, see:  
  
-   [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)]:  [Planning for Maintenance Tasks for Configuration Manager](https://technet.microsoft.com/library/gg712686.aspx)  
  
-   [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]:  [Reference for maintenance tasks for System Center Configuration Manager](../System Center Configuration Manager/Reference-for-maintenance-tasks-for-System-Center-Configuration-Manager.md)  
  
 **Run Setup Prerequisite Checker**:  
  
 Before you upgrade a site, you can run the **Prerequisite Checker** independently from Setup to validate that your site meets the prerequisites. When you upgrade the site, Prerequisite Checker runs again.  
  
 For more information, see the [Prerequisite Checker](../System Center Configuration Manager/Site-installation-technical-reference-for-System-Center-Configuration-Manager.md#bkmk_PreqChk) and [List of Prerequisite Checks for System Center Configuration Manager](../System Center Configuration Manager/List-of-Prerequisite-Checks-for-System-Center-Configuration-Manager.md)  
  
 **Download prerequisite files and redistributable files** for [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]:  
  
 Use **Setup Downloader** to download prerequisite redistributable files, language packs, and the latest product updates for [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)].  
  
 For information, see [Setup Downloader](../System Center Configuration Manager/Site-installation-technical-reference-for-System-Center-Configuration-Manager.md#bkmk_SetupDownloader)  
  
 **Plan to manage server and client languages**:  
  
 When you upgrade a site, the site upgrade installs only the language pack versions you select during the upgrade.  
  
-   Setup reviews the current language configuration of your site, and then identifies the language packs that are available in the folder where you store previously downloaded prerequisite files.  
  
-   You can then affirm the selection of the current server and client language packs, or change the selections to add or remove support for languages.  
  
-   Only language packs that are available when you run Setup (which you get with the prerequisite files that you download) can be selected.  
  
> [!NOTE]  
>  You cannot use the language packs from [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] to enable languages for a [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] site.  
  
 For more information about language packs, see  [Language Packs in System Center Configuration Manager](../System Center Configuration Manager/Language-Packs-in-System-Center-Configuration-Manager.md)  
  
 **Review considerations for site upgrades**:  
  
 When you upgrade a site, some features and configurations reset to a default configuration. To help you prepare for these and related changes, review the information in  [Considerations for upgrading](#bkmk_considerations).  
  
 **Create a backup** of the site database at the central administration site and primary sites:  
  
 Before you upgrade a site, back up the site database to ensure that you have a successful backup to use for disaster recovery.  
  
 See [Backup and recovery for System Center Configuration Manager](../System Center Configuration Manager/Backup-and-recovery-for-System-Center-Configuration-Manager.md)  
  
 **Backup a customized Configuration.mof file**:  
  
 If you use a customized Configuration.mof file to define data classes you use with hardware inventory, create a backup of this file before upgrading the site. Then after the upgrade, restore this file to your  site. For more information  about using this file see [How to extend hardware inventory in System Center Configuration Manager](../System Center Configuration Manager/How-to-extend-hardware-inventory-in-System-Center-Configuration-Manager.md)  
  
 **Test the database upgrade** process on a copy of the most recent site database backup:  
  
 Before you upgrade a Configuration Manager central administration site or primary site, test the site database upgrade process on a copy of the site database.  
  
-   You should test the site database upgrade process because when you upgrade a site, the site database might be modified  
  
-   Although a test database upgrade is not required, it can identify problems for the upgrade before your production database is affected  
  
-   A failed site database upgrade can render your site database inoperable and might require a site recovery to restore functionality  
  
-   Although the site database is shared between sites in a hierarchy, plan to test the database at each applicable site before you upgrade that site  
  
-   If you use database replicas for management points at a primary site, disable replication before you create the backup of the site database  
  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not support  the backup of secondary sites nor the test upgrade of a secondary site database.  
  
 It is not supported to run a test database upgrade on the production site database. Doing so upgrades the site database and could render your site inoperable.  
  
 For more information, see [Test the site database upgrade](#bkmk_test).  
  
 **Restart the site server and each computer that hosts a site system role** to ensure that there are no pending actions from a recent installation of updates or from prerequisites:  
  
 Internal process that is company-specific.  
  
 **Upgrade sites**:  
  
 **Starting at the top-level site in the hierarchy**, run Setup.exe from the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] source media.  
  
 After the top-level site upgrades,    you can begin the upgrade of each child site. Complete the upgrade of each site before you begin to upgrade the next site  
  
 Until all sites in your hierarchy upgrade to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], your hierarchy operates in a mixed version mode.  
  
 For information about how to run upgrade, see [Upgrade sites](#bkmk_upgrade)  
  
### After you upgrade  
 **Upgrade stand-alone [!INCLUDE[cmconsole](../System Center Configuration Manager/itokens/cmconsole_md.md)]s**:  
  
 By default, when you upgrade a central administration site or primary site, the installation also upgrades the [!INCLUDE[cmconsole](../System Center Configuration Manager/itokens/cmconsole_md.md)] that is installed on the site server. However, you must manually upgrade each console that is installed on a computer other than the site server.  
  
> [!TIP]  
>  Close each open console before you start the upgrade.  
  
 For more information, see [Install System Center Configuration Manager consoles](../System Center Configuration Manager/Install-System-Center-Configuration-Manager-consoles.md).  
  
 **Reconfigure database replicas** for management points at primary sites:  
  
 If you use database replicas for management points at primary sites, you must uninstall the database replicas before you upgrade the site. After you upgrade a primary site, reconfigure the database replica for management points.   
For more information, see  [Database replicas for management points for System Center Configuration Manager](../System Center Configuration Manager/Database-replicas-for-management-points-for-System-Center-Configuration-Manager.md).  
  
 **Reconfigure any database maintenance tasks** you disabled prior to the upgrade:  
  
 If you disabled database [Reference for maintenance tasks for System Center Configuration Manager](../System Center Configuration Manager/Reference-for-maintenance-tasks-for-System-Center-Configuration-Manager.md) at a site prior to the upgrade, reconfigure those tasks at the site using the same settings that were in place prior to the upgrade.  
  
 **Upgrade clients**:  
  
 After all your sites upgrade to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], plan to upgrade clients.  
  
 When you upgrade a client, the current client software is uninstalled and the new client software version is installed. To upgrade clients, you can use any method that Configuration Manager supports.  
  
> [!TIP]  
>  When you upgrade the top-level site of a hierarchy, the client installation package on each distribution point in the hierarchy is also updated. When you upgrade a primary site, the client upgrade package that is available from that primary site is updated.  
  
 For information about how to upgrade existing clients and how to install new clients, see [How to upgrade clients for Windows computers in System Center Configuration Manager](../System Center Configuration Manager/How-to-upgrade-clients-for-Windows-computers-in-System-Center-Configuration-Manager.md).  
  
##  <a name="bkmk_considerations"></a> Considerations for upgrading  
 **Automatic actions** - When you upgrade to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], the following actions occur automatically:  
  
-   The site performs a site reset, which includes a reinstallation of all site system roles.  
  
-   If the site is the top-level site of a hierarchy, it updates the client installation package on each distribution point in the hierarchy. The site also updates the default boot images to use the new Windows PE version that is included with the Windows Assessment and Deployment Kit 10. However, the upgrade does not upgrade existing media for use with image deployment.  
  
-   If the site is a primary site, it updates the client upgrade package for that site.  
  
 **Manual actions for the administrative user after an upgrade** - After you upgrade a site, ensure that the following actions are performed:  
  
-   Ensure that clients that are assigned to each primary site upgrade and install the client software for the new version  
  
-   Upgrade each [!INCLUDE[cmconsole](../System Center Configuration Manager/itokens/cmconsole_md.md)] that connects to the site and that runs on a computer that is remote from the site server  
  
-   At primary sites where you use database replicas for management points, reconfigure the database replicas  
  
-   After the site upgrades, you must manually upgrade physical media like ISO files for CDs and DVDs or USB flash drives, or prestaged media used for Windows To Go deployments or provided to hardware vendors. Although the site upgrade updates the default boot images it cannot upgrade these media files or devices used external to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]  
  
-   Plan to update non-default boot images when you do not require the original (older) version of Windows PE.  
  
 **Actions that affect configurations and settings** - When a site upgrades to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], some configurations and settings do not persist after the upgrade or are set to a new default configuration. The following table are settings that do not persist or that change, and provides details to help you plan for them during a site upgrade:  
  
-   **Software Center:**  
  
     The following Software Center items are reset to their default values:  
  
    -   **Work information** is reset to business hours from **5.00am** to **10.00pm** Monday to Friday.  
  
    -   The value for **Computer maintenance** is set to **Suspend Software Center activities when my computer is in presentation mode**.  
  
    -   The value for **Remote control** is set to the value in the client settings that are assigned to the computer.  
  
-   **Software update summarization schedules:**  
  
     Custom summarization schedules for software updates or software update groups are reset to the default value of 1 hour. After the upgrade finishes, reset custom summarization values to the required frequency.  
  
##  <a name="bkmk_test"></a> Test the site database upgrade  
 Before you upgrade a site, test a copy of that site’s database for the upgrade.  
  
 To test the database for an upgrade, you first restore a copy of the site database to an instance of SQL Server that does not host a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site. The version of SQL Server that you use to host the database copy must be a version of SQL Server that the version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports that is the source of the database copy.  
  
 Next, after you restore the site database, on the SQL Server computer, run [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Setup from the source media folder for [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] with the **/TESTDBUPGRADE** command-line option.  
  
-   For information about how to create and restore a backup of a site database, see [Command-line options for Setup](../System Center Configuration Manager/Command-line-options-for-Setup-for-System-Center-Configuration-Manager.md).  
  
-   For information about the **/TESTDBUPGRADE** command-line option, see the table in [Command-line options for Setup](../System Center Configuration Manager/Command-line-options-for-Setup-for-System-Center-Configuration-Manager.md).  
  
-   For information about the supported versions of SQL Server, see the [Support for SQL Server versions for System Center Configuration Manager](../System Center Configuration Manager/Support-for-SQL-Server-versions-for-System-Center-Configuration-Manager.md) topic.  
  
> [!TIP]  
>  If you integrate [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]:  
>   
>  When you run a test database upgrade on copy of the site database that is 5 or more days old, you might receive one of the following messages:  
>   
>  -   WARN: Upgrade will force full sync to cloud.  
> -   ERROR: Database upgrade will force full sync to cloud.  
>   
>  Both of these can be safely ignored during the testing of a database upgrade as they do not indicate a failure or problem with the test upgrade. Instead, they indicate that during the actual upgrade, data from the **Cloud** database replication group might synchronize with [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)].  
  
 Use the following procedure on each central administration site and primary site that you plan to upgrade.  
  
#### To test a site database for upgrade  
  
1.  Make a copy of the site database, and then restore that copy to an instance of SQL Server that uses the same edition as your site database and that does not host a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site. For example, if the site database runs on an instance of the Enterprise edition of SQL Server, make sure you restore the database to an instance of SQL Server that also runs the Enterprise edition of SQL Server.  
  
2.  After you restore the database copy, run Setup from the source media for [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]. When you run Setup, use the **/TESTDBUPGRADE** command-line option. If the SQL Server instance that hosts the database copy is not the default instance, you must also provide the command-line arguments to identify the instance that hosts the site database copy.  
  
     For example, you plan to upgrade a site database with the database name SMS_ABC. You restore a copy of this site database to a supported instance of SQL Server with the instance name DBTest. To test an upgrade of this copy of the site database, use the following command line: **Setup.exe /TESTDBUPGRADE DBtest\CM_ABC**  
  
     You can find Setup.exe in the following location on the source media for [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]: **SMSSETUP\BIN\X64**.  
  
3.  On the instance of SQL Server where you run the database upgrade test, monitor the ConfigMgrSetup.log in the root of the system drive for progress and success:  
  
    -   If the test upgrade fails, resolve any issues related to the site database upgrade failure, create a new backup of the site database, and then test the upgrade of the new copy of the site database.  
  
    -   After the process is successful, you can delete the database copy.  
  
        > [!NOTE]  
        >  It is not supported to restore the copy of the site database that you use for the test upgrade for use as a site database at any site.  
  
 After you successfully upgrade a copy of the site database, proceed with the upgrade of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site and its site database.  
  
##  <a name="bkmk_upgrade"></a> Upgrade sites  
 After you complete pre-upgrade configurations for your site, test the upgrade of the site database on a database copy, and download prerequisite files and language packs for the service pack version that you plan to install, you are ready to upgrade your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site.  
  
 When you upgrade a site in a hierarchy, you upgrade the top-level site of the hierarchy first. This top-level site is either a central administration site or a stand-alone primary site. After the upgrade of a central administration site is completed, you can upgrade child primary sites in any order that you want. After you upgrade a primary site, you can upgrade that site’s child secondary sites, or upgrade additional primary sites before you upgrade any secondary sites.  
  
 To upgrade a central administration site or primary site, you run Setup from the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] source media. However, you do not run Setup to upgrade secondary sites. Instead, you use the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console to upgrade a secondary site after you complete the upgrade of its primary parent site.  
  
 Before you upgrade a site, close the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console that is installed on the site server until after the site upgrade is completed. Also close each [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console that runs on computers other than the site server. You can reconnect the console after the site upgrade is completed. However, until you upgrade a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console to the new version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], that console cannot display some objects and information that are available in new version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
 Use the following procedures to upgrade [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] sites:  
  
#### To upgrade a central administration site or primary site  
  
1.  Verify that the user who runs Setup has the following security rights:  
  
    -   Local Administrator rights on the site server computer.  
  
    -   Local Administrator rights on the remote site database server for the site, if it is remote.  
  
2.  On the site server computer, open Windows Explorer and browse to **<ConfigMgSourceMedia\>\SMSSETUP\BIN\X64**.  
  
3.  Double-click **Setup.exe**. The [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Setup wizard opens.  
  
4.  On the **Before You Begin** page, click **Next**.  
  
5.  On the **Getting Started** page, select **Upgrade this Configuration Manager site**, and then click **Next**.  
  
6.  On the **Product Key** page, click **Next**.  
  
     If you previously installed [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Evaluation, you can select **Install the licensed edition of this product**, and then enter your product key for the full installation of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to convert the site to the full version.  
  
7.  On the **Microsoft Software License Terms** page, read and accept the license terms, and then click **Next**.  
  
8.  On the **Prerequisite Licenses** page, read and accept the license terms for the prerequisite software, and then click **Next**. Setup downloads and automatically installs the software on site systems or clients when it is required. You must select all check boxes before you can continue to the next page.  
  
9. On the **Prerequisite Downloads** page, specify whether Setup downloads the latest prerequisite redistributable files, language packs, and the latest product updates from the Internet or use previously downloaded files, and then click **Next**. If you previously downloaded the files by using Setup Downloader, select **Use previously downloaded files** and specify the download folder. For information about Setup Downloader, see the [Setup Downloader](../System Center Configuration Manager/Site-installation-technical-reference-for-System-Center-Configuration-Manager.md#bkmk_SetupDownloader) section in the [Site installation technical reference for System Center Configuration Manager](../System Center Configuration Manager/Site-installation-technical-reference-for-System-Center-Configuration-Manager.md) topic.  
  
    > [!NOTE]  
    >  When you use previously downloaded files, verify that the path to the download folder contains the most recent version of the files.  
  
10. On the **Server Language Selection** page, view the list of languages that are currently installed for the site. Select additional languages that are available at this site for the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console and for reports, or clear languages that you no longer want to support at this site, and then click **Next**. By default, English is selected and cannot be removed.  
  
    > [!IMPORTANT]  
    >  Each version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] cannot use language packs from a prior version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. To enable support for a language at a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site that you upgrade, you must use the version of the language pack for that new version. For example, during upgrade from [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], if the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] version of a language pack is not available with the prerequisite files you download, support for that language cannot be installed.  
  
11. On the **Client Language Selection** page, view the list of languages that are currently installed for the site. Select additional languages that are available at this site for client computers, or clear languages that you no longer want to support at this site. Specify whether to enable all client languages for mobile device clients, and then click **Next**. By default, English is selected and cannot be removed.  
  
    > [!IMPORTANT]  
    >  Each version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] cannot use language packs from a prior version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. To enable support for a language at a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site that you upgrade, you must use the version of the language pack for that new version. For example, during upgrade from [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], if the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] version of a language pack is not available with the prerequisite files you download, support for that language cannot be installed.  
  
12. On the **Settings Summary** page, click **Next** to start Prerequisite Checker to verify server readiness for the upgrade of the site.  
  
13. On the **Prerequisite Installation Check** page, if there are no problems listed, click **Next** to upgrade the site and site system roles. When Prerequisite Checker finds a problem, click an item on the list for details about how to resolve the problem. Resolve all items in the list that have an **Error** status before you continue Setup. After you resolve the issue, click **Run Check** to restart prerequisite checking. You can also open the ConfigMgrPrereq.log file in the root of the system drive to review the Prerequisite Checker results. The log file can contain additional information that is not displayed in the user interface. For a complete list of installation prerequisite rules and descriptions, see  [Prerequisite Checker](../System Center Configuration Manager/Site-installation-technical-reference-for-System-Center-Configuration-Manager.md#bkmk_PreqChk) in [Site installation technical reference for System Center Configuration Manager](../System Center Configuration Manager/Site-installation-technical-reference-for-System-Center-Configuration-Manager.md).  
  
 On the **Upgrade** page, Setup displays the overall progress status. When Setup completes the core site server and site system installation, you can close the wizard. Site configuration continues in the background.  
  
#### To upgrade a secondary site  
  
1.  Verify that the administrative user that runs Setup has the following security rights:  
  
    -   Local Administrator rights on the secondary site computer  
  
    -   Infrastructure Administrator or a Full Administrator security role on the parent primary site  
  
    -   System administrator (SA) rights on the site database of the secondary site  
  
2.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
3.  In the **Administration** workspace, expand **Site Configuration**, and then click **Sites**.  
  
4.  Select the secondary site that you want to upgrade, and then, on the **Home** tab, in the **Site** group, click **Upgrade**.  
  
5.  Click **Yes** to confirm the decision, and to start the upgrade of the secondary site.  
  
 The secondary site upgrade progresses in the background. After the upgrade is completed, you can confirm the status in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. To confirm the status, select the secondary site server, and then on the **Home** tab, in the **Site** group, click **Show Install Status**.  
  
##  <a name="BKMK_PostUpgrade"></a> Perform post-upgrade tasks  
 After you upgrade a site to a new service pack, you might have to complete additional tasks to finish the upgrade or reconfigure the site. These tasks can include the upgrade of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients or [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] consoles, re-enabling database replicas for management points, or restoring settings for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] functionality that you use and that does not persist after the service pack upgrade.  
  
## See Also  
 [Start using System Center Configuration Manager](../System Center Configuration Manager/Start-using-System-Center-Configuration-Manager.md)