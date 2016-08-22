---
title: "Install in-console updates for System Center Configuration Manager"
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
ms.assetid: c14a3607-253b-41fb-8381-ae2d534a9022
caps.latest.revision: 34
---
# Install in-console updates for System Center Configuration Manager
[!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] synchronizes with the Microsoft cloud service to get updates you can then install from within the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. 

## Get available updates
Only updates that apply to your infrastructure and version are downloaded and made available to your hierarchy. This synchronization can be automatic, or manual depending on how you configure the service connection point for your hierarchy: 
  
-   In **online mode**, the service connection point automatically connects to the Microsoft cloud service and downloads applicable updates.  
  
     By default, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] checks for new updates every 24 hours. Beginning with version 1602 or later, you can also check for updates immediately by clicking **Check for Updates** in the **Administration** > **Cloud Services** > **Updates and Servicing** node of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
-   In **offline mode**, the service connection point does not connect to the Microsoft cloud service and you must manually [Use the Service Connection Tool for System Center Configuration Manager](../System Center Configuration Manager/Use-the-Service-Connection-Tool-for-System-Center-Configuration-Manager.md) to download and then import available updates.  
  
> [!NOTE]  
>  In addition to the updates you get when synchronizing with the Microsoft cloud service, out-of-band fixes that install using the [Update Registration Tool](http://technet.microsoft.com/library/mt691544.aspx) are also imported into your console where you can then select them to install.  
  
 After updates are synchronized you can view them in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console by navigating to the **Administration** > **Cloud Services** > **Updates and Servicing** node:  
  
-   Updates you have not installed display as **Available**.
  
-   Updates you have installed display as **Installed**.  Beginning with release 1606, only the most recently installed update is displayed, and you can click the **History** button on the ribbon to view previously installed updates.
  
  
  
 Before you configure the service connection point, understand and plan for its additional uses which might affect how you configure this site system role:  
  
-   The service connection point is used to upload usage information about your site. This information helps the Microsoft cloud service identify the updates that are available for the current version of your infrastructure. For more information see [Diagnostics and usage data for System Center Configuration Manager](../System Center Configuration Manager/Diagnostics-and-usage-data-for-System-Center-Configuration-Manager.md)  
  
-   The service connection point is used to manage devices with [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)], and using [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] on-premises mobile device management. For more information see   [Hybrid mobile device management (MDM) with System Center Configuration Manager and Microsoft Intune](../System Center Configuration Manager/Hybrid-mobile-device-management--MDM--with-System-Center-Configuration-Manager-and-Microsoft-Intune.md).  
  
 To better understand what happens updates are downloaded, see:  
  
-   [Flowchart - Download updates for System Center Configuration Manager](../System Center Configuration Manager/Flowchart---Download-updates-for-System-Center-Configuration-Manager.md).  
  
-   [Flowchart - Update replication for System Center Configuration Manager](../System Center Configuration Manager/Flowchart---Update-replication-for-System-Center-Configuration-Manager.md)  

## Permissions to view and manage updates and features
 Prior to installing update 1606, to view updates in the console, a user must be assigned a security role that includes the **Read** permission in the permission group **Site**, and the security scope **All**. Beginning with update 1606, a new role-based administration security class named **Update packages** is introduced that grants access to view and manage updates in the Configuration Manager console.    

**About the Update packages class:**  
 By default, **Update packages** (SMS_CM_Updatepackages) is part of the following built-in security roles with the listed permissions:
 -  **Full Administrator** with **Modify** and **Read** permissions:
    -   A user with this security role and access to the **All** security scope can view updates, install updates and enable features during the install, and enable individual features after the update has previously installed. 
    - A user with this security role and access to the **Default** security scope can view updates, install updates and enable features during the install, and view features after an update has installed but not enable the features after the update has previously installed. 
  -  **Read-only Analyst** with **Read** permissions: 
     -  A user with this security role and access to the **Default** scope can view updates but not install them, and can view features after an update has installed but cannot enable them.

 **Summary of permissions required for updates and servicing:**   
  - Use an account that is assigned a security role that includes the **Update packages** class with both **Modify** and **Read** permissions. 
  - The account must be assigned the **Default** scope.
  
