---
title: "tp mock up"
ms.custom: na
ms.date: 08/22/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: de8bee42-e1c7-49af-a3b6-f756b6fba4f7
caps.latest.revision: 8
---
# tp mock up
Welcome to the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] Technical Preview. With the release of [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], version 1511, this topic provides details about the evolving preview release that includes new functionality and capabilities we are working on, and that are not yet included in current branch of [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)].  
  
 Because this is a technical preview, details and functionality are subject to change:  
  
-   This topic will include information about  new capabilities that are available in subsequent Technical Previews and that are not yet included in the full product release  
  
-   Information about  new capabilities will be grouped in this topic by the Technical Preview version in which the capability first appears, like 1512 for December of 2015  
  
-   When features or capabilities are moved from the Technical Preview into the current branch of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], this content will update to indicate the update version that introduces  that functionality  
  
 For information about what's new in the current branch of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], see [What's new in System Center Configuration Manager](../Topic/What's%20new%20in%20System%20Center%20Configuration%20Manager.md).  
  
> [!NOTE]  
>  For information about what's in System Center Configuration Manager Technical Preview 4 (and earlier previews), see [Technical Previews for the pre-release of System Center Configuration Manager](https://technet.microsoft.com/library/dn965439.aspx)  
  
 **In this topic:**  
  
-   [Requirements and limitations for the Technical Preview](#bkmk_reqs)  
  
-   [Providing feedback](#BKMK_TPFeedback)  
  
-   [Capabilities delivered in technical previews](#bkmk_tpCaps)  
  
##  <a name="bkmk_reqs"></a> Requirements and limitations for the Technical Preview  
 The Technical Preview is intended for use in a lab environment. Because it is a limited build intended for use in a lab environment, it does not include options for support and should not be used in a production environment.  
  
 For most product prerequisites, use the information in the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)][Supported configurations for System Center Configuration Manager](../System Center Configuration Manager/Supported-configurations-for-System-Center-Configuration-Manager.md).  
  
 The following exceptions apply to the Technical Preview releases:  
  
-   Each install remains active for 60 days before it becomes inactive.  
  
-   English is the only language supported.  
  
-   Only a stand-alone primary site is supported. There is no support for a central administration site, multiple primary sites, or secondary sites.  
  
-   Only the following versions of SQL Server are supported:  
  
    -   SQL Server 2012 with cumulative update 2 or later  
  
    -   SQL Server 2014  
  
-   The site supports up to 10 clients, which must run one of the following:  
  
    -   Windows 7  
  
    -   Windows 8  
  
    -   Windows 8.1  
  
    -   Windows 10  
  
-   There is no support for upgrade to this preview build.  
  
-   There is no support for upgrade to a later build from this preview build.  
  
-   Only the following install flags (switches) are supported:  
  
    -   **/silent**  
  
    -   **/testdbupgrade**  
  
-   There is no support for migration to or from this preview build.  
  
-   When applicable, additional limitations or requirements are included with details for each specific version of the Technical Preview  
  
##  <a name="BKMK_TPFeedback"></a> Providing feedback  
 We would love to hear your feedback about our technical previews. To submit feedback about the capabilities in each preview, follow the link to our feedback form on the [Configuration Manager feedback program](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) page on the Microsoft Connect site.  
  
 And, if you have ideas about new features you would like to see, we want to know that as well. To submit new ideas and to vote on the ideas submitted by others, [visit our user voice page](http://configurationmanager.uservoice.com).  
  
##  <a name="bkmk_tpCaps"></a> Capabilities delivered in technical previews  
 The following table lists the  capabilities delivered in each [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]technical preview release. Click the name of the capability to learn more about it.  
  
> [!NOTE]  
>  Technical Preview 1511 is also known as Technical Preview 4. It represents a baseline for Technical Previews that begin with the release of the current branch for [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], version 1511.  
  
|Capability|1511|1512|  
|----------------|----------|----------|  
|[Integration with Windows Update for Business in Windows 10](#BKMK_WUfB)|Yes|Yes|  
|[Managing Office 365 ProPlus Client Update through System Center Configuration Manager](#BKMK_Office365ProPlus)|Yes|Yes|  
|[Support for SQL Server AlwaysOn for highly available databases](#BKMK_AlwasyOn)|Yes|Yes|  
|[Service a server cluster](#BKMK_ClusterServerUpdates)|Yes|Yes|  
|[Device Health Attestation](#bkmk_devicehealth)||Yes|  
  
##  <a name="BKMK_WUfB"></a> Integration with Windows Update for Business in Windows 10  
 First introduced in: 1511  
  
 System Center [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Technical Preview 4 now has the ability to differentiate a Windows 10 computer that is directly connected via Windows Update for Business (WUfB) versus the ones connected to WSUS for getting Windows 10 updates and upgrades.  For computers connected via WUfB, the updates and upgrades can be managed at the cadence set by an administrative user via Group Policies or MDM policies and these updates/upgrades can be installed directly from WUfB.    
For computers connected via WUfB, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] will not be able to report on compliance status (including Windows Updates or Definition Updates). Also [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] will not be able to deploy Microsoft Updates or 3rd party updates to these computers.  
  
 **Prerequisites for this scenario:**  
  
-   System Center [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Technical Preview 4.  
  
-   Windows 10 Desktop Pro or Windows 10 Enterprise Edition version 1511 or later  
  
-   Computers to be managed via [Windows Update for Business](https://technet.microsoft.com/library/mt622730\(v=vs.85\).aspx).  
  
### Try it out!  
 Try to complete the following task and then use the feedback information near the top of this topic to let us know how it worked:  
  
1.  Disable the Windows Update Agent so it doesn't scan against WSUS,  if it was previously enabled.   
    The registry key **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU\useWSUSServer** can be set to indicate whether the computer is scanning against WSUS or Windows Update.  When the value is  2, it’s not scanning against WSUS.  
  
2.  Take note of  the new attribute **UseWUServer**, under the **Windows Update** node in Configuration Manager Resource Explorer.  
  
3.  Create a collection based on the **UseWUServer** attribute for all the computers that are connected via WUfB for updates and upgrades.  
  
4.  Create a  client agent setting to disable the software update workflow and deploy the setting to the collection of computers that are connected directly to WUfB.  
  
5.  The computers that are managed via WUfB will display **Unknown** in the compliance status and won’t be counted as part of the overall compliance percentage.  
  
##  <a name="BKMK_Office365ProPlus"></a> Managing Office 365 ProPlus Client Update through System Center Configuration Manager  
 First introduced in: 1511  
  
 System Center [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Technical Preview 4 now has the ability to manage Office 365 desktop client updates using the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Software Update Management workflow.    
When Microsoft publishes a new Office 365 desktop client update to Windows Server Updates Services (WSUS), [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] will be able to synchronize the update to its catalog if the Office 365 update is configured to be part of the catalog synchronization.  The [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site server will download the Office 365 client updates and distribute the package to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] distribution points.  The [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client will then inform Office 365 desktop clients where to get the updates and when to start the update installation process.  
  
 **Prerequisites for this scenario:**  
  
-   System Center [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Technical Preview 4  
  
-   Windows 7 Service Pack 1  
  
-   Office 365 ProPlus (Build 16.0.6228.1000)  
  
### Try it out!  
 Try to complete the following task and then use the feedback information near the top of this topic to let us know how it worked:  
  
1.  You can synchronize Office 365 updates to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site server and view them from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
2.  You can approve and successfully deploy Office 365 updates.  
  
3.  You can download and successfully Office 365 updates to clients.  
  
4.  You can verify compliance for Office 365 updates by using in-console monitoring or reports.  
  
### To install Office 365 ProPlus  
 There are several ways to enable your Office 365 desktop client to be managed by the software update workflow in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  The following provides you with instructions on how to install Office 365 ProPlus and with the capability for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to manage the client updates using the update engine.  
  
1.  **Download the Office 2016 Deployment Tool**  
  
     Download the latest version of the [Office 2016 Deployment Tool](http://aka.ms/ODT2016) from the Microsoft Download Center  
  
2.  **Extract the Office Deployment Tool**  
  
     Extract the Office Deployment Tool to a local folder. There are two files:  setup.exe and configuration.xml.  
  
3.  **Create an XML file**  
  
     In the same folder, create an XML file or modify the sample configuration.xml file with the bellow parameters:  
  
    ```  
    <Configuration>   
        <Add OfficeClientEdition="32" Branch=”FirstReleaseCurrent” OfficeMgmtCOM=“True”>   
            <Product ID="O365ProPlusRetail">   
        <Language ID="en-us" />   
            </Product>   
        </Add>   
    </Configuration>  
  
    ```  
  
     This sample XML file will install a 32-bit version of Office 365 ProPlus in English on your target desktop.  You will need to ensure that you have the Branch pointing to the First Release for Current Branch (FirstReleaseCurrent) and OfficeMgmtCOM set to True.  These settings will ensure that you get the latest Office 365 Client build that supports the ability for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to manage Office updates.  For more information about the tool, see  [Office Deployment Tool](http://aka.ms/ODT).  
  
4.  **Install Office 365 ProPlus**  
  
     From the command line, switch to the folder where you extracted the  Office Deployment Tool, and then type **setup.exe /configure configuration.xml**. If you used a different name for the XML file, use that name in the command line.  
  
##  <a name="BKMK_AlwasyOn"></a> Support for SQL Server AlwaysOn for highly available databases  
 First introduced in: 1511  
  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] now supports using a SQL Server AlwaysOn availability groups to host the site database.  When you install a new site, you can direct setup to use the availability group instead of a normal instance of SQL Server.  
  
> [!NOTE]  
>  Successful configuration and use of availability groups requires you to be comfortable with configuring SQL Server availability groups, and relies on documentation and procedures provided in the SQL Server documentation library.  
  
 The high level process to configure and use availability groups includes:  
  
1.  Configure the availability group in SQL Server.  
  
2.  Install a new [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site and during Setup direct the site to use the availability group by specifying the groups Endpoint.  
  
 **Prerequisites for this scenario:**  
  
-   Requires a version of SQL Server supported by the Configuration Manager Technical Preview  
  
-   You must create and configure the SQL Server Availability Group before installing [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]  
  
-   The availability group must have one primary replica, and can have up to two synchronous secondary replicas  
  
-   The availability group must have at least one Endpoint  
  
-   You must have a network location that each SQL Server in the Availability Group can access. This location is used by Setup when configuring the Availability Group, and can be removed after Setup completes.  
  
 **Known issues for this release:**  
  
-   You cannot successfully add a new replica member to an Availability Group that is already in use as a site database. Instead, you must reinstall the site after the new replica member is added.  
  
-   For this scenario  you might need to install the **SQL Server 2012 native client** ([from the SQL Server 2012 Feature Pack](http://www.microsoft.com/download/details.aspx?id=29065)) on the management point server. This prevents SQL connection errors (which are logged in the **mp_getauth.log** on the management point server).  
  
### Try it out!  
 Try to complete the following tasks and then use the feedback information near the top of this topic to let us know how they worked:  
  
-   I can install a primary site that uses a database server configured for SQL AlwaysOn Availability Groups  
  
-   I was able to failover my SQL AlwaysOn Availability Group to a new replica in the group and the primary site is still operational  
  
### Configuring SQL Server AlwaysOn for Configuration Manager  
 First introduced in: 1511  
  
 Use the following procedures to first create and configure the availability group, and then install a new [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site that uses the availability group.  
  
#### To create a SQL Server AlwaysOn availability group  
 The process to [create a SQL Server availability group](https://technet.microsoft.com/library/ff878265\(v=sql.120\).aspx) is documented in the SQL Server documentation library.  When you create the availability group, ensure the following requirements for use with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] are met:  
  
-   A maximum of three members:  
  
    -   One primary replica and up to two secondary replicas  
  
    -   Secondary replicas must be synchronous.  
  
        > [!TIP]  
        >  We recommend that secondary replicas be configured to be read only. This enables you to use a secondary replica for functions like reporting while maintaining the performance of the primary replica for site operations.  
  
-   At least one endpoint. The virtual name of this endpoint will be used when you install the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site.  
  
    > [!TIP]  
    >  Although the group can contain multiple Endpoints, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] can only make use of one.  
  
#### To install a Configuration Manager site that uses the availability group  
 To install a site that uses a SQL Server availability group:  
  
1.  Substitute the following when prompted by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Setup:  
  
    -   **SQL Server name**: Enter the virtual name for the Endpoint that you configured when creating the availability group. The virtual name should be a full DNS name, like **<endpointServer\>.fabrikam.com**.  
  
    -   **Instance**:  This value should remain blank. There is no instance in this configuration.  
  
    -   **Database**: Enter the name of the database you created on the primary replica of the availability group.  
  
2.  Next, you must provide a network location that each SQL Server in the group can access:  
  
    -   The computer account and service account from each SQL Server require full control access to this location.  
  
    -   This location is only used during setup, and can be unshared or deleted after Setup completes and the site is installed.  
  
3.  After you provide this information, complete setup with your normal process and configurations.  
  
##  <a name="BKMK_ClusterServerUpdates"></a> Service a  server cluster  
 First introduced in: 1511  
  
 You can now create a collection that contains servers in a cluster,  and then configure the cluster settings to use when you deploy updates to the cluster. You can control the percentage of servers that are online at any given time, as well as to configure pre-deployment and post-deployment PowerShell scripts to run custom actions.  
  
 **Known issues for this release:**  
  
-   Reporting is not available to check the status of software updates deployment for cluster servers.  
  
-   The maintenance sequence option on the **Cluster Settings** page is disabled and not available in this release.  
  
### Try it out!  
 Try to complete the following task and then use the feedback information near the top of this topic to let us know how it worked:  
  
-   I can create a collection that represents a cluster of servers. For this test, you can configure your collect membership rules to have 2 machines in this collection.  
  
-   I can specify that only 50% of servers in the cluster can be offline at any point in cluster servicing. Use the sample scripts in the procedure to specify the pre-deployment and post-deployment scripts.  
  
-   Deploy an update to this collection. Review the start.txt and end.txt files in C:\temp and verify start and end times for the deployment on the servers in the cluster. Review the UpdatesDeployment.log file for more information.  
  
#### To create a collection for a server cluster  
  
1.  [Create a device collection](https://technet.microsoft.com/library/gg712295.aspx) that contains the servers in the cluster.  
  
2.  In the **Assets and Compliance** workspace, click **Device Collections**, right-click the collection that contains the servers in the cluster, and then click **Properties**.  
  
3.  On the **General** tab, select **All devices are part of the same server cluster**, and then click **Settings**.  
  
4.  On the **Cluster Settings** page, select the percentage of servers that can be taken offline at the same time  to have software updates installed. One cluster server might be taken offline at a time regardless of the percentage that you provide. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] will round down when selecting how many servers to service at one time. For example, if you choose 51% and there are 4 servers in the cluster, 2 servers will be taken offline at the same time.  
  
5.  Specify whether to use a pre-deployment (node drain) script or post-deployment (node resume) script.  
  
    > [!TIP]  
    >  The following are examples that you can use in testing for pre-deployment and post-deployment scripts that write the current time to a text file:  
    >   
    >  **Pre-deployment**  
    >   
    >  `#Start`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\start.txt`  
    >   
    >  **Post-deployment**  
    >   
    >  `#End`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\end.txt`  
  
#### To deploy software updates to the server cluster  
  
1.  [Deploy software updates](https://technet.microsoft.com/library/gg712304.aspx) to the server cluster collection.  
  
2.  [Monitor the software update deployment](https://technet.microsoft.com/library/gg712304.aspx).  
  
##  <a name="bkmk_devicehealth"></a> Device Health Attestation  
 First introduced in: 1512  
  
## See Also  
 [What's new in System Center Configuration Manager](../Topic/What's%20new%20in%20System%20Center%20Configuration%20Manager.md)   
 [Introduction to System Center Configuration Manager](../System Center Configuration Manager/Introduction-to-System-Center-Configuration-Manager.md)