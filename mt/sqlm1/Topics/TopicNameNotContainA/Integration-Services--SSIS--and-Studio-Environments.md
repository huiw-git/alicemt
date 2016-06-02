---
title: Integration Services (SSIS) and Studio Environments
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4eb73e65-d9f3-4ac6-a408-abfa85afc537
---
# Integration Services (SSIS) and Studio Environments
  [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] includes two studios for working with [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)]:  
  
-   [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] for developing the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages that a business solution requires. [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] provides the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project in which you create packages.  
  
-   [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] for managing packages in a production environment.  
  
## SQL Server Data Tools  
 Working in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], you can perform the following tasks:  
  
-   Run the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard to create basic packages that copy data from a source to a destination.  
  
-   Create packages that include complex control flow, data flow, event\-driven logic, and logging.  
  
-   Test and debug packages by using the troubleshooting and monitoring features in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, and the debugging features in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)].  
  
-   Create configurations that update the properties of packages and package objects at run time.  
  
-   Create a deployment utility that can install packages and their dependencies on other computers.  
  
-   Save copies of packages to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] msdb database, the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Package Store, and the file system.  
  
 For more information about [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], see [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686.aspx).  
  
## SQL Server Management Studio  
 [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] provides the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service that you use to manage packages, monitor running packages, and determine impact and data lineage for [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] objects.  
  
 Working in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], you can perform the following tasks:  
  
-   Create folders to organize packages in a way that is meaningful to your organization.  
  
-   Run packages that are stored on the local computer by using the Execute Package utility.  
  
-   Run the Execute Package utility to generate a command line to use when you run the **dtexec** command prompt utility \(dtexec.exe\).  
  
-   Import and export packages to and from the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] msdb database, the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Package Store, and the file system.  
  
-   View data lineage and impact information for supported [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] objects that are deployed to the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] server and supported [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] objects.  
  
  