**To only view updates**: 
  - Use an account that is assigned a security role that includes **Update packages** class with only the **Read** permission. 
  - The account must be assigned the **Default** scope.

**To enable Features after updates are installed:** 
  -   Use an account that is assigned a security role that includes the **Update packages** class with both **Modify** and **Read** permissions.
  -  The account must be assigned the **All** scope. 

  
  


  
##  <a name="bkmk_beforeinstall"></a> Before you install an in-console update  
 Review the following steps before installing updates from within the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console:  
  
###  <a name="bkmk_step1"></a> Step 1: Review the update checklist  
 Before installing a new update from within the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, review the applicable  
update checklist for actions to take before starting the update:  
  
-   Upgrade to 1511 from [Upgrade to System Center Configuration Manager](../System Center Configuration Manager/Upgrade-to-System-Center-Configuration-Manager.md)    
  
-   Update to 1602 from 1511: See  [Checklist for installing update 1602](../System Center Configuration Manager/Checklist-for-installing-update-1602-for-System-Center-Configuration-Manager.md)

- Update to 1606 from either 1511 or 1602: See [Checklist for installing update 1606](../System Center Configuration Manager/Checklist-for-installing-update-1606-for-System-Center-Configuration-Manager.md)  
  
  
###  <a name="bkmk_step2"></a> Step 2: Test the database upgrade before installing an update  
 Before you install a new update in your hierarchy, like update 1602, you should test the upgrade of your site database. The name of the command line option you use to test installing an update to a backup of your site database is **testdbupgrade**.  
  
 Unlike past versions of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], if installing an update fails you should not need to perform a site recovery and instead can Retry the update installation. Therefore, while the test upgrade of the database is less critical than in past product versions it remains a recommended step.  
  
##### To run testdbupgrade before installing an update  
  
1.  Obtain a set of source files from the **CD.Latest** folder of a site that runs the version you plan to update to. This might require you to first install a site in a lab or test environment that runs that version of [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)].  
  
     The **CD.Latest** folder for a site contains the source files for that version. You must use these source files to run the test upgrade of your site database. For more information see [The CD.Latest folder for System Center Configuration Manager](../System Center Configuration Manager/The-CD.Latest-folder-for-System-Center-Configuration-Manager.md).  
  
     For example, if your site runs version 1501 and you want to update to 1602, you must get a CD.Latest folder from a site that has already updated to version 1602. Typically, you can install a new and temporary site in a lab, and upgrade that to version 1602 to create the CD.Latest folder with the required files.  
  
2.  Copy the CD.Latest folder to a location on the SQL Server that you will use to run the test database upgrade. (See the next step).  
  
3.  Create a backup of the site database that you want to test upgrade, and then restore a copy of that database to an instance of SQL Server that does not host a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site. The SQL Server must use the same edition of SQL Server as your site database.  
  
4.  After you restore the database copy, run **Setup** from the CD.Latest folder you copied from your lab or test environment. When you run Setup, use the **/TESTDBUPGRADE** command-line option. If the SQL Server instance that hosts the database copy is not the default instance, you must also provide the command-line arguments to identify the instance that hosts the site database copy.  
  
     For example, you plan to upgrade a site database with the database name SMS_ABC. You restore a copy of this site database to a supported instance of SQL Server with the instance name DBTest. To test an upgrade of this copy of the site database, use the following command line: **Setup.exe /TESTDBUPGRADE DBtest\CM_ABC**  
  
     You can find Setup.exe in the following location on the source media for [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]: **SMSSETUP\BIN\X64**.  
  
