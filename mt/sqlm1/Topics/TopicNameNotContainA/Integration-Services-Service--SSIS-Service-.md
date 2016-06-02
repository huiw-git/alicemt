---
title: Integration Services Service (SSIS Service)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2c785b3b-4a0c-4df7-b5cd-23756dc87842
---
# Integration Services Service (SSIS Service)
  The topics in this section discuss the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages. This service is not required to create, save, and run Integration Services packages. [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] supports the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)].  
  
 Starting in [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] stores objects, settings, and operational data in the **SSISDB** database for projects that you’ve deployed to the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] server using the project deployment model. The [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] server, which is an instance of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Database Engine, hosts the database. For more information about the database, see [SSIS Catalog](../../Topics\TopicNameNotContainA/SSIS-Catalog.md). For more information about deploying projects to the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] server, see [Deploy Projects to Integration Services Server](../../Topics\TopicNameNotContainA/Deploy-Projects-to-Integration-Services-Server.md).  
  
## Management Capabilities  
 The [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service is a Windows service for managing [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages. The [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service is available only in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
 Running the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service provides the following management capabilities:  
  
-   Starting remote and locally stored packages  
  
-   Stopping remote and locally running packages  
  
-   Monitoring remote and locally running packages  
  
-   Importing and exporting packages  
  
-   Managing package storage  
  
-   Customizing storage folders  
  
-   Stopping running packages when the service is stopped  
  
-   Viewing the Windows Event log  
  
-   Connecting to multiple [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] servers  
  
## Startup Type for Integration Services Service  
 The [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service is installed when you install the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] component of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. By default, the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service is started and the startup type of the service is set to automatic. The service must be running to monitor the packages that are stored in the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Package Store. The [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Package Store can be either the msdb database in an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or the designated folders in the file system.  
  
 The [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service is not required if you only want to design and execute [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages. However, the service is required to list and monitor packages using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
## Related Tasks  
  
-   [Set the Properties of the Integration Services Service](../../Topics\TopicNameNotContainA/Set-the-Properties-of-the-Integration-Services-Service.md)  
  
-   [View Events for the Integration Services Service](../../Topics\TopicNameNotContainA/View-Events-for-the-Integration-Services-Service.md)  
  
  