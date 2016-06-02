---
title: Reporting Services Configuration Manager (Native Mode)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 379eab68-7f13-4997-8d64-38810240756e
---
# Reporting Services Configuration Manager (Native Mode)
  Use the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager to configure a [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Native Mode installation. If you installed a report server by using the files\-only installation option, you must use the Configuration Manager to configure the server before you can use it. If you installed a report server by using the default configuration installation option, you can use the Configuration Manager to verify or modify the settings that were specified during setup. [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager can be used to configure a local or remote report server instance.  
  
 [!INCLUDE[applies](../../Token\Other/applies_md.md)] [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Native mode.  
  
> [!NOTE] Starting with the [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] release, the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager is not designed to manage SharePoint mode report servers. SharePoint mode is managed and configured by using SharePoint Central Administration and PowerShell scripts.  
  
##  <a name="bkmk_scenarios"></a> Scenarios to use Reporting Services Configuration Manager  
 You can use the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager to perform the following tasks:  
  
-   Configure the Report Server service account. The account is initially configured during setup, but can be modified by using the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager if you update the password or want to use a different account.  
  
-   Create and configure URLs. The report server and the [!INCLUDE[ssRSWebPortal-Non-Markdown](../../Token\Other/ssRSWebPortal-Non-Markdown_md.md)] are [!INCLUDE[vstecasp](../../Token\Other/vstecasp_md.md)] applications accessed through URLs. The report server URL provides access to the SOAP endpoints of the report server. The [!INCLUDE[ssRSWebPortal-Non-Markdown](../../Token\Other/ssRSWebPortal-Non-Markdown_md.md)] URL is used to open the [!INCLUDE[ssRSWebPortal-Non-Markdown](../../Token\Other/ssRSWebPortal-Non-Markdown_md.md)] You can configure a single URL or multiple URLs for each application.  
  
-   Create and configure the report server database. The report server is a stateless server that requires a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database for internal storage. You can use the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager to create and configure a connection to the report server database. You can also select an existing report server database that already contains the content you want to use.  
  
-   Configure a Native mode scale\-out deployment. [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] supports a deployment topology that allows multiple report server instances use a single, shared report server database. To deploy a report server scale\-out deployment, you use the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager to connect each report server to the shared report server database.  
  
-   Backup, restore, or replace the symmetric key that is used to encrypt stored connection strings and credentials. You must have a backup of the symmetric key if you change the service account, or move a report server database to another computer.  
  
-   Configure the unattended execution account. This account is used for remote connections during scheduled operations or when user credentials are not available.  
  
-   Configure report server e\-mail. [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] includes a report server e\-mail delivery extension that uses a Simple Mail Transfer Protocol \(SMTP\) to deliver reports or report processing notification to an electronic mailbox. You can use the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager to specify which SMTP server or gateway on your network to use for e\-mail delivery.  
  
 The [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager does not help you manage report server content, enable additional features, or grant access to the server. Full deployment requires that you also use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] to enable additional features or modify default values, and Report Manager to grant user access to the server.  
  
##  <a name="bkmk_requirements"></a> Requirements  
 The [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager is version\-specific. The [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager that installs with this version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] cannot be used to configure an earlier version of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]. If you are running older and newer versions of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] side\-by\-side on the same computer, you must use the Reporting Service Configuration manager that comes with each version to configure each instance.  
  
 To use the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration manager, you must have the following:  
  
-   Local system administrator permissions on the computer that hosts the report server you want to configure. If you are configuring a remote computer, you must have local system administrator permissions on that computer as well.  
  
-   You must have permission to create databases on the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] used to host the report server database.  
  
-   Windows Management Instrumentation \(WMI\) service must be enabled and running on any report server you are configuring. The [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager uses the report server WMI provider to connect to local and remote report servers. If you are configuring a remote report server, the computer must allow remote WMI access. For more information, see [Configure a Report Server for Remote Administration](../../Topics\TopicNameContainA/Configure-a-Report-Server-for-Remote-Administration.md).  
  
-   Before you can connect to and configure a remote report server instance, you must enable remote Windows Management Instrumentation \(WMI\) calls to pass through Windows Firewall. For more information, see [Configure a Report Server for Remote Administration](../../Topics\TopicNameContainA/Configure-a-Report-Server-for-Remote-Administration.md) in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Books Online.  
  
 The [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager is installed automatically when you install [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]  
  
##  <a name="bkmk_start_configuration_manager"></a> To Start the Reporting Services Configuration Manager  
  
1.  Use the following step that is appropriate for your version of Microsoft Windows:  
  
    -   From the Windows start screen, type **Reporting** and select **Reporting Services Configuration Manager** from the search results.  
  
    -   Select **Start**, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../Token\Other/ssCurrentUI_md.md)], and then point to **Configuration Tools**.  
  
         If you want to configure a report server instance from a previous version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], open the program folder for that version. For example, point to [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] instead of [!INCLUDE[ssCurrentUI](../../Token\Other/ssCurrentUI_md.md)] to open the configuration tools for [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] server components.  
  
         Select **Reporting Services Configuration Manager**.  
  
2.  The **Reporting Services Configuration Connection** dialog box appears so that you can select the report server instance you want to configure. Select **Connect**.  
  
3.  In **Server Name**, specify the name of the computer on which the report server instance is installed. The name of the local computer appears by default, but you can type the name of a remote [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance if you want to connect to a report server that is installed on a remote computer.  
  
4.  If you specify a remote computer, select **Find** to establish a connection.  
  
5.  In **Report Server Instance**, select the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] instance that you want to configure. Only report server instances for this version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] appear in the list. You cannot configure earlier versions of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)].  
  
6.  Select **Connect**.  
  
## See Also  
 [Web portal &#40;SSRS Native Mode&#41;](../Topic/Web%20portal%20\(SSRS%20Native%20Mode\).md)   
 [Reporting Services Tools](../../Topics\TopicNameNotContainA/Reporting-Services-Tools.md)   
 [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20a%20Report%20Server%20Database%20Connection%20%20\(SSRS%20Configuration%20Manager\).md)   
 [SQL Server Configuration Manager](../../Topics\TopicNameNotContainA/SQL-Server-Configuration-Manager.md)   
 [Configure and Administer a Report Server &#40;SSRS Native Mode&#41;](../Topic/Configure%20and%20Administer%20a%20Report%20Server%20\(SSRS%20Native%20Mode\).md)  
  
  