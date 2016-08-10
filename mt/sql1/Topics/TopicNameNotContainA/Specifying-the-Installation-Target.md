---
title: "Specifying the Installation Target"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cb706817-6f63-4771-92c3-b70030bbce3d
caps.latest.revision: 35
caps.handback.revision: 0
manager: mblythe
---
# Specifying the Installation Target
The [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] Deployment Wizard reads the installation target information from the <*project name*>.deploymenttargets file. [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)] creates this file when you build the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] project. [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)] uses the database and server specified on the **Deployment** page of the *<project name\>* **Properties Pages** dialog box to create the <*project name*>.targets file.  
  
## Modifying the Installation Target for Deployment  
 In some situations, you may need to deploy an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] project to a database or [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] instance that is different than the one specified on the **Deployment** page. For example, you may want to deploy the project to a server for testing before deployment, and then deploy it to a production server after testing is finished. You may also want to deploy a completed and tested project to multiple production servers in a Network Load Balancing cluster, or to a staging server and a production server.  
  
 To deploy an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] project to a different database or [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] instance, you can change the installation target in the input file by using one of the methods described in the following procedure.  
  
#### To change the installation target after the input files have been generated  
  
-   Run the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] Deployment Wizard interactively. On the **Installation Target** page, specify a new destination for the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] instance and database.  
  
     —or—  
  
-   Run the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] Deployment Wizard at the command prompt and set the wizard to run in answer file mode. For more information about answer file mode, see [Running the Analysis Services Deployment Wizard](../../Topics/TopicNameNotContainA/Running-the-Analysis-Services-Deployment-Wizard.md).  
  
     —or—  
  
-   Modify the <*project name*>.deploymenttargets file by using any text editor.  
  
## See Also  
 [Specifying Partition and Role Deployment Options](../../Topics/TopicNameNotContainA/Specifying-Partition-and-Role-Deployment-Options.md)   
 [Specifying Configuration Settings for Solution Deployment](../../Topics/TopicNameNotContainA/Specifying-Configuration-Settings-for-Solution-Deployment.md)   
 [Specifying Processing Options](../../Topics/TopicNameNotContainA/Specifying-Processing-Options.md)