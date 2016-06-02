---
title: Master Data Services
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: f6cd850f-b01b-491f-972c-f966b9fe4190
---
# Master Data Services
  [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] \(MDS\) is enables your organization to manage a trusted version of data. This article covers how to install [!INCLUDE[ssMDSshort_md](../../Token\Other/ssMDSshort_md.md)], set up the MDS database and website, and deploy the sample models and data.  
   
For an overview of how you organize data in [!INCLUDE[ssMDSshort_md](../../Token\Other/ssMDSshort_md.md)], see [enter link description here](Master%20Data%20Services%20Overview%20\(MDS\).md).     
  
 For information about the new features in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], see [What's New in Master Data Services &#40;MDS&#41;](../Topic/What's%20New%20in%20Master%20Data%20Services%20\(MDS\).md).  
  
> **Download**  
>-   To download [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)], go to  **[Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**.  
>-   Have an Azure account?  Then go **[Here](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rc3evaluationwindowsserver2012r2/?wt.mc_id=sqL16_vm)** to spin up a Virtual Machine with [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] RC3 already installed.  
  
  
## Installing Master Data Services, and IIS Roles and Features  
 You use the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup installation wizard or a command prompt to install [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)].  
  
 **To install [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup.**  
  
1.  Double\-click Setup.exe, and follow the steps in the installation wizard.  
  
2.  Select [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] on the **Feature Selection** page under **Shared Features**.  
  
     This installs [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)], assemblies, a Windows PowerShell snap\-in, and folders and files for Web applications and services.  
  
     ![mds_SQLServer2016Setup_FeatureSelection](../../Images\Image\ImageNotContaina/mds_SQLServer2016Setup_FeatureSelection.png "mds_SQLServer2016Setup_FeatureSelection")  
  
3.  Complete the installation wizard.  
  
4.  In [!INCLUDE[winblue_server_2](../../Token\Other/winblue_server_2_md.md)], click the **Server Manager** icon on the taskbar on the **Desktop**.  
  
     ![Icon for the Server Manager in Windows Server 2012 taskbar](../../Images\Image\ImageNotContaina/mds_WindowsServerTaskbar_ServerManagerIcon.png "mds_WindowsServerTaskbar_ServerManagerIcon")  
  
5.  In **Server Manager**, click, **Add Roles and Features** on the **Manage** menu.  
  
     ![In Server Manage, the Add Roles and Features menu command](../../Images\Image\ImageNotContaina/mds_ServerManagerDashboard_AddRolesFeaturesMenu.png "mds_ServerManagerDashboard_AddRolesFeaturesMenu")  
  
6.  On the **Installation Type** page of the **Add Roles and Features Wizard**, accept the default value \(**Role\-based or feature\-based installation**\) and click **Next**.  
  
7.  Click **Select a server from the server pool**, and then click the server where you installed [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)].  
  
     ![Server Selection page on the Add Roles and Features Wizard](../../Images\Image\ImageNotContaina/mds_ServerManagerDashboard_AddRolesandFeaturesWizard_ServerSelection.png "mds_ServerManagerDashboard_AddRolesandFeaturesWizard_ServerSelection")  
  
