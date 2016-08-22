---
title: "Use the Hotfix Installer to install updates for System Center Configuration Manager"
ms.custom: na
ms.date: 2016-03-11
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: f3058277-c597-4dac-86d1-41b6f7e62b36
caps.latest.revision: 9
---
# Use the Hotfix Installer to install updates for System Center Configuration Manager
Some updates for [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] are not available from the Microsoft cloud service and are only obtained out-of-band. An example is a limited release hotfix to address a specific issue.   
When you must install an update (or hotfix) that you receive from Microsoft, and that update has a file name that ends with the extension **.exe** (not **update.exe**), you use the hotfix installer that is included with that hotfix download to install the update directly to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site server.  
  
 If the hotfix file has the **.update.exe** file extension, see [Use the Update Registration Tool to import hotfixes to System Center Configuration Manager](../System Center Configuration Manager/Use-the-Update-Registration-Tool-to-import-hotfixes-to-System-Center-Configuration-Manager.md).  
  
> [!NOTE]  
>  This topic provides general guidance about how to install hotfixes that update [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]. For details about a specific update, refer to its corresponding Knowledge Base (KB) article at Microsoft Support.  
  
##  <a name="bkmk_Overview"></a> Overview of hotfixes for Configuration Manager  
 Hotfixes for  [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] are similar to those for other Microsoft products, such as SQL Server, contain either one individual fix or a bundle (a rollup of fixes), and are described in a Microsoft Knowledge Base article.  
  
 Individual updates include a single focused update for a specific version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
Update bundles include multiple updates for a specific version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
When an update is a bundle, you cannot install individual updates from that bundle.  
  
 If you plan to create deployments to install updates on additional computers, you must install the update bundle on a central administration site server or primary site server.  
  
 The following happens when you run the update bundle:  
  
-   It extracts the update files for each applicable component from the update bundle.  
  
-   Starts a wizard that guides you through a process to configure the updates and deployment options for the updates.  
  
-   After you complete the wizard, the updates in the bundle that apply to the site server are installed on the site server.  
  
 The wizard also creates deployments that you can use to install the updates on additional computers. You deploy the updates to additional computers by using a supported deployment method, such as a software deployment package or Microsoft System Center Updates Publisher 2011.  
  
 When the wizard runs, it creates a **.cab** file on the site server for use with Updates Publisher 2011. Optionally, you can configure the wizard to also create one or more packages for software deployment. You can use these deployments to install updates on components, such as clients or the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. You can also install updates manually on computers that do not run the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client.  
  
 The following three groups in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] can be updated:  
  
-   [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] server roles, which include:  
  
    -   Central administration site  
  
    -   Primary site  
  
    -   Secondary site  
  
    -   Remote SMS Provider  
  
-   [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console  
  
-   [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client  
  
> [!NOTE]  
>  **Updates for site system roles** (including updates for the site database and cloud-based distribution points) are installed as part of the update for site servers and services by the site component manager.  
>   
>  However, updates pull-distribution points are serviced by distribution manager instead of the site component manager.  
  
 Each update bundle for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] is a self-extractable .exe file (SFX) that contains the files that are necessary to install the update on the applicable components of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. Typically, the SFX file can contain the following files:  
  
|File|Details|  
|----------|-------------|  
|<Product version\>-QFE-KB<KB article ID\>-<platform\>-<language\>.exe|This is the update file. The command line for this file is managed by Updatesetup.exe.<br /><br /> For example:<br />CM1511RTM-QFE-KB123456-X64-ENU.exe|  
|Updatesetup.exe|This .msi wrapper manages the installation of the update bundle.<br /><br /> When you run the update, Updatesetup.exe detects the display language of the computer where it runs. By default, the user interface for the update is in English. However, when the display language is supported, the user interface displays in the computer's local language.|  
|License_<language\>.rtf|When applicable, each update contains one or more license files for supported languages.|  
|<Product&updatetype>-<product version\>-<KB article ID\>-<platform\>.msp|When the update applies to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console or clients, the update bundle includes separate Windows Installer patch (.msp) files.<br /><br /> For example:<br /><br /> **Configuration Manager console update:** ConfigMgr1511-AdminUI-KB1234567-i386.msp<br /><br /> **Client update:** ConfigMgr1511-client-KB1234567-i386.msp<br />ConfigMgr1511-client-KB1234567-x64.msp|  
  
 By default, the update bundle logs its actions to a .log file on the site server. The log file has the same name as the update bundle and is written to the **%SystemRoot%/Temp** folder.  
  
 When you run the update bundle, it extracts a file with the same name as the update bundle to a temporary folder on the computer, and then runs Updatesetup.exe. Updatesetup.exe starts the Software Update for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] <product version\> <KB Number\> Wizard.  
  
 As applicable to the scope of the update, the wizard creates a series of folders under the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] installation folder on the site server. The folder structure resembles the following:   
 **\\\\<Server Name\>\SMS_<Site Code\>\Hotfix\\<KB Number\>\\<Update Type\>\\<Platform\>**.  
  
 The following table provides details about the folders in the folder structure:  
  
