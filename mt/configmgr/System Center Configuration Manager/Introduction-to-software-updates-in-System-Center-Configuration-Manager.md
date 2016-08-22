---
title: "Introduction to software updates in System Center Configuration Manager"
ms.custom: na
ms.date: 2016-07-22
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-sum
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: e9778b13-c8a3-40eb-8655-34ac8ce9cdaa
caps.latest.revision: 12
---
# Introduction to software updates in System Center Configuration Manager
Software updates in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] provides a set of tools and resources that can help manage the complex task of tracking and applying software updates to client computers in the enterprise. An effective software update management process is necessary to maintain operational efficiency, overcome security issues, and maintain the stability of the network infrastructure. However, because of the changing nature of technology and the continual appearance of new security threats, effective software update management requires consistent and continual attention.  
  
 See the following sections for more information about software updates:  
  
-   [Software updates synchronization](#BKMK_Synchronization)  
  
-   [Software updates compliance assessment](#BKMK_SUMCompliance)  
  
-   [Software update deployment packages](#BKMK_DeploymentPackages)  
  
-   [Software update deployment workflows](#BKMK_DeploymentWorkflows)  
  
-   [Software update deployment process](#BKMK_DeploymentProcess)  
  
-   [Extend software updates in Configuration Manager](#BKMK_ExtendSoftwareUpdates)  
  
-   [Support for Windows embedded devices that use write filters](#BKMK_EmbeddedDevices)  

-   [Restart options for Windows 10 clients after software update installation](#BKMK_RestartOptions)
  
 For an example scenario that shows how you might deploy software updates in your environment, see [Example scenario for using System Center Configuration Manager to deploy and monitor the security software updates released monthly by Microsoft](../System Center Configuration Manager/Example-scenario-for-using-System-Center-Configuration-Manager-to-deploy-and-monitor-the-security-software-updates-released-monthly-by-Microsoft.md).  
  
##  <a name="BKMK_Synchronization"></a> Software updates synchronization  
 Software updates synchronization in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] uses Microsoft Update to retrieve software updates metadata. The top-level site (central administration site or stand-alone primary site) synchronizes with Microsoft Update on a schedule or when you manually start synchronization from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. When [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] finishes software updates synchronization at the top-level site, software updates synchronization starts at child sites, if they exist. When synchronization is complete at each primary site or secondary site, a site-wide policy is created that provides to client computers the location of the software update points.  
  
> [!NOTE]  
>  Software updates are enabled by default in client settings. However, if you set the **Enable software updates on clients** client setting to **No** to disable software updates on a collection or in the default settings, the location for software update points are not sent to associated clients. For more information about the software updates client settings, see the [Software Updates](../System Center Configuration Manager/About-client-settings-in-System-Center-Configuration-Manager.md#BKMK_SoftwareUpdatesDeviceSetting) section in the [About client settings in System Center Configuration Manager](../System Center Configuration Manager/About-client-settings-in-System-Center-Configuration-Manager.md) topic.  
  
 After the client receives the policy, the client starts a scan for software updates compliance and writes the information to Windows Management Instrumentation (WMI). The compliance information is then sent to the management point that then sends the information to the site server. For more information about compliance assessment, see the [Software updates compliance assessment](#BKMK_SUMCompliance) section in this topic.  
  
 You can install multiple software update points at a primary site. The first software update point that you install is configured as the synchronization source. This synchronizes from Microsoft Update or a WSUS server not in your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy. The other software update points at the site use the first software update point as the synchronization source.  
  
> [!NOTE]  
>  When the software updates synchronization process is complete at the top-level site, the software updates metadata is replicated to child sites by using database replication. When you connect a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console to the child site, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] displays the software updates metadata. However, until you install and configure a software update point at the site, clients will not scan for software updates compliance, clients will not report compliance information to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], and you cannot successfully deploy software updates.  
  
### Synchronization on the top-level site  
 The software updates synchronization process at the top-level site retrieves from Microsoft Update the software updates metadata that meet the criteria that you specify in Software Update Point Component properties. You configure the criteria only at the top-level site.  
  
> [!NOTE]  
>  You can specify an existing WSUS server that is not in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy instead of Microsoft Updates as the synchronization source.  
  
 The following list describes the basic steps for the synchronization process on the top-level site:  
  
1.  Software updates synchronization starts.  
  
2.  WSUS Synchronization Manager sends a request to WSUS running on the software update point to start synchronization with Microsoft Update.  
  
3.  The software updates metadata is synchronized from Microsoft Update, and any changes are inserted or updated in the WSUS database.  
  
4.  When WSUS has finished synchronization, WSUS Synchronization Manager synchronizes the software updates metadata from the WSUS database to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database, and any changes after the last synchronization are inserted or updated in the site database. The software updates metadata is stored in the site database as a configuration item.  
  
5.  The software updates configuration items are sent to child sites by using database replication.  
  
6.  When synchronization has finished successfully, WSUS Synchronization Manager creates status message 6702.  
  
7.  WSUS Synchronization Manager sends a synchronization request to all child sites.  
  
8.  WSUS Synchronization Manager sends a request one at a time to WSUS running on other software update points at the site. The WSUS servers on the other software update points are configured to be replicas of WSUS running on the default software update point at the site.  
  
### Synchronization on child primary and secondary sites  
 During the software updates synchronization process on the top-level site, the software updates configuration items are replicated to child sites by using database replication. At the end of the process, the top-level site sends a synchronization request to the child site, and the child site starts the WSUS synchronization. The following list provides the basic steps for the synchronization process on a child primary site or secondary site:  
  
1.  WSUS Synchronization Manager receives a synchronization request from the top-level site.  
  
2.  Software updates synchronization starts.  
  
3.  WSUS Synchronization Manager makes a request to WSUS running on the software update point to start synchronization.  
  
4.  WSUS running on the software update point on the child site synchronizes software updates metadata from WSUS running on the software update point on the parent site.  
  
5.  When synchronization has finished successfully, WSUS Synchronization Manager creates status message 6702.  
  
6.  From a primary site, WSUS Synchronization Manager sends a synchronization request to any child secondary sites. The secondary site starts the software updates synchronization with the parent primary site. The secondary site is configured as a replica of WSUS running on the parent site.  
  
7.  WSUS Synchronization Manager sends a request one at a time to WSUS running on other software update points at the site. The WSUS servers on the other software update points are configured to be replicas of WSUS running on the default software update point at the site.  
  
##  <a name="BKMK_SUMCompliance"></a> Software updates compliance assessment  
 Before you deploy software updates to client computers in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], start a scan for software updates compliance on client computers. For each software update, a state message is created that contains the compliance state for the update. The state messages are sent in bulk to the management point and then to the site server, where the compliance state is inserted into the site database. The compliance state for software updates is displayed in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. You can deploy and install software updates on computers that require the updates. The following sections provide information about the compliance states and describe the process for scanning for software updates compliance.  
  
### Software updates compliance states  
 The following lists and describes each compliance state that is displayed in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console for software updates.  
  
-   **Required**  
  
     Specifies that the software update is applicable and required on the client computer. Any of the following conditions could be true when the software update state is **Required**:  
  
    -   The software update was not deployed to the client computer.  
  
    -   The software update was installed on the client computer. However, the most recent state message has not yet been inserted into the database on the site server. The client computer rescans for the update after the installation has finished. There might be a delay of up to two minutes before the client sends the updated state to the management point that then forwards the updated state to the site server.  
  
    -   The software update was installed on the client computer. However, the software update installation requires a computer restart before the update is completed.  
  
    -   The software update was deployed to the client computer but has not yet been installed.  
  
-   **Not Required**  
  
     Specifies that the software update is not applicable on the client computer. Therefore, the software update is not required.  
  
-   **Installed**  
  
     Specifies that the software update is applicable on the client computer and that the client computer already has the software update installed.  
  
-   **Unknown**  
  
     Specifies that the site server has not received a state message from the client computer, typically because one of the following:  
  
    -   The client computer did not successfully scan for software updates compliance.  
  
    -   The scan finished successfully on the client computer. However, the state message has not yet been processed on the site server, possibly because of a state message backlog.  
  
    -   The scan finished successfully on the client computer, but the state message has not been received from the child site.  
  
    -   The scan finished successfully on the client computer, but the state message file was corrupted in some way and could not be processed.  
  
### Scan for software updates compliance process  
 When the software update point is installed and synchronized, a site-wide machine policy is created that informs client computers that [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] software updates was enabled for the site. When a client receives the machine policy, a compliance assessment scan is scheduled to start randomly within the next two hours. When the scan is started, a Software Updates Client Agent process clears the scan history, submits a request to find the WSUS server that should be used for the scan, and updates the local Group Policy with the WSUS server location.  
  
> [!NOTE]  
>  Internet-based clients must connect to the WSUS server by using SSL.  
  
 A scan request is passed to the Windows Update Agent (WUA). The WUA then connects to the WSUS server location that is listed in the local policy, retrieves the software updates metadata that has been synchronized on the WSUS server, and scans the client computer for the updates. A Software Updates Client Agent process detects that the scan for compliance has finished, and it creates state messages for each software update that changed in compliance state after the last scan. The state messages are sent to the management point in bulk every 15 minutes. The management point then forwards the state messages to the site server, where the state messages are inserted into the site server database.  
  
 After the initial scan for software updates compliance, the scan is started at the configured scan schedule. However, if the client has scanned for software updates compliance in the time frame indicated by the Time to Live (TTL) value, the client uses the software updates metadata that is stored locally. When the last scan is outside the TTL, the client must connect to WSUS running on the software update point and update the software updates metadata stored on the client.  
  
 Including the scan schedule, the scan for software updates compliance can start in the following ways:  
  
-   **Software updates scan schedule**: The scan for software updates compliance starts at the configured scan schedule that is configured in the Software Updates Client Agent settings. For more information about how to configure the Software Updates client settings, see the [Software Updates](../System Center Configuration Manager/About-client-settings-in-System-Center-Configuration-Manager.md#BKMK_SoftwareUpdatesDeviceSetting) section in the [About client settings in System Center Configuration Manager](../System Center Configuration Manager/About-client-settings-in-System-Center-Configuration-Manager.md) topic.  
  
-   **Configuration Manager Properties action**: The user can start the **Software Updates Scan Cycle** or **Software Updates Deployment Evaluation Cycle** action on the **Action** tab in the **Configuration Manager Properties** dialog box on the client computer.  
  
-   **Deployment reevaluation schedule**: The deployment evaluation and scan for software updates compliance starts at the configured deployment reevaluation schedule, which is configured in the Software Updates Client Agent settings. For more information about the Software Updates client settings, see the  [Software Updates](../System Center Configuration Manager/About-client-settings-in-System-Center-Configuration-Manager.md#BKMK_SoftwareUpdatesDeviceSetting) section in the [About client settings in System Center Configuration Manager](../System Center Configuration Manager/About-client-settings-in-System-Center-Configuration-Manager.md) topic.  
  
-   **Prior to downloading update files**: When a client computer receives an assignment policy for a new required deployment, the Software Updates Client Agent downloads the software update files to the local client cache. Before downloading the software update files, the client agent starts a scan to verify that the software update is still required.  
  
-   **Prior to software update installation**: Just before the software update installation, the Software Updates Client Agent starts a scan to verify that the software updates are still required.  
  
-   **After software update installation**: Just after a software update installation is complete, the Software Updates Client Agent starts a scan to verify that the software updates are no longer required and creates a new state message that states that the software update is installed. When the installation has finished, but a restart is necessary, the state message indicates that the client computer is pending a restart.  
  
-   **After system restart**: When a client computer is pending a system restart for the software update installation to finish, the Software Updates Client Agent starts a scan after the restart to verify that the software update is no longer required and creates a state message that states that  the software update is installed.  
  
#### Time to live value  
 The software updates metadata that is required for the scan for software updates compliance is stored on the local client computer, and by default, is relevant for up to 24 hours. This value is known as the Time to Live (TTL).  
  
#### Scan for software updates compliance types  
 The client scans for software updates compliance by using an online or offline scan and a forced or non-forced scan, depending on the way the scan for software updates compliance is started. The following describes which methods for starting the scan are online or offline and whether the scan is forced or non-forced.  
  
-   **Software updates scan schedule** (non-forced online scan)  
  
     At the configured scan schedule, the client connects to WSUS running on the software update point to retrieve the software updates metadata only when the last scan was outside the TTL.  
  
-   **Software Updates Scan Cycle** or **Software Updates Deployment Evaluation Cycle** (forced online scan)  
  
     The client computer always connects to WSUS running on the software update point to retrieve the software updates metadata before the client computer scans for software updates compliance. After the scan is complete, the TTL counter is reset. For example, if the TTL is 24 hours, after a user starts a scan for software updates compliance, the TTL is reset to 24 hours.  
  
-   **Deployment reevaluation schedule** (non-forced online scan)  
  
     At the configured deployment reevaluation schedule, the client connects to WSUS running on the software update point to retrieve the software updates metadata only when the last scan was outside the TTL.  
  
-   **Prior to downloading update files** (non-forced online scan)  
  
     Before the client can download update files in required deployments, the client connects to WSUS running on the software update point to retrieve the software updates metadata only when the last scan was outside the TTL.  
  
-   **Prior to software update installation** (non-forced online scan)  
  
     Before the client installs software updates in required deployments, the client connects to WSUS running on the software update point to retrieve the software updates metadata only when the last scan was outside the TTL.  
  
-   **After software update installation** (forced offline scan)  
  
     After a software update is installed, the Software Updates Client Agent starts a scan by using the local metadata. The client never connects to WSUS running on the software update point to retrieve software updates metadata.  
  
-   **After system restart** (forced offline scan)  
  
     After a software update is installed and the computer is restarted, the Software Updates Client Agent starts a scan by using the local metadata. The client never connects to WSUS running on the software update point to retrieve software updates metadata.  
  
##  <a name="BKMK_DeploymentPackages"></a> Software update deployment packages  
 A software update deployment package is the vehicle used to download software updates to a network shared folder, and copy the software update source files to the content library on site servers and on distribution points that are defined in the deployment. By using the Download Updates Wizard, you can download software updates and add them to deployment packages before you deploy them. This wizard lets you provision software updates on distribution points and verify that this part of the deployment process is successful before you deploy the software updates to clients.  
  
 When you deploy downloaded software updates by using the Deploy Software Updates Wizard, the deployment automatically uses the deployment package that contains the software updates. When software updates that have not been downloaded are deployed, you must specify a new or existing deployment package in the Deploy Software Updates Wizard, and the software updates are downloaded when the wizard is finished.  
  
> [!IMPORTANT]  
>  You must manually create the shared network folder for the deployment package source files before you specify it in the wizard. Each deployment package must use a different shared network folder.  
  
> [!IMPORTANT]  
>  The SMS Provider computer account and the administrative user who actually downloads the software updates both require **Write** permissions to the package source. Restrict access to the package source to reduce the risk of an attacker tampering with the software updates source files in the package source.  
  
 When a new deployment package is created, the content version is set to 1 before any software updates are downloaded. When the software update files are downloaded by using the package, the content version is incremented to 2. Therefore, all new deployment packages start with a content version of 2. Every time that the content changes in a deployment package, the content version is incremented by 1. For more information about content management in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], see [Fundamental concepts for content management in System Center Configuration Manager](../System Center Configuration Manager/Fundamental-concepts-for-content-management-in-System-Center-Configuration-Manager.md).  
  
 Clients install software updates in a deployment by using any distribution point that has the software updates available, regardless of the deployment package. Even if a deployment package is deleted for an active deployment, clients still can install the software updates in the deployment as long as each update was downloaded to at least one other deployment package and is available on a distribution point that can be accessed from the client. When the last deployment package that contains a software update is deleted, client computers cannot retrieve the software update until the update is downloaded again to a deployment package. Software updates appear with a red arrow in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console when the update files are not in any deployment packages. Deployments appear with a double red arrow if they contain any updates in this condition.  
  
##  <a name="BKMK_DeploymentWorkflows"></a> Software update deployment workflows  
 There are two main scenarios for deploying software updates in your environment, manual deployment and automatic deployment. Typically, you deploy software updates manually to create a baseline for client computers, and then you manage software updates on clients by using automatic deployment. The following sections provide a summary for the workflow for manual and automatic deployment for software updates.  
  
###  <a name="BKMK_ManualDeployment"></a> Manual deployment of software updates  
 Manual deployment of software updates is the process of selecting software updates in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console and manually starting the deployment process. You typically use this method of deployment to get the client computers up-to-date with required software updates before you create automatic deployment rules that manage ongoing monthly software update deployments, and to deploy out of band software update requirements. The following list provides the general workflow for manual deployment of software updates:  
  
1.  Filter for software updates that use specific requirements. For example, you could provide criteria that retrieves all security or critical software updates that are required on more than 50 client computers.  
  
2.  Create a software update group that contains the software updates.  
  
3.  Download the content for the software updates in the software update group.  
  
4.  Manually deploy the software update group.  
  
###  <a name="BKMK_AutomaticDeployment"></a> Automatic deployment of software updates  
 Automatic software updates deployment is configured by using an automatic deployment rule (ADR). You typically use this method of deployment for your monthly software updates (generally known as Patch Tuesday) and for managing definition updates. When the rule runs, software updates are removed from the software update group (if using an existing group), the software updates that meet a specified criteria (for example, all security software updates released in the last week) are added to a software update group, the content files for the software updates are downloaded and copied to distribution points, and the software updates are deployed to client computers in the target collection. The following list provides the general workflow for automatic deployment of software updates:  
  
1.  Create an ADR that specifies deployment settings such as the following:  
  
    -   Target collection  
  
    -   Decide whether to enable the deployment or report on software updates compliance for the client computers in the target collection  
  
    -   Software updates criteria  
  
    -   Evaluation and deployment schedules  
  
    -   User experience  
  
    -   Download properties  
  
2.  The software updates are added to a software update group.  
  
3.  The software update group is deployed to the client computers in the target collection, if it is specified.  
  
 You must determine what deployment strategy to use in your environment. For example, you might create the ADR and target a collection of test clients. After you verify that the software updates are installed on the test group, you can add a new deployment to the rule or change the collection in the existing deployment  to a target collection that includes a larger set of clients. The software update objects that are created by the ADRs are interactive.  
  
-   Software updates that were deployed by using an ADR are automatically deployed to new clients added to the target collection.  
  
-   New software updates added to a software update group are automatically deployed to the clients in the target collection.  
  
-   You can enable or disable deployments at any time for the ADR.  
  
 After you create an ADR, you can add additional deployments to the rule. This can help you manage the complexity of deploying different updates to different collections. Each new deployment has the full range of functionality and deployment monitoring experience, and each new deployment that you add:  
  
-   Uses the same update group and package which is created when the ADR first runs  
  
-   Can specify a different collection  
  
-   Supports unique deployment properties including:  
  
    -   Activation time  
  
    -   Deadline  
  
    -   Show or hide end user experience  
  
    -   Separate alerts for this deployment  
  
##  <a name="BKMK_DeploymentProcess"></a> Software update deployment process  
 After you deploy software updates or when an automatic deployment rule runs and deploys software updates, a deployment assignment policy is added to the machine policy for the site. The software updates are downloaded from the download location, the Internet, or network shared folder, to the package source. The software updates are copied from the package source to the content library on the site server, and then copied to the content library on the distribution point.  
  
 When a client computer in the target collection for the deployment receives the machine policy, the Software Update Client Agent starts an evaluation scan. The client agent downloads the content for required software updates from a distribution point to the local client cache soon after it receives the deployment, but waits until after the **Software available time** setting for the deployment before the software updates are available to install. The software updates in optional deployments (deployments that do not have an installation deadline) are not downloaded until a user manually starts the installation.  
  
 When the configured deadline passes, the Software Updates Client Agent performs a scan to verify that the software updates are still required. Then it checks the local cache on the client computer to verify that the software update source files are still available. Finally, the client installs the software updates. If the content was deleted from the client cache to make room for another deployment, the client re-downloads the software updates from the distribution point to the client cache. Software updates are always downloaded to the client cache regardless of the configured maximum client cache size. When the installation is complete, the client agent verifies that the software updates are no longer required, and then sends a state message to the management point to indicate that the software updates are now installed on the client.  
  
### Required system restart  
 By default, when software updates from a required deployment are installed on a client computer and a system restart is required for the installation to finish, the system restart is started. For software updates that were installed before the deadline, the automatic system restart is postponed until the deadline, unless the computer is restarted before that for some other reason. The system restart can be suppressed for servers and workstations. These settings are configured in the **User Experience** page of the Deploy Software Updates Wizard or Create Automatic Updates Rule Wizard.  
  
### Deployment reevaluation cycle  
 By default, client computers start a deployment reevaluation cycle every 7 days. During this evaluation cycle, the client computer scans for software updates that were previously deployed and installed. If any software updates are missing, the software updates are reinstalled from the local cache. If a software update is no longer available in the local cache, it is downloaded from a distribution point and then installed. You can configure the reevaluation schedule on the **Software Updates** page in client settings for the site.  
  
##  <a name="BKMK_EmbeddedDevices"></a> Support for Windows embedded devices that use write filters  
 When you deploy software updates to Windows Embedded devices that are write filter-enabled, you can specify whether to disable the write filter on the device during the deployment and then restart the device after the deployment. If the write filter is not disabled, the software is deployed to a temporary overlay and the software will no longer be installed when the device restarts unless another deployment forces changes to be persisted.  
  
> [!NOTE]  
>  When you deploy a software update to a Windows Embedded device, make sure that the device is a member of a collection that has a configured maintenance window. This lets you manage when the write filter is disabled and enabled, and when the device restarts.  
  
 The user experience setting that controls the write filter behavior is a check box named **Commit changes at deadline or during a maintenance windows (requires restarts)**.  
  
 For more information about how [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] manages embedded devices that use write filters, see  [Planning for client deployment to Windows Embedded devices in System Center Configuration Manager](../System Center Configuration Manager/Planning-for-client-deployment-to-Windows-Embedded-devices-in-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_ExtendSoftwareUpdates"></a> Extend software updates in Configuration Manager  
 Use System Center Updates Publisher to manage software updates that are not available from Microsoft Update. After you publish the software updates to the update server and synchronize the software updates in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], you can deploy the software updates to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients. For more information about Updates Publisher, see [Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkId=252947).  




## See Also  
 [Deploy and manage software updates in System Center Configuration Manager](../System Center Configuration Manager/Deploy-and-manage-software-updates-in-System-Center-Configuration-Manager.md)