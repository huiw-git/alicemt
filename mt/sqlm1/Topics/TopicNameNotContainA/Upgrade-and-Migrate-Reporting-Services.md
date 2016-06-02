---
title: Upgrade and Migrate Reporting Services
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 851a19a8-07ab-4d42-992f-1986c4c8df55
---
# Upgrade and Migrate Reporting Services
  This topic is an overview of the upgrade and migration options for [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)][!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]. There are two general approaches to upgrading a [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] deployment:  
  
-   **Upgrade:** You upgrade the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] components on the servers and instances where they are currently installed. This is commonly called an “in place” upgrade. In\-place upgrade is not supported from one mode of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] server to another. For example, you cannot upgrade a Native Mode report server to a SharePoint mode report server. You can migrate your report items from one mode to another. For more information, see the ‘Native to SharePoint Migration’ section later in this document.  
  
-   **Migrate**: You install and configure a new SharePoint environment, copy your report items and resources to the new environment, and configure the new environment to use existing content. A lower level form of migration is to copy the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] databases, configuration files, and if you are using SharePoint mode, the SharePoint content databases.  
  
||  
|-|  
|**[!INCLUDE[applies](../../Token\Other/applies_md.md)]**  [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint mode|  
  
##  <a name="bkmk_top"></a> In this topic:  
  
-   [Known Upgrade Issues and Best Practices](#bkmk_known_issues)  
  
-   [Side By Side Installations](#bkmk_side_by_side)  
  
-   [In-place Upgrade](#bkmk_inplace_upgrade)  
  
-   [Pre-Upgrade Checklist](#bkmk_upgrade_checklist)  
  
-   [Native Mode Upgrade and Migration Scenarios](#bkmk_native_scenarios)  
  
-   [Upgrade a Reporting Services Native Mode Scale-out Deployment](#bkmk_native_scaleout)  
  
-   [SharePoint Mode Upgrade and Migration Scenarios](#bkmk_sharePoint_scenarios)  
  
-   [Considerations for a Migration](#bkmk_migration_considerations)  
  
-   [Additional Resources](#bkmk_additional_resources)  
  
##  <a name="bkmk_known_issues"></a> Known Upgrade Issues and Best Practices  
 For a detailed list of the supported editions and versions you can upgrade, see [Supported Version and Edition Upgrades](../../Topics\TopicNameNotContainA/Supported-Version-and-Edition-Upgrades.md).  
  
> [!TIP]  
>  For the latest information regarding issues with [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], see the following:  
>   
>  -   [SQL Server 2016 Release Notes](http://go.microsoft.com/fwlink/?LinkID=398124).  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [In this topic:](#bkmk_top)  
  
##  <a name="bkmk_side_by_side"></a> Side By Side Installations  
 [!INCLUDE[ssRSCurrent](../../Token\Other/ssRSCurrent_md.md)] Native mode can be installed side\-by\-side with a [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] Native mode deployment.  
  
 There is no support for side\-by\-side deployments of [!INCLUDE[ssRSCurrent](../../Token\Other/ssRSCurrent_md.md)] SharePoint mode and any previous versions of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint mode components.  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [In this topic:](#bkmk_top)  
  
##  <a name="bkmk_inplace_upgrade"></a> In\-place Upgrade  
 Upgrade is completed by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup can be used to upgrade any or all [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] components, including [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]. Setup detects the existing instances and prompts you to upgrade. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup provides upgrade options that you can specify as a command\-line argument or in the Setup wizard.  
  
 When you run [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup, you can select the option to upgrade from one of the following versions or you can install a new instance of [!INCLUDE[ssRSCurrent](../../Token\Other/ssRSCurrent_md.md)] that runs side\-by\-side existing installations:  
  
-   [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)]  
  
-   [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)]  
  
-   [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)]  
  
 For more information on [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see the following:  
  
||  
|-|  
|[Upgrade to SQL Server 2016](../../Topics\TopicNameNotContainA/Upgrade-to-SQL-Server-2016.md)|  
|[Upgrade to SQL Server 2016 Using the Installation Wizard &#40;Setup&#41;](../Topic/Upgrade%20to%20SQL%20Server%202016%20Using%20the%20Installation%20Wizard%20\(Setup\).md)|  
|[Install SQL Server 2016 from the Command Prompt](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016-from-the-Command-Prompt.md)|  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [In this topic:](#bkmk_top)  
  
##  <a name="bkmk_upgrade_checklist"></a> Pre\-Upgrade Checklist  
 Before upgrading to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], review the following:  
  
-   Review requirements to determine whether your hardware and software can support [!INCLUDE[ssRSCurrent](../../Token\Other/ssRSCurrent_md.md)]. For more information, see [Hardware and Software Requirements for Installing SQL Server 2016](../../Topics\TopicNameNotContainA/Hardware-and-Software-Requirements-for-Installing-SQL-Server-2016.md).  
  
-   Use System Configuration Checker \(SCC\) to scan the report server computer for any conditions that might prevent a successful installation of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. For more information, see [Check Parameters for the System Configuration Checker](../../Topics\TopicNameNotContainA/Check-Parameters-for-the-System-Configuration-Checker.md).  
  
-   Review security best practices and guidance for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. For more information, see [Security Considerations for a SQL Server Installation](../../Topics\TopicNameContainA/Security-Considerations-for-a-SQL-Server-Installation.md).  
  
-   Back up your symmetric key. For more information, see [Back Up and Restore Reporting Services Encryption Keys](../../Topics\TopicNameNotContainA/Back-Up-and-Restore-Reporting-Services-Encryption-Keys.md).  
  
-   Back up your report server databases and configuration files. For more information, see [Backup and Restore Operations for Reporting Services](../../Topics\TopicNameNotContainA/Backup-and-Restore-Operations-for-Reporting-Services.md).  
  
-   Back up any customizations to existing [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] virtual directories in IIS.  
  
-   Remove invalid SSL certificates.  This includes certificates that are expired and you do not plan to update prior to upgrading Reporting Services.  Invalid certificates will cause upgrade to fail and an error message similar to the following will be written to the Reporting Services Log file: **Microsoft.ReportingServices.WmiProvider.WMIProviderException: A Secure Sockets Layer \(SSL\) certificate is not configured on the Web site.**.  
  
 Before you upgrade a production environment, always run a test upgrade in a pre\-production environment that has the same configuration as your production environment.  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [In this topic:](#bkmk_top)  
  
## Overview of Migration Scenarios  
 If you are upgrading from a supported version of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], you can usually run the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup Wizard to upgrade the report server program files, database, and all application data.  
  
 However, **migrating** a report server installation manually is required if you encounter any of the following conditions:  
  
-   You want to change the type of report server used in your deployment. For example, you cannot upgrade or convert a native mode report server to SharePoint mode. For more information, see [Native to SharePoint Migration &#40;SSRS&#41;](../Topic/Native%20to%20SharePoint%20Migration%20\(SSRS\).md).  
  
-   You want to minimize the amount of time the report server is taken offline during the upgrade process. Your current installation remains online while you copy content data to a new report server instance and test the installation without changing the state of your existing report server installation.  
  
-   You want to migrate a SharePoint 2010 deployment of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] to SharePoint 2013. SharePoint 2013 does not support in\-place upgrade from SharePoint 2010. For more information, see [Migrate a Reporting Services Installation &#40;SharePoint Mode&#41;](../Topic/Migrate%20a%20Reporting%20Services%20Installation%20\(SharePoint%20Mode\).md).  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [In this topic:](#bkmk_top)  
  
##  <a name="bkmk_native_scenarios"></a> Native Mode Upgrade and Migration Scenarios  
 **Upgrade:** In\-place upgrade for native mode is the same process for each of the supported versions that are listed earlier in this topic. Run the SQL Server installation wizard or a command line installation. Following installation the report server database will automatically upgrade to the new report server database schema. For more information, see the [In-place Upgrade](#bkmk_inplace_upgrade) section in this topic.  
  
 The upgrade process begins when you select an existing report server instance to upgrade.  
  
1.  If the report server database is on a remote computer and you do not have permission to update that database, Setup prompts you to provide credentials to update to a remote report server database. Be sure to provide credentials that have **sysadmin** or database update permissions.  
  
2.  Setup checks for conditions or settings that prevent upgrade and reads configuration settings. Examples include custom extensions deployed on the report server. If upgrade is blocked, you must either modify your installation so that upgrade is no longer blocked, or migrate to a new [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] instance. For more information, see the Upgrade Advisor documentation.  
  
3.  If upgrade can proceed, Setup prompts you to continue with the upgrade process.  
  
4.  Setup creates new folders for [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] program files. The program folders for a [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] installation include MSRS13.\<*instance name*\>.  
  
5.  Setup adds the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] report server program files, configuration tools, and command line utilities that are part of the report server feature.  
  
    1.  Program files from the previous version are removed.  
  
    2.  Report server configuration tools and utilities that are upgraded to the new version include the Native Mode [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration tool, command line utilities such as RS.exe, and Report Builder.  
  
    3.  Other client tools such as [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] and Books Online are not upgraded. To obtain new versions of the tools, you can add them when you run Setup. Earlier versions will co\-exist alongside [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] versions. If you installed samples, the earlier version will remain. Setup does not support upgrade for the SQL Server samples.  
  
    4.  [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] is a separate download. For more information, see [Microsoft SQL Server 2014 Data Tools \- Business Intelligence for Microsoft Visual Studio 2012](http://go.microsoft.com/fwlink/?LinkID=325512).  
  
6.  Setup reuses the service entry in Service Control Manager for the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Report Server service. This service entry includes the Report Server Windows service account.  
  
7.  Setup reserves new URLs based on existing virtual directory settings in IIS. Setup might not remove virtual directories in IIS, so be sure to remove those manually after upgrade is finished.  
  
8.  Setup merges settings in the configuration files. Using the configuration files from the current installation as the basis, new entries are added. Obsolete entries are not removed, but they will no longer be read by the report server after upgrade is finished. Upgrade will not delete old log files, the obsolete RSWebApplication.config file, or virtual directory settings in IIS. Upgrade will not remove older versions of Report Designer, Management Studio, or other client tools. If you no longer require them, be sure to remove these files and tools after upgrade is finished.  
  
 **Migration:** Migrating a previous version of a native mode installation to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] is the same steps for all of the supported versions that are listed earlier in this topic. For more information, see [Migrate a Reporting Services Installation &#40;Native Mode&#41;](../Topic/Migrate%20a%20Reporting%20Services%20Installation%20\(Native%20Mode\).md)  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [In this topic:](#bkmk_top)  
  
##  <a name="bkmk_native_scaleout"></a> Upgrade a Reporting Services Native Mode Scale\-out Deployment  
 The following is a summary of how to upgrade a [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Native mode deployment that is scaled–out to more than one report server. This process requires downtime of the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] deployment:  
  
1.  Backup the report server databases and encryption keys. For more information, see [Backup and Restore Operations for Reporting Services](../../Topics\TopicNameNotContainA/Backup-and-Restore-Operations-for-Reporting-Services.md) and [Add and Remove Encryption Keys for Scale-Out Deployment &#40;SSRS Configuration Manager&#41;](../Topic/Add%20and%20Remove%20Encryption%20Keys%20for%20Scale-Out%20Deployment%20\(SSRS%20Configuration%20Manager\).md).  
  
2.  Use the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager and remove all of the report servers from the scaled\-out deployment. For more information, see [Configure a Native Mode Report Server Scale-Out Deployment &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20a%20Native%20Mode%20Report%20Server%20Scale-Out%20Deployment%20\(SSRS%20Configuration%20Manager\).md).  
  
3.  Upgrade one of the report servers to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
4.  Use the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager to add the report servers back to the scale\-out deployment. For more information, see [Configure a Native Mode Report Server Scale-Out Deployment &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20a%20Native%20Mode%20Report%20Server%20Scale-Out%20Deployment%20\(SSRS%20Configuration%20Manager\).md).  
  
     For each server, repeat the upgrade and Scale\-out steps.  
  
##  <a name="bkmk_sharePoint_scenarios"></a> SharePoint Mode Upgrade and Migration Scenarios  
 The following sections describe the issues and basic steps needed to upgrade or migrate from specified versions of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint mode to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint mode.  
  
 There are two installation components to upgrade a [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint Mode deployment.  
  
-   [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint Shared Service.  
  
    > [!TIP]  
    >  Use the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint cmdlet `Get-SPRSServiceApplicationServers` to determine servers in the SharePoint farm that are currently running the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint Shared Service and therefore require an upgrade.  
  
-   [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Add\-in for SharePoint products. For more information, see [Install or Uninstall the Reporting Services Add-in for SharePoint](../../Topics\TopicNameNotContainA/Install-or-Uninstall-the-Reporting-Services-Add-in-for-SharePoint.md).  
  
 For detailed steps on Migrating a SharePoint mode installation, see [Migrate a Reporting Services Installation &#40;SharePoint Mode&#41;](../Topic/Migrate%20a%20Reporting%20Services%20Installation%20\(SharePoint%20Mode\).md).  
  
> [!IMPORTANT]  
>  Some of the following scenarios require down time of the SharePoint environment due to the different technologies that need to be upgraded. If your situation does not allow for down time, you will need to complete a migration instead of an in\-place upgrade.  
  
### [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]  
 **Starting environment:** [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] SP1, SharePoint 2010.  
  
 **Ending environment:** [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], SharePoint 2010 or SharePoint 2013.  
  
-   **SharePoint 2010:** In\-place upgrade of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] is supported but the upgrade scenario does require down time of the SharePoint environment.  
  
     If you also want the ending environment to run SharePoint 2013, you need to complete a database\-attach upgrade of the SharePoint 2010 to SharePoint 2013.  
  
-   **SharePoint 2013:** SharePoint 2013 does not support in\-place upgrade from SharePoint 2010. However the procedure of **database\-attach upgrade**  is supported. The behavior is different from upgrading to SharePoint 2010, where a customer could choose between the two basic upgrade approaches, in\-place upgrade and database\-attach upgrade.  
  
     If you have a [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] installation integrated with SharePoint 2010, you cannot upgrade in\-place the SharePoint server. However you can migrate content databases and service application databases from the SharePoint 2010 farm to a SharePoint 2013 farm.  
  
### [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]  
 **Starting environment:** [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] or [!INCLUDE[ssSQL11SP1](../../Token\Other/ssSQL11SP1_md.md)], SharePoint 2010.  
  
 **Ending environment:** [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], SharePoint 2010 or SharePoint 2013.  
  
-   **SharePoint 2010:** In\-place upgrade of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] is supported but the upgrade scenario does require down time of the SharePoint environment.  
  
     If you also want the ending environment to run SharePoint 2013, you need to complete a database\-attach upgrade of the SharePoint 2010 to SharePoint 2013.  
  
-   **SharePoint 2013:** SharePoint 2013 does not support in\-place upgrade from SharePoint 2010. However the procedure of **database\-attach upgrade**  is supported. The behavior is different from upgrading to SharePoint 2010, where a customer could choose between the two basic upgrade approaches, in\-place upgrade and database\-attach upgrade.  
  
     If you have a [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] installation integrated with SharePoint 2010, you cannot upgrade in\-place the SharePoint server. However you can migrate content databases and service application databases from the SharePoint 2010 farm to a SharePoint 2013 farm.  
  
### [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]  
 **Starting environment:** [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], SharePoint 2010.  
  
 **Ending environment:** [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], SharePoint 2010.  
  
-   In\-place upgrade is supported and there is no down time for your SharePoint environment.  
  
-   Install the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] version of the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] add\-in for SharePoint on each web front\-end in the farm. You can install the add\-in by using the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] installation wizard or by downloading the add\-in.  
  
-   Run [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] installation to upgrade SharePoint mode for each ‘report server’.The SQL Server installation wizard will install the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Service and create a new Service application.  
  
     If you also want the ending environment to run SharePoint 2013, you need to complete a database\-attach upgrade of the SharePoint 2010 to SharePoint 2013.  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [In this topic:](#bkmk_top)  
  
### [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] SP2 to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]  
 **Starting environment:** [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] SP2, SharePoint 2007.  
  
 **Ending environment:** [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], SharePoint 2010.  
  
-   This in\-place upgrade scenario does require down time of the SharePoint environment because both the SharePoint and SQL Server technologies need to be upgraded. You may want to consider completing a migration rather than an in\-place upgrade.  
  
-   Upgrade [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] to Service Pack 2 \(SP2\) first, if that has not already been completed.  
  
-   Upgrade SharePoint to 2010. When you run the SharePoint 2010 prerequisite installer it will upgrade the Reporting Services add\-in for SharePoint 2010 products.  
  
-   Install the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] version of the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] add\-in for SharePoint on all SharePoint web front\-ends. The SharePoint pre\-requisite installer installed the SQL Server 2008 R2 version of the add\-in but you need the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] version to work with a [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] report server.  
  
-   > [!WARNING]  
    >  Following the SharePoint upgrade your reporting services environment will be in a non\-working state until SQL Server is upgraded.  
  
-   Upgrade [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. When you run the SQL server installation wizard, you will a dialog regarding "**SQL Server Reporting Services SharePoint Mode Authentication**" dialog. The [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] service will be installed and the credentials from the authentication page will be used for creating a new SharePoint application pool.  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [In this topic:](#bkmk_top)  
  
##  <a name="bkmk_migration_considerations"></a> Considerations for a Migration  
 When moving application data, you should be aware of the following concerns and restrictions:  
  
-   Protection of encryption key includes a hash that incorporates machine identity.  
  
-   Report server database names are fixed and cannot be renamed on new computer.  
  
### Encryption Key Considerations  
 Always back up the encryption keys before moving a report server database to a new computer.  
  
 Moving a report server installation to another computer will invalidate the hash that protects the encryption keys used to help secure sensitive data stored in the report server database. Each report server instance that uses the database has its copy of the encryption key, which is encrypted with the identity of the service account as it is defined on the current computer. If you change computers, the service will no longer have access to its key, even if you use the same account name on the new computer.  
  
 To re\-establish reversible encryption on the new report server computer, you must restore the key that you previously backed up. The complete key set that is stored in the report server database consists of a symmetric key value, plus service identity information used to restrict access to the key so that it can be used only by the report server instance that stored it. During key restoration, the report server replaces existing copies of the key with new versions. The new version includes machine and service identity values as defined on the current computer. For more information, see the following topics:  
  
-   SharePoint mode: See the “Key Management” section of [Manage a Reporting Services SharePoint Service Application](../../Topics\TopicNameContainA/Manage-a-Reporting-Services-SharePoint-Service-Application.md)  
  
-   Native Mode: See [Back Up and Restore Reporting Services Encryption Keys](../../Topics\TopicNameNotContainA/Back-Up-and-Restore-Reporting-Services-Encryption-Keys.md)  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [In this topic:](#bkmk_top)  
  
### Fixed Database Name  
 You cannot rename the report server database. The identity of the database is recorded in report server stored procedures when the database is created. Renaming either the report server primary or temporary databases will cause errors to occur when the procedures run, invalidating your report server installation.  
  
 If the database name from the existing installation is not suited for the new installation, you should consider creating a new database that has the name that you prefer, and then load existing application data using the techniques in the following list:  
  
-   Write a [!INCLUDE[vbprvb](../../Token\Other/vbprvb_md.md)] script that calls Report Server Web service SOAP methods to copy data between databases. You can use the RS.exe utility to run the script. For more information about this approach, see [Scripting and PowerShell with Reporting Services](../../Topics\TopicNameNotContainA/Scripting-and-PowerShell-with-Reporting-Services.md).  
  
-   Write code that calls the WMI provider to copy data between databases. For more information about this approach, see [Access the Reporting Services WMI Provider](../../Topics\TopicNameNotContainA/Access-the-Reporting-Services-WMI-Provider.md).  
  
-   If you have just a few items, you can republish reports, report models, and shared data sources from Report Designer, Model Designer, and Report Builder to the new report server. You must re\-create role assignments, subscriptions, shared schedules, report snapshot schedules, custom properties that you set on reports or other items, model item security, and properties that you set on the report server. You will lose report history and report execution log data.  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [In this topic:](#bkmk_top)  
  
##  <a name="bkmk_additional_resources"></a> Additional Resources  
  
> [!NOTE]  
>  For more information on SharePoint database\-attach upgrade, see the following:  
  
-   [Overview of the upgrade process to SharePoint 2013](http://go.microsoft.com/fwlink/p/?LinkId=256688) \(http:\/\/go.microsoft.com\/fwlink\/p\/?LinkId\=256688\).  
  
-   [Clean up preparations before an upgrade to SharePoint 2013](http://go.microsoft.com/fwlink/p/?LinkId=256689) \(http:\/\/go.microsoft.com\/fwlink\/p\/?LinkId\=256689\).  
  
-   [Upgrade databases from SharePoint 2010 to SharePoint 2013](http://go.microsoft.com/fwlink/p/?LinkId=256690) \(http:\/\/go.microsoft.com\/fwlink\/p\/?LinkId\=256690\).  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [In this topic:](#bkmk_top)  
  
## See Also  
 [Upgrade Reports](../../Topics\TopicNameNotContainA/Upgrade-Reports.md)   
 [Upgrade to SQL Server 2016 Using the Installation Wizard &#40;Setup&#41;](../Topic/Upgrade%20to%20SQL%20Server%202016%20Using%20the%20Installation%20Wizard%20\(Setup\).md)  
  
  