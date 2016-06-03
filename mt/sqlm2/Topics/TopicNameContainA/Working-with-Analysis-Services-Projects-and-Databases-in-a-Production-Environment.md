---
title: Working with Analysis Services Projects and Databases in a Production Environment
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c589097f-ad29-4b97-8c7e-b8a910909c1a
---
# Working with Analysis Services Projects and Databases in a Production Environment
  After you have developed and deployed your [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database from your [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project to an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance, you must decide how you wish to make changes to objects in the deployed database. Certain changes, such changes related to security roles, partitioning, and storage settings, can be made using either [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)]. Other changes can only be made using [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], either in project mode or in online mode \(such as adding attributes or user\-defined hierarchies\).  
  
 As soon as you make a change to a deployed [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database using either [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] in online mode, the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project that was used for deployment becomes out of date. If a developer makes any changes within the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project and attempts to deploy the modified project, the developer will be prompted to overwrite the entire database. If the developer overwrites the entire database, it must also be processed. This issue becomes compounded if the changes made directly to the deployed database by the production staff were not communicated to the development team because they will not understand why their changes no longer appear in the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database.  
  
 There are several ways in which you can use SQL Server [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] tools to avoid the problems inherent in this situation.  
  
-   Method 1: Whenever a change is made to a production version of an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database, use [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] to create a new [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project based on the modified version of the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database. This new [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project can be checked into the source control system as the master copy of the project. This method will work regardless of whether the change was made to the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] in online mode.  
  
-   Method 2: Only make changes to the production version of an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] in project mode. With this method, you can use options available to you in the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] Deployment Wizard to preserve changes made by [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], such as security roles and storage settings. This ensures that the design\-related settings are kept in the project file \(storage settings and security roles can be ignored\) and the online server is used for storage settings and security roles.  
  
-   Method 3: Only make changes to the production version of an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] in online mode. Since both tools are only working with the same online server, there are no possibilities of getting different version out of sync.  
  
  