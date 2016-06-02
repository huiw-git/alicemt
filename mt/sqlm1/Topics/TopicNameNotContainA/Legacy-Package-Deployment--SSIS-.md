---
title: Legacy Package Deployment (SSIS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0f5fc7be-e37e-4ecd-ba99-697c8ae3436f
---
# Legacy Package Deployment (SSIS)
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] includes tools and wizards that make it simple to deploy packages from the development computer to the production server or to other computers.  
  
 There are four steps in the package deployment process:  
  
1.  The first optional step is optional and involves creating package configurations that update properties of package elements at run time. The configurations are automatically included when you deploy the packages.  
  
2.  The second step is to build the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project to create a package deployment utility. The deployment utility for the project contains the packages that you want to deploy  
  
3.  The third step is to copy the deployment folder that was created when you built the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] project to the target computer.  
  
4.  The fourth step is to run, on the target computer, the Package Installation Wizard to install the packages to the file system or to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
## Related Tasks  
 For information about how to create a deployment utility, see [Create a Deployment Utility](../../Topics\TopicNameContainA/Create-a-Deployment-Utility.md).  
  
 For information about how to deploy packages using the deployment utility, see [Deploy Packages by Using the Deployment Utility](../../Topics\TopicNameNotContainA/Deploy-Packages-by-Using-the-Deployment-Utility.md).  
  
 For information about how to create package configurations, see [Create Package Configurations](../../Topics\TopicNameNotContainA/Create-Package-Configurations.md).  
  
  