5.  On the instance of SQL Server where you run the database upgrade test, monitor the ConfigMgrSetup.log in the root of the system drive for progress and success.  
  
     If the test upgrade fails, resolve any issues related to the site database upgrade failure, create a new backup of the site database, and then test the upgrade of the new copy of the site database.  
  
     After the process is successful, you can delete the database copy.  
  
    > [!NOTE]  
    >  It is not supported to restore the copy of the site database that you use for the test upgrade for use as a site database at any site.  
  
###  <a name="bkmk_step3"></a> Step 3: Run the prerequisite checker before installing an update  
 Before you install an update, consider running the prerequisite check for that update. If you run the prerequisite before installing an update:  
  
-   The update files are replicated to other sites in advance of actually installing the update  
  
-   The prerequisite check will automatically run again when you choose to install the update  
  
 Later, when you install  an update, you have the option to configure the update to ignore prerequisite check warnings.  
  
##### To run the prerequisite checker before installing an update  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, go to **Administration** > **Cloud Services** > **Updates and Servicing**.  
  
2.  Right click on the update package you want to run the prerequisite check for.  
  
3.  Choose **Run prerequisite check**.  You can view the  
  
     When you run the prerequisite check, content for the update replicates to child sites.  You can view the **distmgr.log** on the site server to confirm that content replicates successfully.  
  
4.  To view the results of the check, in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console go to **Monitoring** > **Updates and Servicing Status** and look for the prerequisite status. You can also view the ConfigMgrPrereq.log on the site server for more details.  


  
##  <a name="bkmk_install"></a> Install in-console updates  
 When you are ready to install updates from within the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, you begin with the top-tier site of your hierarchy. This is either the central administration site or a stand-alone primary site.  
  
 We recommend you plan to install the update outside of normal business hours for each site when the process of installing the update and its actions to reinstall site components and site system roles will have the least effect on your business operations.  
  
