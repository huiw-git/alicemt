---
title: Reporting Services Report Server
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 88ed5b97-1d28-4980-80e4-b36761f3c03a
---
# Reporting Services Report Server
  This topic is an overview of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report server, the central component of a [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] installation. It consists of a pair of processing engines plus a collection of special\-purpose extensions that handle authentication, data processing, rendering, and delivery operations. A [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report server runs in one of two deployment modes; Native mode or SharePoint mode. See the [Feature Comparison of SharePoint and Native Mode](#bkmk_featuresupport) section for a comparison of features.  
  
 **Installation:** For information on [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] installation, see the following:  
  
-   [Install Reporting Services Native Mode Report Server](../../Topics\TopicNameNotContainA/Install-Reporting-Services-Native-Mode-Report-Server.md)  
  
-   [Install SQL Server BI Features with SharePoint &#40;Power Pivot and Reporting Services&#41;](../Topic/Install%20SQL%20Server%20BI%20Features%20with%20SharePoint%20\(Power%20Pivot%20and%20Reporting%20Services\).md)  
  
 **Windows Azure**: For information on using [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] with Windows Azure Virtual Machines, see the following:  
  
-   [SQL Server Business Intelligence in Windows Azure Virtual Machines](http://msdn.microsoft.com/en-us//library/windowsazure/jj992719.aspx).  
  
-   [Use PowerShell to Create an Azure VM With a Native Mode Report Server](https://msdn.microsoft.com/en-us/library/azure/dn449661.aspx).  
  
##  <a name="bkmk_top"></a> In this topic  
  
-   [Overview of Report Server Modes](#bkmk_overview)  
  
-   [Feature Comparison of SharePoint and Native Mode](#bkmk_featuresupport)  
  
-   [Native Mode](#bkmk_nativemode)  
  
-   [Native Mode with SharePoint Web Parts](#bkmk_nativewithwebparts)  
  
-   [SharePoint Mode](#bkmk_sharepointmode)  
  
-   [Report Process and Schedule and Delivery Process](#bkmk_reportprocessor)  
  
-   [Report Server Database](#bkmk_reportdatabase)  
  
-   [Authentication, Rendering, Data, and Delivery Extensions](#bkmk_authentication)  
  
-   [Related Tasks](#bkmk_relatedtasks)  
  
##  <a name="bkmk_overview"></a> Overview of Report Server Modes  
 Processing engines \(processors\) are the core of the report server. The processors support the integrity of the reporting system and cannot be modified or extended. Extensions are also processors, but they perform very specific functions. [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] includes one or more default extensions for every type of supported extension. You can add custom extensions to a report server. Doing so allows you to extend a report server to support features that are not supported out of the box; examples of custom functionality might include support for single sign\-on technologies, report output in application formats that are not already handled by the default rendering extensions, and report delivery to a printer or application.  
  
 A single report server instance is defined by the complete collection of processors and extensions that provide end\-to\-end processing, from the handling of the initial request to the presentation of a finished report. Through its subcomponents, the report server processes report requests and makes reports available for on\-demand access or scheduled distribution.  
  
 Functionally, a report server enables report authoring experiences, report rendering, and report delivery experiences for a variety of data sources as well as extensible authentication and authorization schemes. Additionally a report server contains report server databases that store published reports, shared data sources, shared datasets, report parts, shared schedules and subscriptions, report definition source files, model definitions, compiled reports, snapshots, parameters, and other resources. A report server also enables administration experiences for configuring the report server to process report requests, maintain snapshot histories, and manage permissions for reports, data sources, datasets, and subscriptions.  
  
 A [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report server supports two modes of deployment for report server instances:  
  
-   **Native mode**: including native mode with SharePoint Web Parts, where a report server runs as an application server that provides all processing and management capability exclusively through [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] components. You configure a native mode report server with [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] configuration manager and SQL Server Management Studio.  
  
-   **SharePoint mode**: where a report server is installed as part of a SharePoint server farm.  Deploy and configure SharePoint mode by using PowerShell commands or SharePoint content management pages.  
  
 In [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] you cannot switch a report server from one mode to the other. If you want to change the type of report server that your environment uses, you must install the desired mode of report server and then copy or move the report items or report server database from the older versioned report server to the new report server. This process is typically referred to as a ‘migration’. The steps needed to migrate depend on the mode you are migrating to and the version you are migrating from. For more information, see [Upgrade and Migrate Reporting Services](../../Topics\TopicNameNotContainA/Upgrade-and-Migrate-Reporting-Services.md)  
  
##  <a name="bkmk_featuresupport"></a> Feature Comparison of SharePoint and Native Mode  
  
|Feature or component|Native Mode|SharePoint Mode|  
|--------------------------|-----------------|---------------------|  
|**URL addressing**|Yes|URL addressing is different in SharePoint integrated mode. SharePoint URLs are used to reference reports, report models, shared data sources, and resources. The report server folder hierarchy is not used. If you have custom applications that rely on URL access as supported on a native mode report server, that functionality will no longer work when the report server is configured for SharePoint integration.<br /><br /> For more information on URL access, see [URL Access Parameter Reference](../../Topics\TopicNameNotContainA/URL-Access-Parameter-Reference.md)|  
|**Custom security extensions**|Yes|[!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] custom security extensions cannot be deployed or used on the report server. The report server includes a special\-purpose security extension that is used whenever you configure a report server to run in SharePoint integrated mode. This security extension is an internal component, and it is required for integrated operations.|  
|**Configuration Manager**|Yes|**\*\* Important \*\*** Configuration Manager cannot be used to manage a SharePoint mode report server. Instead, use SharePoint central administration.|  
|**Report Manager**|Yes|Report Manager cannot be used to manage SharePoint mode. Use the SharePoint application pages. For more information, see [Reporting Services SharePoint Service and Service Applications](../../Topics\TopicNameNotContainA/Reporting-Services-SharePoint-Service-and-Service-Applications.md).|  
|**Linked Reports**|Yes|No.|  
|**My Reports**|Yes|No|  
|**My Subscriptions** and batching methods.|Yes|No|  
|**Data Alerts**|No|Yes|  
|**Power View**|No|Yes<br /><br /> Requires Silverlight in the client browser. For more information on browser requirements, see [Browser Support for Reporting Services and Power View](../../Topics\TopicNameNotContainA/Browser-Support-for-Reporting-Services-and-Power-View.md)|  
|**.RDL reports**|Yes|Yes<br /><br /> .RDL reports can run on [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report servers in native mode or in SharePoint mode.|  
|**.RDLX reports**|No|Yes<br /><br /> Power View .RDLX reports can only run on [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report servers in SharePoint mode.|  
|**SharePoint user token credentials for the SharePoint list extension**|No|Yes|  
|**AAM zones for internet facing deployments**|No|Yes|  
|**SharePoint backup and recovery**|No|Yes|  
|**ULS log support**|No|Yes|  
  
##  <a name="bkmk_nativemode"></a> Native Mode  
 In native mode, a report server is a stand\-alone application server that provides all viewing, management, processing, and delivery of reports and report models. This is the default mode for report server instances. You can install a native mode report server that is configured during setup or you can configure it for native mode operations once setup is complete.  
  
 The following diagram shows the three\-tier architecture of a [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Native mode deployment. It shows the report server database and data sources in the data tier, the report server components in the middle tier, and the client applications and built\-in or custom tools in the presentation tier. It shows the flow of requests and data among the server components and which components send and retrieve content from a data store.  
  
 ![Reporting Services architecture](../../Images\Image\ImageNotContaina/reporting_serv_arch.gif "reporting_serv_arch")  
  
 The report server is implemented as a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows service, called the "Report Server service", that hosts a Web service, background processing, and other operations. In the Services console application, the service is listed as SQL Server Reporting Services \(MSSQLSERVER\).  
  
 Third\-party developers can create additional extensions to replace or extend the processing capability of the report server. To learn more about the programmatic interfaces available to application developers, see the [Technical Reference](../Topic/Technical%20Reference%20\(SSRS\).md).  
  
###  <a name="bkmk_nativewithwebparts"></a> Native Mode with SharePoint Web Parts  
 [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] provides two Web Parts that you can install and register on an instance of [!INCLUDE[winSPServ](../../Token\Other/winSPServ_md.md)] 2.0 or later, or [!INCLUDE[spPortalServ](../../Token\Other/spPortalServ_md.md)] 2003 or later. From a SharePoint site, you can use the Web Parts to find and view reports that are stored and processed on a report server that runs in native mode. These Web parts were introduced in earlier releases of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)].  
  
##  <a name="bkmk_sharepointmode"></a> SharePoint Mode  
 In SharePoint mode, a report server must run within a SharePoint server farm. The report server processing, rendering, and management features are represented by a SharePoint application server running the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint shared service and one or more [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] service applications. A SharePoint site provides the front\-end access to report server content and operations.  
  
 SharePoint mode requires:  
  
-   [!INCLUDE[SPF2010](../../Token\Other/SPF2010_md.md)] or [!INCLUDE[SPS2010](../../Token\Other/SPS2010_md.md)].  
  
-   An appropriate version of the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Add\-in for SharePoint 2010 Products.  
  
-   A SharePoint application server with the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] shared service installed and at least one [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] service application.  
  
 The following illustration shows a SharePoint mode [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] environment:  
  
 ![SSRS SharePoint Functional Architecture](../../Images\Image\ImageNotContaina/rs_SharePoint_architecture.gif "rs_SharePoint_architecture")  
  
||Description|  
|-|-----------------|  
|**\(1\)**|Web servers or web front\-ends \(WFE\). The [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] add\-in must be installed on each web server from which you want to utilize the web application features such as viewing reports or [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] management pages for tasks such as managing data sources or subscriptions.|  
|**\(2\)**|The add\-in installs URL and SOAP endpoints for clients to communicate with the Application servers, through the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] service proxy.|  
|**\(3\)**|Application servers running [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] shared service. Scale\-out of report processing is managed as part of the SharePoint farm and by adding the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] service to additional application servers.|  
|**\(4\)**|You can create more than one [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] service application, with different configurations including permissions, e\-mail, proxy, and subscriptions.|  
|**\(5\)**|Reports, data sources, and other items are stored in the SharePoint content databases.|  
|**\(6\)**|[!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] service applications create three databases for report server, temp, and data alerting features. Configuration settings that apply to all SSRS service applications are stored in the **RSReportserver.config** file.|  
  
##  <a name="bkmk_reportprocessor"></a> Report Process and Schedule and Delivery Process  
 The report server includes two processing engines that perform preliminary and intermediate report processing, and scheduled and delivery operations. The Report Processor retrieves the report definition or model, combines layout information with data from the data processing extension, and renders it in the requested format. The Scheduling and Delivery Process processes reports triggered from a schedule, and delivers reports to target destinations.  
  
##  <a name="bkmk_reportdatabase"></a> Report Server Database  
 The report server is a stateless server that stores all properties, objects, and metadata in a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database. Stored data includes published reports, compiled reports, report models, and the folder hierarchy that provides the addressing for all items managed by the report server. A report server database can provide internal storage for a single [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] installation or for multiple report servers that are part of a scale\-out deployment. If you configure a report server to run within a larger deployment of a SharePoint product or technology, the report server uses the SharePoint databases in addition to the report server database. For more information about data stores used in Reporting Services installation, see [Report Server Database &#40;SSRS Native Mode&#41;](../Topic/Report%20Server%20Database%20\(SSRS%20Native%20Mode\).md).  
  
##  <a name="bkmk_authentication"></a> Authentication, Rendering, Data, and Delivery Extensions  
 The report server supports the following types of extensions: authentication extensions, data processing extensions, report processing extensions, rendering extensions, and delivery extensions. A report server requires at least one authentication extension, data processing extension, and rendering extension. Delivery and custom report processing extensions are optional, but necessary if you want to support report distribution or custom controls.  
  
 Reporting Services provides default extensions so that you can use all of the server features without having to develop custom components. The following table describes the default extensions that contribute to a complete report server instance that provides ready\-to\-use functionality:  
  
|Type|Default|  
|----------|-------------|  
|Authentication|A default report server instance supports Windows Authentication, including impersonation and delegation features if they are enabled in your domain.|  
|Data processing|A default report server instance includes data processing extensions for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)], Oracle, Hyperion Essbase, SAPBW, OLE DB, Parallel Data Warehouse, and ODBC data sources.|  
|Rendering|A default report server instance includes rendering extensions for HTML, Excel, CSV, XML, Image, Word, SharePoint list, and PDF.|  
|Delivery|A default report server instance includes an e\-mail delivery extension and a file share delivery extension. If the report server is configured for SharePoint integration, you can use a delivery extension that saves reports to a SharePoint library.|  
  
> [!NOTE]  
>  Reporting Services includes a complete set of tools and applications that you can use to administer the server, create content, and make that content available to users in your organization.  
  
##  <a name="bkmk_relatedtasks"></a> Related Tasks  
 The following topics provide additional information on installing, using, and maintaining a report server:  
  
|Task|Link|  
|----------|----------|  
|Review Hardware and software requirements.|[Hardware and Software Requirements for Reporting Services in SharePoint Mode](../../Topics\TopicNameNotContainA/Hardware-and-Software-Requirements-for-Reporting-Services-in-SharePoint-Mode.md).|  
|Install [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] in SharePoint mode.|[Install Reporting Services SharePoint Mode for SharePoint 2010](assetId:///47efa72e-1735-4387-8485-f8994fb08c8c)|  
|If you are a Web developer or have expertise in creating cascading style sheets, you can modify the default styles at your own risk to change the colors, fonts, and layout of the toolbar or Report Manager. Neither the default style sheets nor instructions for modifying the style sheets are documented in this release.|[Customize Style Sheets for HTML Viewer and Report Manager](../../Topics\TopicNameNotContainA/Customize-Style-Sheets-for-HTML-Viewer-and-Report-Manager.md)|  
|Web developers who are familiar with HTML styles and Cascade Style Sheets \(CSS\) can use the information in this topic to determine which files can be modified to customize the appearance of Report Manager.|[Configure Report Manager to Pass Custom Authentication Cookies](../../Topics\TopicNameNotContainA/Configure-Report-Manager-to-Pass-Custom-Authentication-Cookies.md)|  
|Explains how to tune the memory settings for the Report Server Web service and Windows service.|[Configure Available Memory for Report Server Applications](../../Topics\TopicNameNotContainA/Configure-Available-Memory-for-Report-Server-Applications.md)|  
|Explains recommended steps to configure are report server for remote administration.|[Configure a Report Server for Remote Administration](../../Topics\TopicNameContainA/Configure-a-Report-Server-for-Remote-Administration.md)|  
|Provides instructions for configuring the availability of **My Reports** on a Native report server instance.|[Enable and Disable My Reports](../../Topics\TopicNameNotContainA/Enable-and-Disable-My-Reports.md)|  
|Provides instructions for setting up the RSClientPrint control that provides print functionality from within supported browsers. For more information on browser requirements, see [Browser Support for Reporting Services and Power View](../../Topics\TopicNameNotContainA/Browser-Support-for-Reporting-Services-and-Power-View.md).|[Enable and Disable Client-Side Printing for Reporting Services](../../Topics\TopicNameNotContainA/Enable-and-Disable-Client-Side-Printing-for-Reporting-Services.md)|  
  
## See Also  
 [Reporting Services Extensions](../Topic/Reporting%20Services%20Extensions.md)   
 [Reporting Services Tools](../../Topics\TopicNameNotContainA/Reporting-Services-Tools.md)   
 [Subscriptions and Delivery &#40;Reporting Services&#41;](../Topic/Subscriptions%20and%20Delivery%20\(Reporting%20Services\).md)   
 [Report Server Database &#40;SSRS Native Mode&#41;](../Topic/Report%20Server%20Database%20\(SSRS%20Native%20Mode\).md)   
 [Implementing a Security Extension](../Topic/Implementing%20a%20Security%20Extension.md)   
 [Implementing a Data Processing Extension](../Topic/Implementing%20a%20Data%20Processing%20Extension.md)   
 [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../Topic/Data%20Sources%20Supported%20by%20Reporting%20Services%20\(SSRS\).md)   
 [How to Administer SSRS using PowerShell \(Curated Answer\)](http://go.microsoft.com/fwlink/?LinkId=321992)  
  
  