|Folder name|More information|  
|-----------------|----------------------|  
|<Server name\>|This is the name of the site server where you run the update bundle.|  
|SMS_<Site Code\>|This is the share name of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] installation folder.|  
|<KB Number\>|This is the ID number of the Knowledge Base article for this update bundle.|  
|<Update type\>|These are the types of updates for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. The wizard creates a separate folder for each type of update that is contained in the update bundle. The folder names represent the update types. They include the following:<br /><br /> **Server**: Includes updates to site servers, site database servers, and computers that run the SMS Provider.<br /><br /> **Client**: Includes updates to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client.<br /><br /> **AdminConsole**: Includes updates to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console<br /><br /> In addition to the preceding update types, the wizard creates a folder named **SCUP**. This folder does not represent an update type, but instead contains the .cab file for Updates Publisher.|  
|<Platform\>|This is a platform-specific folder. It contains update files that are specific to a type of processor.  These folders include:<br /><br /> x64<br /><br /> I386|  
  
##  <a name="bkmk_Install"></a> How to install updates  
 To install updates, you must first install the update bundle on a site server. When you install an update bundle, it starts an install wizard for that update. This wizard does the following:  
  
-   Extracts the update files  
  
-   Helps you to configure deployments  
  
-   Installs applicable updates on the server components of the local computer  
  
 After you install the update bundle on a site server, you can then update additional components for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. The following table describes update actions for these various components:  
  