-   Child primary sites start the update automatically after the central administration site completes installation of the update. You can use [Service Windows for site servers](#bkmk_ServiceWindow) to control when a site installs updates.  
  
-   You must manually update secondary sites from within the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console after the primary parent site update is complete. Automatic update of secondary site servers is not supported.  
  
-   When you use a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console after the site updates, you are prompted to update the console.  
  
###  <a name="bkmk_overview"></a> Overview of in-console update installation  
 **1. When the update installation starts**  
  
 You are presented with the Updates Wizard that displays a list of the product areas that the update applies to.  
  
-   On the **General** page of the wizard, you can configure **Prerequisite warnings**.  
      -   Prerequisite errors always stop the update installation. You must resolve errors before you will be able to successfully retry the update installation. See [Retry installation of a failed update](#bkmk_retry) for more information.  
  
    -   Prerequisite warnings can also stop the update installation. You should resolve warnings before you retry the update installation.   See [Retry installation of a failed update](#bkmk_retry) for more information.  
    -   Selecting the option **Ignore any prerequisite check warnings and install this update regardless of missing requirements**, sets a condition for the update install that ignores prerequisite warnings, and allows update installation to continue. If you do not select this option, the update install will stop when a warning is encountered. Unless you have previously run the prerequisite check and resolved prerequisite warnings for a site, we do not recommend use of this option.  
    
        Beginning with version 1606, both the **Administration** and **Monitoring** workspaces, the Updates and Servicing node includes a button on the Ribbon named **Ignore prerequisite warnings**. This button become available when an update package fails to complete installation due to prerequisite check warnings.  For example, if you install an update without using the option to Ignore prerequisite warnings (from within the Updates Wizard), and that update installation halts with a state of prerequisite warning but no errors, you can later select **Ignore prerequisite warnings** from the ribbon to trigger an automatic continuation of that update install that then ignores prerequisite warnings.  When this option is used, the update installation automatically continues after a few minutes. 
  

  
-   When an update applies to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client, you are presented with the option to test the client update with a limited set of clients. For more information see [How to test client upgrades in a preproduction collection in System Center Configuration Manager](../System Center Configuration Manager/How-to-test-client-upgrades-in-a-preproduction-collection-in-System-Center-Configuration-Manager.md).  
  
 **2. During the update installation**  
  
 As part of the update installation, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]:  
  
-   Reinstalls any affected components like site system roles or the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console  
  
-   Manages updates to clients based on the selections you made for client piloting, and for [automatic client upgrades](https://technet.microsoft.com/library/mt627885.aspx)  
  
-   Will not need to reboot site system servers as part of the update (unless .NET is installed as part of a site system roles prerequisite)  
  
> [!TIP]  
>  When updates are installed,  [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] also updates  the CD.Latest folder which is used during a site recovery.  
  
 **3. Monitor the progress of updates as they install**  
  
 Use the following to monitor progress:  
  
-   In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console: **Administration** > **Cloud Services** > **Updates and Servicing** node. This node shows the installation status for all update packages. 

  
-   In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console: **Monitoring** > **Overview** > **Updates and Servicing Status** node. this node shows the installation status of only the update package that is currently installing.  

    Beginning with version 1606, the update pack installation is broken down to following phases for ease of monitoring. For each phase there is now additional details including which log file to view for more information:  
    -   **Download** (This applies only to the top-tier site where the service connection point site system role is installed)
    -   **Replication**
    - **Prerequisites Check**
    - **Installation**
  
-   You can view the **CMUpdate.log** file in **<ConfigMgr_Installation_Directory>\Logs\\**  
  
 **4. When the update installation completes**  
  
 After the first site update completes installation:  
  
-   Child primary sites will install the update automatically. No further action is required.  
  
-   Secondary sites must be manually updated from within the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
-   Until all sites in your hierarchy update to the new version, your hierarchy operates in a mixed version mode. For more information, see [Interoperability between different versions of System Center Configuration Manager](../System Center Configuration Manager/Interoperability-between-different-versions-of-System-Center-Configuration-Manager.md).  
  
 **5.   Update Configuration Manager consoles**  
  
 After a central administration site or primary site updates, each [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console that connects to that site must also update. You are prompted to update a console:  
  
-   When you open the console  
  
-   When you navigate to a new node in an open console  
  
 We recommend that you install the update immediately, and not delay.  
  
 After the console update completes, you can verify the console and site version is correct. Go to **About System Center Configuration Manager** at the top-left corner of the console where the new site and console version displays.  
  
###  <a name="bkmk_toptier"></a> To start the update installation at the top-tier site  
 At the top-tier site of your hierarchy, in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console go to **Administration** > **Cloud Services** > **Updates and Servicing**, select an **Available** update and then click **Install Update Pack**.  
  
###  <a name="bkmk_secondary"></a> To start the update installation at a secondary site  
  After a secondary sites parent primary site is updated, you can then update the secondary site from within the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  To do so, you use the **Upgrade Secondary Site Wizard**.  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console go to **Administration** > **Site Configuration** > **Sites**, select the site you want to update, and then on the Home tab, in the Site group, click **Upgrade**.  
  
2.  Click **Yes** to start the update of the secondary site.  
  
 To monitor the update installation on a secondary site, select the secondary site server, and then on the Home tab, in the Site group, click **Show Install Status**. You can also add the **Version** column to the console display so that you can view the version of each secondary site.  
  
##  <a name="bkmk_retry"></a> Retry installation of a failed update  
 When an update fails to install, review the in-console feedback to identify resolutions for warnings and errors.  You can also view the ConfigMgrPrereq.log on the site server for more details. Before retrying the installation of an update you must resolve errors, and should resolve warnings.  
 
When you are ready to retry the installation of an update, select the failed update and then select an applicable option. The update install retry behavior depends on the node from which you start the retry, and the retry option you use:  
1.  **Retry installation for the hierarchy:**  
  
     You can retry the installation of an update for the entire hierarchy when that update is in one of the following states:  
  
    -   Prerequisite check passed with one or more warnings, and option to ignore prerequisite check warnings was not set in the Update Wizard (The updates value for **Ignore Prereq Warning** in the Updates and servicing node is **No**)   
    -   Prerequisite failed    
    -   Installation failed 
    -   Replication of the content to the site failed   
  
     Go to **Administration** > **Cloud Services** > **Updates and Servicing**, select the update and then click one of the following:  
  
    -   **Retry** - When you run Retry from this node, the update install starts again and will automatically ignore prerequisite warnings. It will also re-replicate content for the update if replication previously failed. 
    - **Ignore prerequisite warnings** - Beginning with version 1606, if the update install halts due to a warning, you can then click Ignore prerequisite warnings. This action allows the installation of the update to continue (after a few minutes) and uses the option to ignore prerequisite warnings. 
 
  
2.  **Retry installation for the site:**  
  
     You can retry the installation of an update at a specific site when that update is in one of the following states:  
  
    -   Prerequisite check passed with one or more warnings, and option to ignore prerequisite check warnings was not set in the Update Wizard (The updates value for **Ignore Prereq Warning** in the Updates and servicing node is **No**)  
    -   Prerequisite failed    
    -   Installation failed    
     
    Go to **Monitoring** > **Overview** > **Site Servicing Status**, select the update and then click one of the following:
      
       - **Retry** - When you run Retry from this node, you restart the installation of the update at only that site. Unlike running Retry from the Updates and Servicing node, this retry does not ignore prerequisite warnings. 
       -    **Ignore prerequisite warnings** - Beginning with version 1606, if the update install halts due to a warning, you can then click Ignore prerequisite warnings. This action allows the installation of the update to continue (after a few minutes) and uses the option to ignore prerequisite warnings.
  
##  <a name="bkmk_after"></a> After a site installs an update  
 Use the following checklist to complete common tasks and configurations that are made after a site updates:  
  
 **Confirm site to site replication is active:** In the  [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, go to the following locations to view status and ensure replication is active:  
  
-   **Monitoring** > **Overview** > **Site Hierarchy**  
  
-   **Monitoring** > **Overview** > **Database Replication**  
  
 For more information, see   
[Monitor hierarchy and replication infrastructure in System Center Configuration Manager](../System Center Configuration Manager/Monitor-hierarchy-and-replication-infrastructure-in-System-Center-Configuration-Manager.md) and [About the Replication Link Analyzer](../System Center Configuration Manager/Monitor-hierarchy-and-replication-infrastructure-in-System-Center-Configuration-Manager.md#BKMK_RLA).  
  
 **Confirm site servers and remote site system servers have restarted (if required):** Review your site infrastructure and ensure applicable site servers and site system servers (remote from the site server) have rebooted successfully.  Typically, this is expected only when [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] installs .NET as a prerequisite for a site system role.  
  
 **Update stand-alone Configuration Manager consoles:** Ensure all remote [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] consoles update to the same version. You are prompted to update the console when:  
  
-   You navigate to a new node in the console  
  
-   When you open the console  
  
 **Reconfigure database replicas for management points at primary sites:** If you use database replicas for management points at primary sites, you must uninstall the database replicas before you update the site. After you update a primary site, reconfigure the database replica for management points. For more information, see [Database replicas for management points for System Center Configuration Manager](../System Center Configuration Manager/Database-replicas-for-management-points-for-System-Center-Configuration-Manager.md).  
  
 **Reconfigure any database maintenance tasks you disabled prior to the update:** If you disabled database [Maintenance tasks for System Center Configuration Manager](../System Center Configuration Manager/Maintenance-tasks-for-System-Center-Configuration-Manager.md) at a site prior to the update, reconfigure those tasks at the site using the same settings that were in place prior to the update.  
  
 **Upgrade clients:** For information about how to upgrade existing clients and how to install new clients, see [How to upgrade clients for Windows computers in System Center Configuration Manager](../System Center Configuration Manager/How-to-upgrade-clients-for-Windows-computers-in-System-Center-Configuration-Manager.md)  
  
 **Additional configurations:** Review the changes you made before starting the update and then restore those configurations to your sites and hierarchy.  
  
##  <a name="bkmk_options"></a> Enable optional features from updates  
 When you install an update that includes one or more optional features, you will have the opportunity to enable those features in your hierarchy.  You can do so at the time the update installs, or return to the console at a later time and enable the optional features. 
 
 To view available features and their status, in the console navigate to **Administration** > **Cloud Services** > **Updates and Servicing** > **Features**.
  
 When a feature is not optional, it installs automatically and does not appear in the **Features** node.  
  
##  <a name="bkmk_prerelease"></a> Use pre-release features from updates
Beginning with 1606, you must give consent to use Pre-release features in System Center Configuration Manager before you can select and enable their use.  
 
Pre-release features are included in the product for early testing in a production environment, but should not be considered production ready.

To give consent, in the console navigate to **Administration** > **Site Configuration** > **Sites**, and then select **Hierarchy Settings**. On the **General** tab, select **Consent to use Pre-Release features**. 
 -  Giving consent is a one-time action per hierarchy that cannot be undone  
 -  Until you give consent, you cannot enable new pre-release features included with update 1606 or later update versions
 > [!NOTE]
 > If you have enabled pre-release features from Update 1602 prior to installing update 1606, those features remain enabled for use after installing 1606 even if you do not give consent to use pre-release features.
 
  When your hierarchy runs version 1606 or later, and you then install an update that includes pre-release features, those features are visible in the Updates and Servicing Wizard with the regular features included in the update: 
  - **If you have given consent:** You can enable pre-release features from within the Updates and Servicing Wizard when you are installing the update. To do so, select the pre-release features as you would any other feature.     
  
    Optionally, you can wait to enable a pre-release feature at a later time from the **Administration** > **Cloud Services** > **Updates and Servicing** > **Features** node of the console. To do so, in the Features node select the feature and then click **Turn on**. (This option is greyed out and unavailable until you give consent.)  
-   **If you have not given consent:** When installing an update, pre-release features are visible in the Updates and Servicing Wizard but are greyed out and cannot be enabled. After the update installs, you can view these features in the Features node, but not enable them until after you have given consent in the Hierarchy Settings.  
 > [!TIP]
 > When you are installing update 1606, pre-release features that are included with update 1606 are not visible in the Updates and Servicing Wizard and cannot be enabled at that time. After update 1606 installs you can view the pre-release features it includes in the Features node. 

##  <a name="bkmk_ServiceWindow"></a> Service Windows for site servers  
 On a site server you can configure service windows to control when infrastructure updates for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] can be applied to that site server.  Each site server supports multiple windows, with the window allowed for installing infrastructure updates determined by a combination of  all configured windows for that site server.  
  
 **To configure a service window:**  
  
1.  In  [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console open **Administration** > **Site Configuration** > **Sites**, and then select the site server where you want to configure a service window.  
  
2.  Next, edit the site servers **Properties** and select the **Service Window** tab, where you can then set one or more service windows for that site server.  
  
##  <a name="bkmk_faq"></a> Why don’t I see certain updates in my console?  
 If you cannot find a specific update, or any updates in your console after a successful sync with the Microsoft cloud service, this might be because:  
  
-   The update requires a configuration that your infrastructure does not use, or your current product version does not fulfill a prerequisite for receiving the update.  
  
     If you believe you have the required configurations or meet other prerequisites for a missing update, confirm your service connection point is in online mode and then use the **Check for Updates** option in the Updates and Servicing node to force a check.  If you are in offline mode, you must use the service connection tool to manually sync with the cloud service.  
  
-   Your account lacks the correct role-based administration permissions to view updates in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.
  
    See [Permissions to manage updates](../System Center Configuration Manager/Install-in-console-updates-for-System-Center-Configuration-Manager.md#Permissions-to-view-and-manage-updates-and-features) in this topic for information about required permissions to view updates and enable features from within the console. 
  
  
## See Also  
 [Updates for System Center Configuration Manager](../System Center Configuration Manager/Updates-for-System-Center-Configuration-Manager.md)