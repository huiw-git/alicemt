---
title: Add an Additional Report Server to a Farm (SSRS Scale-out)
H1: na
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c1a6b683-15cf-44ae-ac60-ceee63a60aaf
---
# Add an Additional Report Server to a Farm (SSRS Scale-out)
  Adding a second or more SharePoint mode report servers to your SharePoint farm can improve the performance and response time of the report server processing. If you find performance slowing down as you added more users, reports, and other applications to the report server, then adding additions report servers can improve performance. It is also recommended to add a second report server to increase the availability of report servers when there are issues with hardware or you are conducting general maintenance on individual servers in your environment. Starting with the [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/includes/ssSQL11_md.md)] release, the steps to scale-out a [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] environment in SharePoint mode follows standard SharePoint farm deployment and leverages the SharePoint load balancing features.  
  
> [!IMPORTANT]  
>  Scale-out of [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] is not supported on all editions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)]. For more information, see the [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] section of [Features Supported by the Editions of SQL Server 2016](../../Topics/TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md).  
  
> [!TIP]  
>  Starting with [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/includes/ssSQL11_md.md)] you do not use [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] Configuration Manager to add servers and scale out report servers. SharePoint products manage the scale-out of reporting services as SharePoint servers with the [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] service are added to the farm.  
  
 For information on how to scale-out native mode report servers, see [Configure a Native Mode Report Server Scale-Out Deployment &#40;SSRS Configuration Manager&#41;](../../Topics/TopicNameContainA/Configure-a-Native-Mode-Report-Server-Scale-Out-Deployment--SSRS-Configuration-Manager-.md).  
  
##  <a name="bkmk_loadbalancing"></a> Load Balancing  
 The Load balancing of [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] service applications will be managed automatically by SharePoint unless your environment has a custom or third-party load balancing solution. The default SharePoint load balancing behavior is that each [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] Service Application will be balanced across all the application servers where you have started the [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] service. To verify if the [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] service is installed and started, click **Manage services on server** in SharePoint Central Administration.  
  
##  <a name="bkmk_prerequisites"></a> Prerequisites  
  
-   You must be a local administrator to run SQL Server Setup.  
  
-   The computer must be joined to a domain.  
  
-   You need to know the name of the existing database server that is hosting the SharePoint configuration and content databases.  
  
-   The database server must be configured to allow for remote database connections.  If it is not, you will not be able to join the new server to the farm because the new server will not be able to make a connection to the SharePoint configuration databases.  
  
-   The new server will need to have the same version of SharePoint installed that the current farm servers are running. For example if the farm already has SharePoint 2013 Service Pack 1 (SP1) installed, you will need to also install SP1 on the new server before it can join the farm.  
  
##  <a name="bkmk_steps"></a> Steps  
 The steps in this topic assume that a SharePoint farm administrator is installing and configuring the server. The diagram shows a typical three tier environment and the numbered items in the diagram are described in the following list:  
  
-   (1) Multiple web front-end (WFE) servers. The WFE servers require the [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] add-in for SharePoint 2016.  
  
-   (2) A single application server running [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] and web sites, for example Central Administration. The following steps add a second application server to this tier.  
  
-   (3) Two SQL Server database servers.  
  
-   (4) Represents a software or hardware network load balancing solution (NLB)  
  
 ![Adding a Reporting Services application server](../../Topics/TopicNameContainA/media/rs_SharePointScale.gif "rs_SharePointScale")  
  
 The following steps assume that an administrator is installing and configuring the server. The server will be setup as a new application server in the farm and not used as a web front-end (WFE).  
  
|Step|Description and Link|  
|----------|--------------------------|  
|Add a SharePoint server to a farm.|You will need to intall SharePoint to deploy another Reporting Services application.<br/><br/>For SharePoint 2013, see [Add SharePoint server to a farm in SharePoint Server 2013](https://technet.microsoft.com/library/cc261752(v=office.15).aspx).<br/><br/>For SharePoint 2016, see [Add SharePoint server to a farm in SharePoint Server 2016](https://technet.microsoft.com/library/cc261752(v=office.16).aspx).|  
|Install and configure Reporting Services SharePoint mode.|Run [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/includes/ssCurrent_md.md)] installation. For more information on the installation of [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] SharePoint mode, see [Install The First Report Server in SharePoint Mode](assetId:///b29d0f45-0068-4c84-bd7e-5b8a9cd1b538)<br /><br /> If the server will only be used as an application server and the server will not be used as a WFE, you do not need to select **Reporting Services add-in for SharePoint products**.<br /><br /> 1) On the **Setup Role** page, select **SQL Server Feature Installation**<br /><br /> 2) On the **Feature Selection** page, select **Reporting Services - SharePoint**<br /><br /> 3) On the **Reporting Services Configuration**  page verify the **Install Only** option is selected for **Reporting Services SharePoint Mode**.|  
|Verify that Reporting Services is operational.|1) In SharePoint Central Administration, click **Manage servers in this farm** in the **System Settings** group.<br /><br /> 2) Verify the service **SQL Server Reporting Services Service**.<br /><br />For more information, see [Verify a Reporting Services Installation](../../Topics/TopicNameContainA/Verify-a-Reporting-Services-Installation.md)|  
  
##  <a name="bkmk_additional"></a> Additional Configuration  
 You can optimize individual [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] servers in a scaled out deployment to perform background processing only so they do not compete for resources with interactive report execution. Background processing includes schedules, subscriptions, and data alerts.  
  
 To change the behavior of individual report servers, set **<IsWebServiceEnable\>** to false in the **RSreportServer.config** configuration file.  
  
 By default reports servers are configured with <IsWebServiceEnable\> set to TRUE. When all servers are configured for TRUE, interactive and background will be load balanced across all nodes in the farm.  
  
 If you configure all report servers with <IsWebServiceEnable\> set to False, you will see an error message similar to the following when you try to use [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] features:  
  
      The Reporting Services Web Service is not enabled. Configure at least one instance of the Reporting Services SharePoint Service to have <IsWebServiceEnable> set to true. 
 
 For more information, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](../../Topics/TopicNameContainA/Modify-a-Reporting-Services-Configuration-File--RSreportserver.config-.md)  
  
## See Also  
[Add SharePoint server to a farm in SharePoint Server 2016](https://technet.microsoft.com/library/cc261752(v=office.16).aspx)  
[Add SharePoint server to a farm in SharePoint Server 2013](https://technet.microsoft.com/library/cc261752(v=office.15).aspx)
  
  