8.  In the **Roles** box, click the roles and roles services that are required for [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] on [!INCLUDE[winblue_server_2](../../Token\Other/winblue_server_2_md.md)], and then click **Next**. The following images show the selected, required roles and roles services.  
  
    > [!WARNING]  
    >  Do not install the WebDAV Publishing role service. WebDAV Publishing is not compatible with [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)].  
  
    > [!IMPORTANT]  
    >  **Dynamic Content Compression** is enabled by default. This significantly reduces the size of the xml response and saves the network I\/O, though CPU usage is increased.  For more information, see **\[CTP 2.0\] Improved Performance** in [What's New in Master Data Services &#40;MDS&#41;](../Topic/What's%20New%20in%20Master%20Data%20Services%20\(MDS\).md).  
  
    |Roles and Role Services|Roles and Role Services|  
    |-----------------------------|-----------------------------|  
    |![Common HTTP Features](../../Images\Image\ImageNotContaina/mds_ServerManagerDashboard_CommonHTTPFeaturesRoles.png "mds_ServerManagerDashboard_CommonHTTPFeaturesRoles")|![Health Diagnostics Roles](../../Images\Image\ImageNotContaina/mds_ServerManagerDashboard_HealthDiagnosticsRoles.png "mds_ServerManagerDashboard_HealthDiagnosticsRoles")|  
    |![Performance Roles](../../Images\Image\ImageNotContaina/mds_ServerManagerDashboard_PerformanceRoles.png "mds_ServerManagerDashboard_PerformanceRoles")|![Security Roles](../../Images\Image\ImageNotContaina/mds_ServerManagerDashboard_SecurityRoles.png "mds_ServerManagerDashboard_SecurityRoles")|  
    |![WebServer Application Development Roles](../../Images\Image\ImageNotContaina/mds_ServerManagerDashboard_WebServerApplicationDevelopmentRoles.png "mds_ServerManagerDashboard_WebServerApplicationDevelopmentRoles")|![Management Tools](../../Images\Image\ImageNotContaina/mds_ServerManagerDashboard_ManagementToolsRoles.png "mds_ServerManagerDashboard_ManagementToolsRoles")|  
  
     For a list of the required roles and roles services on various operating systems, see [Web Application Requirements &#40;Master Data Services&#41;](../Topic/Web%20Application%20Requirements%20\(Master%20Data%20Services\).md) .  
  
9. In the **Features** box, click the features that are required for [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] on [!INCLUDE[winblue_server_2](../../Token\Other/winblue_server_2_md.md)], and then click **Next**. The following images show the selected, required features.  
  
    |Features|Features|  
    |--------------|--------------|  
    |![Net Framework Features](../../Images\Image\ImageNotContaina/mds_ServerManagerDashboard_NetFrameworkFeatures.png "mds_ServerManagerDashboard_NetFrameworkFeatures")|![Windows Process Features](../../Images\Image\ImageNotContaina/mds_ServerManagerDashboard_WindowsProcessFeatures.png "mds_ServerManagerDashboard_WindowsProcessFeatures")|  
  
     For a list of the required features on various operating systems, see [Web Application Requirements &#40;Master Data Services&#41;](../Topic/Web%20Application%20Requirements%20\(Master%20Data%20Services\).md) .  
  
 For more information about installing [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] using setup, see [Install SQL Server 2016 from the Installation Wizard &#40;Setup&#41;](../Topic/Install%20SQL%20Server%202016%20from%20the%20Installation%20Wizard%20\(Setup\).md).  
  
 For more information about installing [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] using a command prompt, see [Install SQL Server 2016 from the Command Prompt](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016-from-the-Command-Prompt.md). When you use a command prompt, [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] is available as a feature parameter.  
  
 For a brief description with links to additional information about pre\-installation tasks, see [Install Master Data Services](../../Topics\TopicNameNotContainA/Install-Master-Data-Services.md).  
  
##  <a name="SetUpWeb"></a> Setting up the Database and Website  
 **To set up the database and website using the [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)]**  
  
1.  Launch the [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)], and click **Database Configuration** in the left pane.  
  
2.  Click **Create Database**, and then click **Next** in the **Create Database Wizard**.  
  
3.  On the **Database Server** page, select the **Authentication type** and then click **Test Connection** to confirm that you can connect to the database using the credentials for the authentication type you selected.  
  
    > [!NOTE]  
    >  When you select **Current User – Integrated Security** as the authentication type, **User name** box is read\-only and displays the name of the Windows user account that is logged on to the computer.  
  
     ![The Database server page in the Create Database Wizard](../../Images\Image\ImageNotContaina/mds_ConfigurationManager_CreateDatabaseWizard_ServerPage.png "mds_ConfigurationManager_CreateDatabaseWizard_ServerPage")  
  
4.  Type a name in the **Database name** field. Optionally, to select a Windows collation and specify one or more of the available options such as **Case\-sensitive**, clear the **SQL Server default collation** checkbox.  
  
     ![The Database page in the Create Database Wizard](../../Images\Image\ImageNotContaina/mds_ConfigurationManager_CreateDatabaseWizard_DatabasePage.png "mds_ConfigurationManager_CreateDatabaseWizard_DatabasePage")  
  
     For more information about Windows collation, see [Windows Collation Name \(Transact\-SQL\)](https://msdn.microsoft.com/library/ms188046.aspx).  
  
5.  In the **User name** field, specify  the Windows account of the user that will be the default Super User for Master Data Services. A Super User has access to all functional areas and can add, delete, and update all models.  
  
     ![The Administrator Account page in the Create Database Wizard.](../../Images\Image\ImageNotContaina/mds_ConfigurationManager_CreateDatabaseWizard_AdminPage.png "mds_ConfigurationManager_CreateDatabaseWizard_AdminPage")  
  
6.  Click **Next** to view a summary of the settings for the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)]database, and then click **Next** again to create the database.  
  
     For more information about the settings in the **Create Database Wizard**, see [Create Database Wizard &#40;Master Data Services Configuration Manager&#41;](../Topic/Create%20Database%20Wizard%20\(Master%20Data%20Services%20Configuration%20Manager\).md).  
  
7.  On the Database Configuration page in the [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)],  click Select Database.  
  
