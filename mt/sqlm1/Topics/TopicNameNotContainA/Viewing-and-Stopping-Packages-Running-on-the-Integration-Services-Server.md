---
title: Viewing and Stopping Packages Running on the Integration Services Server
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 11bf44e6-f6b0-475f-b816-40e914dbac80
---
# Viewing and Stopping Packages Running on the Integration Services Server
  The **SSISDB** database stores execution history in internal tables that are not visible to users. However it exposes the information that you need through public views that you can query. It also provides stored procedures that you can call to perform common tasks related to packages.  
  
 Typically you manage [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] objects on the server in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. However you can also query the database views and call the stored procedures directly, or write custom code that calls the managed API. [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] and the managed API query the views and call the stored procedures to perform many of their tasks. For example, you can view the list of [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages that are currently running on the server, and request packages to stop if you have to.  
  
## Viewing the List of Running Packages  
 You can view the list of packages that are currently running on the server in the **Active Operations** dialog box. For more information, see [Active Operations Dialog Box](../../Topics\TopicNameNotContainA/Active-Operations-Dialog-Box.md).  
  
 For information about the other methods that you can use to view the list of running packages, see the following topics.  
  
 [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] access  
 To view the list of packages that are running on the server, query the view, [catalog.executions &#40;SSISDB Database&#41;](../Topic/catalog.executions%20\(SSISDB%20Database\).md) for packages that have a status of 2.  
  
 Programmatic access through the managed API  
 See the [Microsoft.SqlServer.Management.IntegrationServices](assetId:///N:Microsoft.SqlServer.Management.IntegrationServices) namespace and its classes.  
  
## Stopping a Running Package  
 You can request a running package to stop in the **Active Operations** dialog box. For more information, see [Active Operations Dialog Box](../../Topics\TopicNameNotContainA/Active-Operations-Dialog-Box.md).  
  
 For information about the other methods that you can use to stop a running package, see the following topics.  
  
 [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] access  
 To stop a package that is running on the server, call the stored procedure, [catalog.stop_operation &#40;SSISDB Database&#41;](../Topic/catalog.stop_operation%20\(SSISDB%20Database\).md).  
  
 Programmatic access through the managed API  
 See the [Microsoft.SqlServer.Management.IntegrationServices](assetId:///N:Microsoft.SqlServer.Management.IntegrationServices) namespace and its classes.  
  
## Viewing the History of Packages That Have Run  
 To view the history of packages that have run in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)], use the **All Executions** report. For more information on the **All Executions** report and other standard reports, see [Reports for the Integration Services Server](../../Topics\TopicNameNotContainA/Reports-for-the-Integration-Services-Server.md).  
  
 For information about the other methods that you can use to view the history of running packages, see the following topics.  
  
 [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] access  
 To view information about packages that have run, query the view, [catalog.executions &#40;SSISDB Database&#41;](../Topic/catalog.executions%20\(SSISDB%20Database\).md).  
  
 Programmatic access through the managed API  
 See the [Microsoft.SqlServer.Management.IntegrationServices](assetId:///N:Microsoft.SqlServer.Management.IntegrationServices) namespace and its classes.  
  
## See Also  
 [Execution of Projects and Packages](../../Topics\TopicNameNotContainA/Execution-of-Projects-and-Packages.md)   
 [Troubleshooting Reports for Package Execution](../../Topics\TopicNameNotContainA/Troubleshooting-Reports-for-Package-Execution.md)  
  
  