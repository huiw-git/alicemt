---
title: Deploy Model Solutions Using the Deployment Wizard
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
ms.assetid: ff711e8e-971c-43ba-b479-effc034af4a4
---
# Deploy Model Solutions Using the Deployment Wizard
  The [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] Deployment Wizard uses the XML output files generated from a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project as input files. These input files are easily modifiable to customize the deployment of an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project. The generated deployment script can then either be immediately run or saved for later deployment.  
  
 You can deploy by using the wizard as discussed here. You can also automate deployment or use the Synchronize capability. If the deployed database is large, consider using partitions on target systems. You can also automate partition creation and population by using Analysis Management Objects \(AMO\).  
  
> [!IMPORTANT]  
>  Neither the XML output files nor the deployment script will contain the user id or password if these are specified in either the connection string for a data source or for impersonation purposes. Since these are required for processing purposes in this scenario, you will add this information manually. If the deployment will not include processing, you can add this connection and impersonation information as needed after deployment. If the deployment will include processing, you can either add this information within the wizard or in the deployment script after it is saved.  
  
## In This Section  
 The following topics describe how to work with the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] Deployment Wizard, the input files, and the deployment script:  
  
|Topic|Description|  
|-----------|-----------------|  
|[Running the Analysis Services Deployment Wizard](../../Topics\TopicNameNotContainA/Running-the-Analysis-Services-Deployment-Wizard.md)|Describes the various ways in which you can run the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] Deployment Wizard.|  
|[Understanding the Input Files Used to Create the Deployment Script](../../Topics\TopicNameNotContainA/Understanding-the-Input-Files-Used-to-Create-the-Deployment-Script.md)|Describes which files the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] Deployment Wizard uses as input values, what each of those files contains, and provides links to topics that describe how to modify the values in each of the input files.|  
|[Understanding the Analysis Services Deployment Script](../../Topics\TopicNameNotContainA/Understanding-the-Analysis-Services-Deployment-Script.md)|Describes what the deployment script contains and how the script runs.|  
  
## See Also  
 [Deploy Model Solutions Using XMLA](../../Topics\TopicNameNotContainA/Deploy-Model-Solutions-Using-XMLA.md)   
 [Synchronize Analysis Services Databases](../../Topics\TopicNameNotContainA/Synchronize-Analysis-Services-Databases.md)   
 [Understanding the Input Files Used to Create the Deployment Script](../../Topics\TopicNameNotContainA/Understanding-the-Input-Files-Used-to-Create-the-Deployment-Script.md)   
 [Deploy Model Solutions with the Deployment Utility](../../Topics\TopicNameNotContainA/Deploy-Model-Solutions-with-the-Deployment-Utility.md)  
  
  