---
title: Understanding the Input Files Used to Create the Deployment Script
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
ms.assetid: 20e080cd-6a0e-4591-b022-ea4cd3638e36
---
# Understanding the Input Files Used to Create the Deployment Script
  When you build a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project, [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] generates XML files for the project. [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] puts these XML files in the Output folder of the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project. By default output is out in the \\Bin folder. The following table lists the XML files that [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] creates.  
  
|XMLA file|Description|  
|---------------|-----------------|  
|\<*project name*\>.asdatabase|Contains the declarative definitions for all the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] objects in the project.|  
|\<*project name*\>.deploymenttargets|Contains the name of the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance and database in which the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] objects will be created.|  
|\<*project name*\>.configsettings|Contains environment specific settings, such as data source connection information and object storage locations. Settings in this file override settings in the \<*project name*\>.asdatabase file.|  
|\<*project name*\>.deploymentoptions|Contains deployment options, such as whether deployment is transactional and whether deployed objects should be processed after deployment.|  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] never stores passwords in its project files.  
  
## Modifying the Input Files  
 Modifying the values in the input files, or the values retrieved from the input files, makes it possible to change the deployment destination, the configuration settings, and deployment options without editing the whole \<*project name*\>.asdatabase file \(or a whole XMLA script file if you generate a script from an existing [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database\). Being able to modify individual files lets you easily create different deployment scripts for different purposes.  
  
 The following topics explain how to modify values in the various input files:  
  
-   [Specifying the Installation Target](../../Topics\TopicNameNotContainA/Specifying-the-Installation-Target.md)  
  
-   [Specifying Partition and Role Deployment Options](../../Topics\TopicNameNotContainA/Specifying-Partition-and-Role-Deployment-Options.md)  
  
-   [Specifying Configuration Settings for Solution Deployment](../../Topics\TopicNameNotContainA/Specifying-Configuration-Settings-for-Solution-Deployment.md)  
  
-   [Specifying Processing Options](../../Topics\TopicNameNotContainA/Specifying-Processing-Options.md)  
  
## See Also  
 [Running the Analysis Services Deployment Wizard](../../Topics\TopicNameNotContainA/Running-the-Analysis-Services-Deployment-Wizard.md)   
 [Understanding the Analysis Services Deployment Script](../../Topics\TopicNameNotContainA/Understanding-the-Analysis-Services-Deployment-Script.md)  
  
  