8.  Click **Connect**, and then select the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database that you created in Step 6.  
  
     ![Connect to Database dialog box for the Database Configuration page](../../Images\Image\ImageNotContaina/mds_ConfigurationManager_SelectDatabaseButton_ConnectToDatabaseDialog.png "mds_ConfigurationManager_SelectDatabaseButton_ConnectToDatabaseDialog")  
  
     You've finished setting up the database. The **Database Configuration** page now displays the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance that you're connected to for [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], the  database you've created and the current database version.  
  
     ![Database Configuration page in the Configuration Manager shows a completed database setup.](../../Images\Image\ImageContaina/mds_ConfigurationManager_DatabaseConfig_Completed.png "mds_ConfigurationManager_DatabaseConfig_Completed")  
  
9. In [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)], and click **Web Configuration** in the left pane.  
  
10. In the **Website** list box, click **Default Web Site**, and then click **Create** to create a Web application.  
  
    > [!NOTE]  
    >  When you select **Default Web Site**, you must create a Web application. If you select **Create new website** in the list box, the application is automatically created.  
  
     ![Web Configuration page in the Configuration Manager](../../Images\Image\ImageNotContaina/mds_ConfigurationManager_WebConfig.png "mds_ConfigurationManager_WebConfig")  
  
11. In the **Application Pool** section, do one of the following.  
  
    -   Enter the same user name that you entered in Step 5 for the database **Administrator Account**, enter the password, and then click **OK**.  
  
         **\-OR\-**  
  
    -   Enter a different user name, enter the password, and then click OK.  
  
         You don't have to use the same account when you create the database and the web application.  
  
     ![Create Web Application dialog box, Web Configuration page](../../Images\Image\ImageNotContaina/mds_ConfigurationManager_WebConfig_CreateWebApplication.png "mds_ConfigurationManager_WebConfig_CreateWebApplication")  
  
     For more information about the **Create Web Application** dialog box, see [Create Web Application Dialog Box &#40;Master Data Services Configuration Manager&#41;](../Topic/Create%20Web%20Application%20Dialog%20Box%20\(Master%20Data%20Services%20Configuration%20Manager\).md).  
  
12. On the **Web Configuration** page in the **Web application** box, click the application you've created, and then click **Select** in the  **Associate Application with Database** section.  
  
13. Click **Connect**, select the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database that you want to associate with the Web application, and then click **OK**.  
  
     You've finished setting up the Website. The **Web Configuration** page now displays the Website you selected,  Web application you created, and the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database  associated with the application.  
  
     ![The completed Web site configuration](../../Images\Image\ImageNotContaina/mds_ConfigurationManager_WebConfig_Completed.png "mds_ConfigurationManager_WebConfig_Completed")  
  
     For more information about the settings on the Web Configuration page, see [Web Configuration Page &#40;Master Data Services Configuration Manager&#41;](../Topic/Web%20Configuration%20Page%20\(Master%20Data%20Services%20Configuration%20Manager\).md)  
  
 You can also use [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)] to specify other settings for the Web applications and services associated with the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database. For example, you can specify how frequently data is loaded or how often validation emails are sent. For more information, see [System Settings &#40;Master Data Services&#41;](../Topic/System%20Settings%20\(Master%20Data%20Services\).md).  
  
##  <a name="deploySample"></a> Deploying Sample Models and Data  
 The following three sample model packages are included with  [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)].   These sample models include data. The default location for the sample model packages is *\<drive\>*\\Program Files\\Microsoft SQL Server\\130\\Master Data Services\\Samples\\Packages.  
  
-   chartofaccounts\_en.pkg  
  
-   customer\_en.pkg  
  
-   product\_en.pkg  
  
 You deploy the packages using the MDSModelDeploy tool. The default location for the MDSModelDeploy tool is *\<drive\>*\\Program Files\\Microsoft SQL Server\\ 130\\Master Data Services\\Configuration.  
  
 For information about prerequisites for running this tool, see [Deploy a Model Deployment Package by Using MDSModelDeploy](../../Topics\TopicNameContainA/Deploy-a-Model-Deployment-Package-by-Using-MDSModelDeploy.md).  
  
 For information about updates made to the data to support new features in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)][!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], see [Samples: Model Deployment Packages &#40;Master Data Services&#41;](../Topic/Samples:%20Model%20Deployment%20Packages%20\(Master%20Data%20Services\).md).  
  
 **To deploy the sample models**  
  
1.  Copy the sample model packages to \<drive\>\\Program Files\\Microsoft SQL Server\\130\\Master Data Services\\Configuration.  
  
2.  Open an Administrator: Command Prompt and navigate to MDSModelDeploy.exe, by running the following command.  
  
    ```  
    cd c:\Program Files\Microsoft SQL Server\130\Master Data Services\Configuration  
    ```  
  
3.  Deploy each of the sample models to [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] by running each of the following commands.  
  
    > [!IMPORTANT]  
    >  In the examples below, the `MDS1` service value is specified. You use this value if you selected  **Default Web Site** when you set up the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] Web site.  See the [Setting up the Database and Website](#SetUpWeb) section.  
    >   
    >  If you created a new web site or selected another existing web site, run the following command first to determine the correct service value.  
    >   
    >  `MDSModelDeploy listservices`  
    >   
    >  The first service value in the list of values returned, is the one you specify to deploy a model.  
  
     **To deploy the chartofaccounts\_en.pkg sample model**  
  
    ```  
    MDSModelDeploy deploynew -package chartofaccounts_en.pkg -model Customer -service MDS1  
    ```  
  
     **To deploy the customer\_en.pkg sample model**  
  
    ```  
    MDSModelDeploy deploynew -package customer_en.pkg -model Customer -service MDS1  
    ```  
  
     **To deploy the product\_en.pkg sample model**  
  
    ```  
    MDSModelDeploy deploynew -package product_en.pkg -model Customer -service MDS1  
  
    ```  
  
     When a model is successfully deployed, the **MDSModelDeploy operation completed** message is displayed.  
  
     The following image shows the command for deploying the product\_en.pkg sample model.  
  
     ![Command line for deploying the Product sample model](../../Images\Image\ImageNotContaina/mds_CommandPrompt_DeployingSampleModel_Product.png "mds_CommandPrompt_DeployingSampleModel_Product")  
  
4.  To view the sample models, do the following.  
  
    1.  Navigate to the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] web site that you set up. See the [Setting up the Database and Website](#SetUpWeb) section.  
  
         The web site address is http:\/\/\<server name\>\/\<web application\>\/.  
  
    2.  Select a model from the **Model** list box, and click **Explorer**.  
  
         ![MDS Web site, home page.](../../Images\Image\ImageNotContaina/mds_MDSWebSite_HomePage_SelectSampleModel.png "mds_MDSWebSite_HomePage_SelectSampleModel")  
  
## Next Step  
 Create a new model and entities for your data. See [Create a Model &#40;Master Data Services&#41;](../Topic/Create%20a%20Model%20\(Master%20Data%20Services\).md) and [Create an Entity &#40;Master Data Services&#41;](../Topic/Create%20an%20Entity%20\(Master%20Data%20Services\).md).  
  
 For an overview of how you use a model and entities to build a structure for your data in [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], see [Master Data Services Overview &#40;MDS&#41;](../Topic/Master%20Data%20Services%20Overview%20\(MDS\).md)  
  
## Did this Article Help You? We’re Listening  
 What information are you looking for, and did you find it? We’re listening to your feedback to improve the content. Please submit your comments to [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Get%20Started%20with%20Master%20Data%20Services)  
  
## See Also  
 [Master Data Services Database](../../Topics\TopicNameNotContainA/Master-Data-Services-Database.md)   
 [Master Data Manager Web Application](../../Topics\TopicNameNotContainA/Master-Data-Manager-Web-Application.md)   
 [Database Configuration Page &#40;Master Data Services Configuration Manager&#41;](../Topic/Database%20Configuration%20Page%20\(Master%20Data%20Services%20Configuration%20Manager\).md)   
 [What's New in Master Data Services &#40;MDS&#41;](../Topic/What's%20New%20in%20Master%20Data%20Services%20\(MDS\).md)  
  
  