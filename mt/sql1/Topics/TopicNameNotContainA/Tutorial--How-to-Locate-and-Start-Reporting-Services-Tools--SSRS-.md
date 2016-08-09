---
title: "Tutorial: How to Locate and Start Reporting Services Tools (SSRS)"
ms.custom: na
ms.date: 2016-05-31
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 51ad69d8-fe92-4662-a7cd-d235692f0c03
caps.latest.revision: 59
caps.handback.revision: 0
manager: mblythe
---
# Tutorial: How to Locate and Start Reporting Services Tools (SSRS)
This tutorial introduces the tools used to configure a report server, manage report server content and operations, and create and publish paginated and mobile [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] reports. The purpose of this tutorial is to help you understand how to find and open each tool. If you are already familiar with the tools, you can move on to other tutorials to learn skills for using [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)]. For other tutorials, see [Reporting Services Tutorials (SSRS)](assetId:///e90cc448-563b-4dbb-9776-defb8640ec66).  
  
 In this topic:  
  
-   [Reporting Services Configuration Manager (Native Mode)](#bkmk_configuration_manager)  
  
-   [Report Manager (Native Mode)](#bkmk_report_manager)  
  
-   [SQL Server Management Studio](#bkmk_managements_studio)  
  
-   [SQL Server Data Tools with Report Designer and Report Wizard](#bkmk_ssdt)  
  
-   [SQL Server Reporting Services Report Builder](#bkmk_report_builder)  
  
-   [SQL Server Mobile Report Publisher](#bkmk_mobile_report_pub)  
  
##  <a name="bkmk_configuration_manager"></a> Reporting Services Configuration Manager (Native Mode)  
 Use the Native mode configuration manager to complete the following:  
  
-   Specify the service account.  
  
-   Create or upgrade the report server database.  
  
-   Modify the connection properties.  
  
-   Specify URLs.  
  
-   Manage encryption keys.  
  
-   Configure unattended report processing and e-mail report delivery.  
  
 **Installation:** [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] Configuration Manager is installed when you install [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] Native mode. For more information, see [Install Reporting Services Native Mode Report Server](../../Topics/TopicNameNotContainA/Install-Reporting-Services-Native-Mode-Report-Server.md)  
  
#### To start the Reporting Services Configuration Manager  
  
1.  On the Windows start screen, type **reporting** and in the **Apps** search results, click **Reporting Services Configuration Manager**.  
  
     ![reporting services configuration manager on start](../../Topics/TopicNameNotContainA/images/bi_ssrs_configmanager_win8_startscreen.gif "bi_ssrs_configmanager_win8_startscreen")  
  
     **Or**  
  
     Click **Start**, then click **Programs**, then click [!INCLUDE[ssCurrentUI](../../Topics/TopicNameContainA/tokens/ssCurrentUI_md.md)], then click **Configuration Tools**, and then click **Reporting Services Configuration Manager**.  
  
     The **Report Server Installation Instance Selection** dialog box appears so that you can select the report server instance you want to configure.  
  
2.  In **Server Name**, specify the name of the computer on which the report server instance is installed. The name of the local computer is specified by default, but you can also type the name of a remote [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance.  
  
     If you specify a remote computer, click **Find** to establish a connection. The report server must be configured for remote administration in advance. For more information, see [Configure a Report Server for Remote Administration](../../Topics/TopicNameContainA/Configure-a-Report-Server-for-Remote-Administration.md).  
  
3.  In **Instance Name**, choose the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] instance that you want to configure. Only [!INCLUDE[ssKatmai](../../Topics/TopicNameContainA/tokens/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Topics/TopicNameContainA/tokens/ssKilimanjaro_md.md)], and [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] report server instances appear in the list. You cannot configure earlier versions of [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)].  
  
4.  Click **Connect**.  
  
5.  To verify that you launched the tool, compare your results to the following image:  
  
     ![Reporting Services Configuration tool](../../Topics/TopicNameNotContainA/images/rs_ui_reportserverconfigkatmai.png "rs_ui_reportserverconfigkatmai")  
  
 **Next Steps:** [Configure and Administer a Report Server (SSRS Native Mode)](../../Topics/TopicNameContainA/Configure-and-Administer-a-Report-Server--SSRS-Native-Mode-.md) and [Reporting Services Configuration Manager (Native Mode)](../../Topics/TopicNameNotContainA/Reporting-Services-Configuration-Manager--Native-Mode-.md).  
  
##  <a name="bkmk_report_manager"></a> Report Manager (Native Mode)  
 Use [Report Manager  (SSRS Native Mode)](../../Topics/TopicNameNotContainA/Report-Manager---SSRS-Native-Mode-.md) to set permissions, manage subscriptions and schedules, and work with reports. You can also use Report Manager to view reports.  
  
 **Installation:** Report Manager Is installed when you install [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] Native mode: [Install Reporting Services Native Mode Report Server](../../Topics/TopicNameNotContainA/Install-Reporting-Services-Native-Mode-Report-Server.md)  
  
 Before you can open Report Manager, you must have sufficient permissions (initially, only members of the local Administrators group have permissions that provide access to Report Manager features). Report Manager provides different pages and options depending on the role assignments of the current user. Users who have no permissions will get an empty page. Users with permissions to view reports will get links that they can click to open the reports. To learn more about permissions, see [Roles and Permissions (Reporting Services)](../../Topics/TopicNameNotContainA/Roles-and-Permissions--Reporting-Services-.md).  
  
#### To start Report Manager  
  
1.  Open your browser. For information on supported browsers and browser versions, see [Browser Support for Reporting Services and Power View](../../Topics/TopicNameNotContainA/Browser-Support-for-Reporting-Services-and-Power-View.md).  
  
2.  In the address bar of the Web browser, type the Report Manager URL. By default, the URL is **http://<serverName\>/reports**. You can use the Reporting Services Configuration tool to confirm the server name and URL. For more information about URLs used in [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)], see [Configure Report Server URLs  (SSRS Configuration Manager)](../../Topics/TopicNameNotContainA/Configure-Report-Server-URLs---SSRS-Configuration-Manager-.md).  
  
3.  Report Manager opens in the browser window. The startup page is the Home folder. Depending on permissions, you might see additional folders, hyperlinks to reports, and resource files within the startup page. You might also see additional buttons and commands on the toolbar.  
  
4.  If you run Report Manager on the local report server, see [Configure a Native Mode Report Server for Local Administration (SSRS)](../../Topics/TopicNameContainA/Configure-a-Native-Mode-Report-Server-for-Local-Administration--SSRS-.md).  
  
 **Next Steps:** [Configure Report Manager (Native Mode)](../../Topics/TopicNameNotContainA/Configure-Report-Manager--Native-Mode-.md).  
  
##  <a name="bkmk_managements_studio"></a> Management Studio  
 Report server administrators can use [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)] to manage a report server alongside other [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] component servers. For more information, see [Management Studio](assetId:///f289e978-14ca-46ef-9e61-e1fe5fd593be).  
  
#### To Start SQL Server Management Studio  
  
1.  From the Windows Start Screen type **sql server** and in the **Apps** search results, click **SQL Server Management Studio**.  
  
     ![managment studio from windows start screen](../../Topics/TopicNameNotContainA/images/bi_ssms_win8_startscreen.gif "bi_ssms_win8_startscreen")  
  
     **Or**  
  
     Click **Start**, then click **All Programs**, then click [!INCLUDE[ssCurrentUI](../../Topics/TopicNameContainA/tokens/ssCurrentUI_md.md)], and then click **SQL Server Management Studio**. The **Connect to Server** dialog box appears.  
  
2.  If the **Connect to Server** dialog box does not appear, in **Object Explorer**, click **Connect** and then select **Reporting Services**.  
  
3.  In the **Server type** list, select **Reporting Services**. If [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] is not on the list, it is not installed.  
  
4.  In the **Server name** list, select a report server instance. Local instances appear in the list. You can also type the name of a remote [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance.  
  
5.  Click **Connect**. You can expand the root node to set server properties, modify role definitions, or turn off report server features.  
  
##  <a name="bkmk_ssdt"></a> SQL Server Data Tools with Report Designer and Report Wizard  
 You have a choice of two different tools for creating [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] paginated reports:    Report Designer and [Report Builder](#bkmk_report_builder).  
  
 Report Designer is available in [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)] - Visual Studio. The Report Designer design surface includes tabbed windows, wizards, and menus used to access report authoring features. The report designer tool becomes available when you choose a Report Server Project or a Report Server Wizard template  in [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)]. To learn more, see [Reporting Services in SQL Server Data Tools (SSDT)](../../Topics/TopicNameNotContainA/Reporting-Services-in-SQL-Server-Data-Tools--SSDT-.md).  
  
#### To start Report Designer  
  
1.  Open **SQL Server Data Tools**.  
  
2.  On the **File** menu, point to **New**, and then click **Project**.  
  
3.  In the **Project Types** list, click **Business Intelligence Projects**.  
  
4.  In the **Templates** list, click **Report Server Project**. The following diagram shows how the project templates appear in the dialog box:  
  
     ![New Project template dialog box](../../Topics/TopicNameNotContainA/images/rs_ui_newrsproject.gif "rs_ui_newrsproject")  
  
5.  Type a name and location for the project, or click **Browse** and select a location.  
  
6.  [!INCLUDE[clickOK](../../Topics/TopicNameContainA/tokens/clickOK_md.md)] [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)] opens with the [!INCLUDE[vsprvs](../../Topics/TopicNameContainA/tokens/vsprvs_md.md)] start page. Solution Explorer provides categories for creating reports and data sources. You can use these categories to create new reports and data sources. Tabbed windows appear when you create a report definition. The tabbed windows are Data, Layout, and Preview..  
  
 To get started on your first report, see [Create a Basic Table Report (SSRS Tutorial)](assetId:///3b539b4b-26f2-4c0b-b506-80f175679a46). To learn more about query designers you can use within Report Designer, see [Query Design Tools (SSRS)](../../Topics/TopicNameNotContainA/Query-Design-Tools--SSRS-.md).  
  
##  <a name="bkmk_report_builder"></a> [!INCLUDE[ssRBnoversion](../../Topics/TopicNameContainA/tokens/ssRBnoversion_md.md)]  
 [Report Builder in SQL Server 2016](../../Topics/TopicNameNotContainA/Report-Builder-in-SQL-Server-2016.md) is a stand-alone application you can use to create paginated reports outside [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. You can customize and update all existing reports, regardless of whether they were created in Report Designer or in previous versions of [!INCLUDE[ssRBnoversion](../../Topics/TopicNameContainA/tokens/ssRBnoversion_md.md)]. You can install it from the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] web portal or from the Microsoft Download Center.  
  
 [Download Report Builder](http://go.microsoft.com/fwlink/?LinkID=219138) from the Microsoft Download Center.  
  
#### To start [!INCLUDE[ssRBnoversion](../../Topics/TopicNameContainA/tokens/ssRBnoversion_md.md)]  
  
1.  In the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] web portal, on the  **New** menu, select **Paginated Report**.  
  
     ![PBI&#95;SSMRP&#95;NewMenu](../../Topics/TopicNameContainA/images/PBI_SSMRP_NewMenu.png "PBI_SSMRP_NewMenu")  
  
2.  If [!INCLUDE[ssRBnoversion](../../Topics/TopicNameContainA/tokens/ssRBnoversion_md.md)] isn't installed on this computer yet, select **Get [!INCLUDE[ssRBnoversion](../../Topics/TopicNameContainA/tokens/ssRBnoversion_md.md)]**.  
  
     Or  
  
     [Download Report Builder](http://go.microsoft.com/fwlink/?LinkID=219138) from the Microsoft Download Center.  
  
3.  [!INCLUDE[ssRBnoversion](../../Topics/TopicNameContainA/tokens/ssRBnoversion_md.md)] opens and you can create or open a paginated report.  
  
##  <a name="bkmk_mobile_report_pub"></a> [!INCLUDE[SS_MobileReptPub_Long](../../Topics/TopicNameContainA/tokens/SS_MobileReptPub_Long_md.md)]  
 Use [SQL Server Mobile Report Publisher](../../Topics/TopicNameNotContainA/SQL-Server-Mobile-Report-Publisher.md) to create mobile reports you can view in the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] web portal and in mobile devices such as iPads and iPhones.   You can install it from the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] web portal or  from the Microsoft Download Center.  
  
 [Download SQL Server Mobile Report Publisher](http://go.microsoft.com/fwlink/?LinkID=733527) from the Microsoft Download Center.  
  
#### To start [!INCLUDE[SS_MobileReptPub_Short](../../Topics/TopicNameNotContainA/tokens/SS_MobileReptPub_Short_md.md)]  
  
1.  In the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] web portal, on the  **New** menu, select **Mobile Report**.  
  
     ![PBI&#95;SSMRP&#95;NewMenu](../../Topics/TopicNameContainA/images/PBI_SSMRP_NewMenu.png "PBI_SSMRP_NewMenu")  
  
2.  If [!INCLUDE[SS_MobileReptPub_Short](../../Topics/TopicNameNotContainA/tokens/SS_MobileReptPub_Short_md.md)] isn't installed on this computer yet, select **Get [!INCLUDE[SS_MobileReptPub_Short](../../Topics/TopicNameNotContainA/tokens/SS_MobileReptPub_Short_md.md)]**.  
  
     Or  
  
     [Download SQL Server Mobile Report Publisher](http://go.microsoft.com/fwlink/?LinkID=733527) from the Microsoft Download Center.  
  
3.  [!INCLUDE[SS_MobileReptPub_Short](../../Topics/TopicNameNotContainA/tokens/SS_MobileReptPub_Short_md.md)] opens and you can create or open a mobile report.  
  
## See Also  
 [Download SQL Server Mobile Report Publisher](http://go.microsoft.com/fwlink/?LinkID=733527)   
 [Download Report Builder](http://go.microsoft.com/fwlink/?LinkID=219138)   
 [Install Reporting Services SharePoint Mode](../../Topics/TopicNameNotContainA/Install-Reporting-Services-SharePoint-Mode.md)   
 [Reporting Services Report Server](../../Topics/TopicNameNotContainA/Reporting-Services-Report-Server.md)   
 [Query Design Tools (SSRS)](../../Topics/TopicNameNotContainA/Query-Design-Tools--SSRS-.md)   
 [Reporting Services Tutorials (SSRS)](assetId:///e90cc448-563b-4dbb-9776-defb8640ec66)