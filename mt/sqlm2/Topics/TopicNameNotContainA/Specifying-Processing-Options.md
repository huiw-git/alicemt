---
title: Specifying Processing Options
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e9e50817-908e-4210-bc3d-8e2957568241
---
# Specifying Processing Options
  The [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] Deployment Wizard reads the processing options from the \<*project name*\>.deploymentoptions file. [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] creates this file when you build the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project. [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] uses the processing options specified on the **Deployment** page of *\<project name\>* **Properties Pages** dialog box to create the \<*project name*\>.deploymentoptions file.  
  
## Reviewing the Processing Options for Deployment  
 The configuration settings stored within the \<*project name*\>.deploymentoptions file are as follows:  
  
-   **Processing Method** This setting controls whether the deployed objects are processed after deployment and the type of processing that will be performed. There are three processing options:  
  
    -   Default processing \(default\)  
  
    -   Full processing  
  
    -   None  
  
-   **Writeback Table Options** If writeback is enabled in the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project, this setting defines how writeback is handled. There are three writeback table options:  
  
    -   By default, if a writeback table exists, it will be used. If a writeback table does not exist, a new writeback table will be created.  
  
    -   If a writeback table already exists, the deployment fails. If a writeback table does not exist, a new writeback table will be created.  
  
    -   Regardless of whether a writeback table already exists, a new writeback table will be created. In this case, the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] Deployment Wizard will delete any existing table and replace it with a new writeback table.  
  
-   **Transactional Deployment** This setting controls whether the deployment of metadata changes and process commands occurs in a single transaction or in separate transactions.  
  
    -   If this option is **True** \(default\), [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] deploys all metadata changes and all process commands within a single transaction.  
  
    -   If this option is **False**, [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] deploys the metadata changes in a single transaction, and deploys each processing command in its own transaction.  
  
## Modifying the Processing Options for Deployment  
 However, you may need to deploy the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project using different processing options than those stored in the \<*project name*\>.deploymentoptions file. For example, you may want to have all objects fully processed, or processed using the default processing option, or have no processing occur. If the cubes or dimensions are write\-enabled, you can specify whether a new or existing writeback table be used.  
  
 To modify the processing options used during deployment, you can either edit and rebuild the project, or change the processing options in the input file by using one of the methods as described in the following procedure.  
  
#### To change processing options after the input files have been generated  
  
-   Run the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] Deployment Wizard interactively. On the **Processing Options** page, specify the processing options for the project being deployed.  
  
     —or—  
  
-   Run the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] Deployment Wizard at the command prompt and set the wizard to run in answer file mode. For more information about answer file mode, see [Running the Analysis Services Deployment Wizard](../../Topics\TopicNameNotContainA/Running-the-Analysis-Services-Deployment-Wizard.md).  
  
     —or—  
  
-   Modify the \<*project name*\>.deploymentoptions file by using any text editor.  
  
## See Also  
 [Specifying the Installation Target](../../Topics\TopicNameNotContainA/Specifying-the-Installation-Target.md)   
 [Specifying Partition and Role Deployment Options](../../Topics\TopicNameNotContainA/Specifying-Partition-and-Role-Deployment-Options.md)   
 [Specifying Configuration Settings for Solution Deployment](../../Topics\TopicNameNotContainA/Specifying-Configuration-Settings-for-Solution-Deployment.md)  
  
  