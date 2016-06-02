---
title: Install Reporting Services Native Mode Report Server
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8f25e6dc-b753-400e-9e9a-50f4f35bf6c4
---
# Install Reporting Services Native Mode Report Server
  A [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] native mode report server is the default [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] server mode and can be installed from the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installation wizard or from the command line. In the setup wizard, you can select to either install files and configure the server with default settings or to only install the files. This topic reviews the *Default configuration for native mode* where Setup both installs and configures a report server instance. After Setup is finished, the report server is running and ready to use for basic report viewing and report management.  Additional features such as [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)] integration and e\-mal delivery with subscription processing require additional configuration.  
  
||  
|-|  
|**[!INCLUDE[applies](../../Token\Other/applies_md.md)]**  [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Native mode|  
  
##  <a name="bkmk_top"></a> In this topic  
  
-   [What is the Default Configuration?](#bkmk_whatisdefaultconfiguration)  
  
-   [When to Install the Default Configuration for Native Mode](#bkmk_whentoinstalldefaultconfig)  
  
-   [Requirements](#bkmk_requirements)  
  
-   [Default URL Reservations](#bkmk_defaultURLreservations)  
  
-   [Install Native Mode with the SQL Server Installation Wizard](#bkmk_installwithwizard)  
  
-   [Additional Configuration](#bkmk_additional_configuration)  
  
##  <a name="bkmk_whatisdefaultconfiguration"></a> What is the Default Configuration?  
 Setup installs the following [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] features when you select the default configuration for native mode option:  
  
-   Report Server service \(which includes the Report Server Web service, background processing application, and the [!INCLUDE[ssRSWebPortal-Non-Markdown](../../Token\Other/ssRSWebPortal-Non-Markdown_md.md)] for viewing and managing reports as well as permissions.  
  
-   The [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager  
  
-   The [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] command line utilities rsconfig.exe, rskeymgmt.exe and rs.exe.  
  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] and [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] are now separate downloads.  
  
 Setup configures the following for a native mode report server installation:  
  
-   Service account for the Report Server service.  
  
-   Report Server Web service URL.  
  
-   The [!INCLUDE[ssRSWebPortal-Non-Markdown](../../Token\Other/ssRSWebPortal-Non-Markdown_md.md)] URL.  
  
-   Report Server database.  
  
-   Service account access to the report server databases.  
  
-   Connection information, also known as the data source name \(DSN\), for the report server databases.  
  
 Setup does not configure the unattended execution account, report server e\-mail, back up the encryption keys, or a scale\-out deployment. You can use the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager to configure these properties. For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../Topic/Reporting%20Services%20Configuration%20Manager%20\(Native%20Mode\).md).  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [In this topic](#bkmk_top)  
  
##  <a name="bkmk_whentoinstalldefaultconfig"></a> When to Install the Default Configuration for Native Mode  
 A default configuration installs [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] in an operational state so that you can use the report server immediately after Setup is finished. Specify this mode when you want to save steps by eliminating any required configuration tasks you would otherwise have to perform in the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration tool.  
  
 Installing the default configuration does not guarantee that the report server will work after Setup is finished. The default URLs might not register when the service starts. Always test your installation to verify that the service starts and runs as expected.  See [Verify a Reporting Services Installation](../../Topics\TopicNameContainA/Verify-a-Reporting-Services-Installation.md).  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [In this topic](#bkmk_top)  
  
##  <a name="bkmk_requirements"></a> Requirements  
 The default configuration option uses default values to configure the core settings required to make a report server operational. It has the following requirements:  
  
-   Review [Hardware and Software Requirements for Installing SQL Server 2016](../../Topics\TopicNameNotContainA/Hardware-and-Software-Requirements-for-Installing-SQL-Server-2016.md) .  
  
-   [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] must be installed together in the same instance. The [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] instance hosts the report server database that Setup creates and configures.  
  
-   The user account used to run Setup must be a member of the local Administrators group and have permission to access and create databases on the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] instance that hosts the report server databases.  
  
-   Setup must be able to use the default values to reserve the URLs that provide access to the report server and the [!INCLUDE[ssRSWebPortal-Non-Markdown](../../Token\Other/ssRSWebPortal-Non-Markdown_md.md)]. These values are port 80, a strong wildcard, and the virtual directory names in the format **ReportServer\_\<***instance\_name***\>** and **Reports\_\<***instance\_name***\>**.  
  
-   Setup must be able to use the default values to create the report server databases. These values are **ReportServer** and **ReportServerTempDB**. If you have existing databases from a previous installation, Setup will be blocked because it cannot configure the report server in the default configuration for native mode. You must rename, move, or delete the databases to unblock Setup.  
  
 If your computer does not meet all requirements for a default installation, you must install [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] in files\-only mode and then use the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager to configure it after Setup is finished.  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [In this topic](#bkmk_top)  
  
##  <a name="bkmk_defaultURLreservations"></a> Default URL Reservations  
 URL reservations are composed of a prefix, host name, port, and virtual directory:  
  
|Part|Description|  
|----------|-----------------|  
|Prefix|The default prefix is HTTP. If you previously installed a Secure Sockets Layer \(SSL\) certificate, Setup will try to create URL reservations that use the HTTPS prefix.|  
|Host name|The default host name is a strong wildcard \(\+\). It specifies that the report server will accept any HTTP request on the designated port for any host name that resolves to the computer, including http:\/\/\<computername\>\/reportserver, http:\/\/localhost\/reportserver, or http:\/\/\<IPAddress\>\/reportserver.|  
|Port|The default port is 80. Note that if you use any port other than port 80, you will have to explicitly add it to the URL when you open a [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Web application in a browser window.|  
|Virtual directory|By default, virtual directories are created in the format of ReportServer\_\<*instance\_name*\> for the Report Server Web service and Reports\_\<*instance\_name*\> for the [!INCLUDE[ssRSWebPortal-Non-Markdown](../../Token\Other/ssRSWebPortal-Non-Markdown_md.md)]. For the Report Server Web service, the default virtual directory is **reportserver**. For the [!INCLUDE[ssRSWebPortal-Non-Markdown](../../Token\Other/ssRSWebPortal-Non-Markdown_md.md)], the default virtual directory is **reports**.|  
  
 An example of the complete URL string might be as follows:  
  
-   http:\/\/\+:80\/reportserver, provides access to the report server.  
  
-   http:\/\/\+:80\/reports, provides access to the [!INCLUDE[ssRSWebPortal-Non-Markdown](../../Token\Other/ssRSWebPortal-Non-Markdown_md.md)].  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [In this topic](#bkmk_top)  
  
##  <a name="bkmk_installwithwizard"></a> Install Native Mode with the SQL Server Installation Wizard  
 The following list describes the  [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] specific  steps and options you select in the SQL Server Installation Wizard. The list does not described each page you will see in the installation wizard, only the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] related pages that are part of a Native mode installation.  
  
1.  Run the SQL Server setup wizard \(setup.exe\) and step through the following preliminary pages:  
  
    -   Product Key  
  
    -   License Terms  
  
    -   Global Rules  
  
    -   Microsoft Update  
  
    -   Product Updates  
  
    -   Install Setup Files  
  
    -   Install Rules  
  
2.  On the **Setup Role** page, Select **SQL Server Feature Installation**.  
  
     ![SQL Server Feature Installation for setup role](../../Images\Image\ImageNotContaina/rs_SetupRole.png "rs_SetupRole")  
  
3.  On the **Feature Selection** page, select the following:  
  
    -   \(1\) **Database Engine Services**, unless an instance of the database engine is already installed.  
  
    -   \(2\) **Reporting Services\-Native**.  
  
     ![SSRS Native Mode Select in Feature Selection](../../Images\Image\ImageNotContaina/rs_SetupFeatureSelection_Native_withcircles.png "rs_SetupFeatureSelection_Native_withcircles")  
  
4.  Review the **Feature Rules** passed.  
  
5.  On the Instance configuration page, remember that if you choose to configure a **Named Instance**, you will need to use the instance name in URLS when you browse to Report Manger and the report server itself. If the instance was name was "THESQLINSTANCE" , the URLS would look like the following:  
  
    -   `http://[ServerName]/ReportServer_THESQLINSTANCE`  
  
    -   `http://[ServerName]/Reports_THESQLINSTANCE`  
  
6.  **Server Configuration**: If you plan to use the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] subscription feature, then on the **Server Configuration** page, configure SQL Server Agent **Automatic** Startup type.   The default is manual.  
  
7.  Add  SQL Server administrators on the **Database Engine Configuration** page.  
  
8.  On the **Reporting Services Configuration** page select **Install and Configure**.  
  
     ![SSRS Native Mode Configuration](../../Images\Image\ImageNotContaina/rs_SetupConfiguration_native_with_circles.png "rs_SetupConfiguration_native_with_circles")  
  
    > [!NOTE]  
    >  **Install and Configure** will not be available unless the database feature is also selected to be installed.  
  
9. Feature Configuration Rules: verify the rules passed. The setup wizard automatically advances to the **Ready to install** if the rules all pass.  Specific to [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)], the rules verify a report server catalog and temp catalog database do not already exist.  
  
10. ![note](../../Images\Image\ImageNotContaina/ssrs_fyi_note.png "ssrs_fyi_note")On the **ready to install** page, note the path to the  configuration file as you can refer to it at a later time for a good summary of the servers initial [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] configuration including the components installed, service accounts and administrators.  
  
11. After the SQL Server installation wizard is complete, verify the default Native mode installation using the following basic steps.  
  
    -   Open [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager and confirm you can connect to the report server.  
  
    -   Open your browser **with administrative privileges** and connect to the [!INCLUDE[ssRSWebPortal-Non-Markdown](../../Token\Other/ssRSWebPortal-Non-Markdown_md.md)], for example `http://localhost/Reports`.  
  
    -   Open your browser with administrative privileges and connect to the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report server page. For example,  `http://localhost/ReportServer`  
  
 For more information, see the Native section of the following two topics:  
  
 [Verify a Reporting Services Installation](../../Topics\TopicNameContainA/Verify-a-Reporting-Services-Installation.md)  
  
 [Troubleshoot a Reporting Services Installation](../../Topics\TopicNameContainA/Troubleshoot-a-Reporting-Services-Installation.md)  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [In this topic](#bkmk_top)  
  
##  <a name="bkmk_additional_configuration"></a> Additional Configuration  
  
-   To configure [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)] integration so you can pin report items to a [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)] dashboard, see [Power BI Report Server Integration &#40;Configuration Manager&#41;](../Topic/Power%20BI%20Report%20Server%20Integration%20\(Configuration%20Manager\).md).  
  
-   To configure email for subscriptions processing, see [E-Mail Settings - Reporting Services Native mode &#40;Configuration Manager&#41;](../Topic/E-Mail%20Settings%20-%20Reporting%20Services%20Native%20mode%20\(Configuration%20Manager\).md) and [E-Mail Delivery in Reporting Services](../../Topics\TopicNameNotContainA/E-Mail-Delivery-in-Reporting-Services.md).  
  
-   To configure the [!INCLUDE[ssRSWebPortal-Non-Markdown](../../Token\Other/ssRSWebPortal-Non-Markdown_md.md)] so you can access it on a report computer to view and manage reports, see [Configure a Firewall for Report Server Access](../../Topics\TopicNameContainA/Configure-a-Firewall-for-Report-Server-Access.md) and [Configure a Report Server for Remote Administration](../../Topics\TopicNameContainA/Configure-a-Report-Server-for-Remote-Administration.md).  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [In this topic](#bkmk_top)  
  
## See Also  
 [Troubleshoot a Reporting Services Installation](../../Topics\TopicNameContainA/Troubleshoot-a-Reporting-Services-Installation.md)   
 [Verify a Reporting Services Installation](../../Topics\TopicNameContainA/Verify-a-Reporting-Services-Installation.md)   
 [Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20the%20Report%20Server%20Service%20Account%20\(SSRS%20Configuration%20Manager\).md)   
 [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20Report%20Server%20URLs%20%20\(SSRS%20Configuration%20Manager\).md)   
 [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20a%20Report%20Server%20Database%20Connection%20%20\(SSRS%20Configuration%20Manager\).md)   
 [Files-Only Installation &#40;Reporting Services&#41;](../Topic/Files-Only%20Installation%20\(Reporting%20Services\).md)   
 [Initialize a Report Server &#40;SSRS Configuration Manager&#41;](../Topic/Initialize%20a%20Report%20Server%20\(SSRS%20Configuration%20Manager\).md)   
 [Configure SSL Connections on a Native Mode Report Server](../../Topics\TopicNameContainA/Configure-SSL-Connections-on-a-Native-Mode-Report-Server.md)   
 [Configure Windows Service Accounts and Permissions](../../Topics\TopicNameNotContainA/Configure-Windows-Service-Accounts-and-Permissions.md)   
 [Quick-Start Installation of SQL Server 2016](../../Topics\TopicNameNotContainA/Quick-Start-Installation-of-SQL-Server-2016.md)  
  
  