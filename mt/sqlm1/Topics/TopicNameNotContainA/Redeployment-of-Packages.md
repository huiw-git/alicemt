---
title: Redeployment of Packages
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 86806efb-8cf4-4f9d-9824-1152cb4c495c
---
# Redeployment of Packages
  After a project is deployed, you may need to update or extend package functionality and then redeploy the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project that contains the updated packages. As part of the process of redeploying packages, you should review the configuration properties that are included in the deployment utility. For example, you may not want to allow configuration changes after the package is redeployed.  
  
## Process for Redeployment  
 After you finish updating the packages, you rebuild the project, copy the deployment folder to the target computer, and then rerun the Package Installation Wizard.  
  
 If you update only a few packages in the project, you may not want to redeploy the entire project. To deploy only a few packages, you can create a new [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project, add the updated packages to the new project, and then build and deploy the project. Package configurations are automatically copied with the package when you add the package to a different project.  
  
## Related Tasks  
 [Deploy Packages by Using the Deployment Utility](../../Topics\TopicNameNotContainA/Deploy-Packages-by-Using-the-Deployment-Utility.md)  
  
  