|Component|Instructions|  
|---------------|------------------|  
|Site server|Deploy updates to a remote site server when you do not choose to install the update bundle directly on that remote site server.|  
|Site database|For remote site servers, deploy server updates that include an update to the site database if you do not install the update bundle directly on that remote site server.|  
|[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console|After initial installation of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, you can install updates for the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console on each computer that runs the console. You cannot modify the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console installation files to apply the updates during the initial installation of the console.|  
|Remote SMS Provider|Install updates for each instance of the SMS Provider that runs on a computer other than the site server where you installed the update bundle.|  
|[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients|After initial installation of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client, you can install updates for the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client on each computer that runs the client.|  
  
> [!NOTE]  
>  You can deploy updates only to computers that run the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client.  
  
 If you reinstall a client, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, or SMS Provider, you must also reinstall the updates for these components.  
  
 Use the information in the following sections to install updates on the each of the components for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
###  <a name="bkmk_servers"></a> Update servers  
 Updates for servers can include updates for **sites**, the **site database**, and computers that run an instance of the **SMS Provider**:  
  
####  <a name="bkmk_site"></a> Update a site  
 To update a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site, you can install the update bundle directly on the site server, or you can deploy the updates to a site server after you install the update bundle on a different site.  
  
 When you install an update on a site server, the update installation process manages additional actions that are required to apply the update, such as updating site system roles. The exception to this is the site database. The following section contains information about how to update the site database.  
  
####  <a name="bkmk_database"></a> Update a site database  
 To update the site database, the installation process runs a file named **update.sql** on the site database. You can configure the update process to automatically update the site database, or you can manually update the site database later.  
  
 **Automatic Update of the Site Database**  
  
 When you install the update bundle on a site server, you can choose to automatically update the site database when the server update is installed. This decision applies only to the site server where you install the update bundle and does not apply to deployments that are created to install the updates on remote site servers.  
  
> [!NOTE]  
>  When you choose to automatically update the site database, the process updates a database regardless whether the database is located on the site server or on a remote computer.  
  
> [!IMPORTANT]  
>  Before you update the site database, create a backup of the site database. You cannot uninstall an update to the site database. For information about how to create a backup for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], see [Backup and recovery for System Center Configuration Manager](../System Center Configuration Manager/Backup-and-recovery-for-System-Center-Configuration-Manager.md).  
  
 **Manual Update of the Site Database**  
  
 If you choose not to automatically update the site database when you install the update bundle on the site server, the server update does not modify the database on the site server where the update bundle runs. However, deployments that use the package that is created for software deployment or that installs always update the site database.  
  
> [!WARNING]  
>  When the update includes updates to both the site server and the site database, the update is not functional until the update is completed for both the site server and site database. Until the update is applied to the site database, the site is in an unsupported state.  
  
 **To manually update a site database:**  
  
1.  On the site server stop the SMS_SITE_COMPONENT_MANAGER service, and then stop the SMS_EXECUTIVE service.  
  
2.  Close the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
3.  Run the update script named **update.sql** on that site's database. For information about how to run a script to update a SQL Server database, see the documentation for the version of SQL Server that you use for your site database server.  
  
4.  Restart services that were stopped in previous steps.  
  
5.  When the update bundle installs, it extracts **update.sql** to the following location on the site server:  **\\\\<Server Name\>\SMS_<Site Code\>\Hotfix\\<KB Number\>\update.sql**  
  
####  <a name="bkmk_provider"></a> Update a computer that runs the SMS Provider  
 After you install an update bundle that includes updates for the SMS Provider, you must deploy the update to each computer that runs the SMS Provider. The only exception to this is the instance of the SMS Provider that was previously installed on the site server where you install the update bundle. The local instance of the SMS Provider on the site server is updated when you install the update bundle.  
  
 If you remove and then reinstall the SMS Provider on a computer, you must then reinstall the update for the SMS Provider on that computer.  
  
###  <a name="BKMK_clients"></a> Update clients  
 When you install an update that includes updates for the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client, you are presented with the option to automatically upgrade clients with the update installation, or manually upgrade clients at a later time. For more information about automatic client upgrade, see [How to upgrade clients for Windows computers](https://technet.microsoft.com/library/mt627885.aspx).  
  
 You can deploy updates with Updates Publisher or a software deployment package, or you can choose to manually install the update on each client. For more information about how to use deployments to install updates, see the [Deploy updates for Configuration Manager](#BKMK_Deploy) section in this topic.  
  
> [!IMPORTANT]  
>  When you install updates for clients and the update bundle includes updates for servers, be sure to also install the server updates on the primary site to which the clients are assigned.  
  
 To manually install the client update, on each [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client, you must run **Msiexec.exe** and reference the platform-specific client update .msp file.  
  
 For example, you can use the following command line for a client update. This command line runs MSIEXEC on the client computer and references the .msp file that the update bundle extracted on the site server: **msiexec.exe /p \\\\<ServerName\>\SMS_<SiteCode\>\Hotfix\\<KB Number\>\Client\\<Platform\>\\<msp\> /L\*v <logfile\>REINSTALLMODE=mous REINSTALL=ALL**  
  
###  <a name="BKMK_console"></a> Update Configuration Manager consoles  
 To update a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, you must install the update on the computer that runs the console after the console installation is finished.  
  
> [!IMPORTANT]  
>  When you install updates for the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, and the update bundle includes updates for servers, be sure to also install the server updates on the site that you use with the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
 If the computer that you update runs the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client:  
  
-   You can use a deployment to install the update. For more information about how to use deployments to install updates, see the [Deploy updates for Configuration Manager](#BKMK_Deploy) section in this topic.  
  
-   If you are logged directly on to the client computer, you can run the installation interactively.  
  
-   You can manually install the update on each computer. To manually install the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console update, on each computer that runs the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, you can run Msiexec.exe and reference the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console update .msp file.  
  
 For example, you can use the following command line to update a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. This command line runs MSIEXEC on the computer and references the .msp file that the update bundle extracted on the site server: **msiexec.exe /p \\\\<ServerName\>\SMS_<SiteCode\>\Hotfix\\<KB Number\>\AdminConsole\\<Platform\>\\<msp\> /L\*v <logfile\>REINSTALLMODE=mous REINSTALL=ALL**  
  
##  <a name="BKMK_Deploy"></a> Deploy updates for Configuration Manager  
 After you install the update bundle on a site server, you can use one of the following three methods to  deploy updates to additional computers.  
  
###  <a name="BKMK_DeploySCUP"></a> Use Updates Publisher 2011 to install updates  
 When you install the update bundle on a site server, the installation Wizard creates a catalog file for Updates Publisher that you can use to deploy the updates to applicable computers. The wizard always creates this catalog, even when you select the option **Use package and program to deploy this update**.  
  
 The catalog for Updates Publisher is named **SCUPCatalog.cab** and can be found in the following location on the computer where the update bundle runs: **\\\\<ServerName\>\SMS_<SiteCode\>\Hotfix\\<KB Number\>\SCUP\SCUPCatalog.cab**  
  
> [!IMPORTANT]  
>  Because the SCUPCatalog.cab file is created by using paths that are specific to the site server where the update bundle is installed, it cannot be used on other site servers.  
  
 After the wizard is finished, you can import the catalog to Updates Publisher, and then use [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] software updates to deploy the updates. For information about Updates Publisher, see [Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkID=83449) in the TechNet library for System Center 2012.  
  
 Use the following procedure to import the SCUPCatalog.cab file to Updates Publisher and publish the updates.  
  
##### To import the updates to Updates Publisher 2011  
  
1.  Start the Updates Publisher console and click **Import**.  
  
2.  On the **Import Type** page of the Import Software Updates Catalog Wizard, select **Specify the path to the catalog to import**, and then specify the SCUPCatalog.cab file.  
  
3.  Click **Next**, and then click **Next** again.  
  
4.  In the **Security Warning - Catalog Validation** dialog box, click **Accept**. Close the wizard after it is finished.  
  
5.  In the Updates Publisher console, select the update that you want to deploy, and then click **Publish**.  
  
6.  On the **Publish Options** page of the Publish Software Updates Wizard, select **Full Content**, and then click **Next**.  
  
7.  Complete the wizard to publish the updates.  
  
###  <a name="BKMK_DeploySWDist"></a> Use software deployment to install updates  
 When you install the update bundle on the site server of a primary site or central administration site, you can configure the installation Wizard to create update packages for software deployment. You can then deploy each package to a collection of computers that you want to update.  
  
 To create a software deployment package, on the **Configure Software Update Deployment** page of the wizard, select the check box for each update package type that you want to update. The available types can include servers, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] consoles, and clients. A separate package is created for each type of update that you select.  
  
> [!NOTE]  
>  The package for servers contains updates for the following components:  
>   
>  -   Site server  
> -   SMS Provider  
> -   Site database  
  
 Next, on the **Configure Software Update Deployment Method** page of the wizard, select the option **I will use software distribution**. This selection directs the wizard to create the software deployment packages.  
  
 After the wizard is finished, you can view the packages that it creates in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console in the **Packages** node in the **Software Library** workspace. You can then use your standard process to deploy software packages to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients. When a package runs on a client, it installs the updates to the applicable components of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] on the client computer.  
  
 For information about how to deploy packages to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients, see [Packages and programs in System Center Configuration Manager](../System Center Configuration Manager/Packages-and-programs-in-System-Center-Configuration-Manager.md).  
  
###  <a name="BKMK_DeployCollections"></a> Create collections for deploying updates to Configuration Manager  
 You can deploy specific updates to applicable clients. The following information can help you to create device collections for the different components for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
|Component of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]|Instructions|  
|----------------------------------------|------------------|  
|Central administration site server|Create a direct membership query and add the central administration site server computer.|  
|All primary site servers|Create a direct membership query and add each primary site server computer.|  
|All secondary site servers|Create a direct membership query and add each secondary site server computer.|  
|All x86 clients|Create a collection with the following query criteria:<br /><br /> **Select \* from SMS_R_System inner join SMS_G_System_SYSTEM on SMS_G_System_SYSTEM.ResourceID = SMS_R_System.ResourceId where SMS_G_System_SYSTEM.SystemType = "X86-based PC"**|  
|All x64 clients|Create a collection with the following query criteria:<br /><br /> **Select \* from SMS_R_System inner join SMS_G_System_SYSTEM on SMS_G_System_SYSTEM.ResourceID = SMS_R_System.ResourceId where SMS_G_System_SYSTEM.SystemType = "X64-based PC"**|  
|All computers that run the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console|Create a direct membership query and add each computer.|  
|Remote computers that run an instance of the SMS Provider|Create a direct membership query and add each computer.|  
  
> [!NOTE]  
>  To update a site database, deploy the update to the site server for that site.  
  
 For information about how to create collections, see [How to create collections in System Center Configuration Manager](../System Center Configuration Manager/How-to-create-collections-in-System-Center-Configuration-Manager.md).  
  
## See Also  
 [Use the Update Registration Tool to import hotfixes to System Center Configuration Manager](../System Center Configuration Manager/Use-the-Update-Registration-Tool-to-import-hotfixes-to-System-Center-Configuration-Manager.md)   
 [Updates for System Center Configuration Manager](../System Center Configuration Manager/Updates-for-System-Center-Configuration-Manager.md)