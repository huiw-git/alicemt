---
title: Deploy Model Solutions Using XMLA
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
ms.assetid: a8cb1837-fcac-4730-bea4-a72cf94d9f7c
---
# Deploy Model Solutions Using XMLA
  In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], the **CREATE To** option of the **Script Database As** command creates an XML script of an entire [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database or one of its constituent objects. The resulting script can then be run on another computer to recreate the schema \(metadata\) of the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database. The script generates the entire database, and there is no mechanism for incrementally updating already deployed objects when using the script. After running the script and deploying the database, the newly created database must be processed before users can browse it.  
  
 For more information about the **Script Database As** command, see [Document and Script an Analysis Services Database](../../Topics\TopicNameNotContainA/Document-and-Script-an-Analysis-Services-Database.md).  
  
## Modifying Object Properties in the XML Script  
 When using the **Script Database As** command, you cannot modify specific properties \(such as the database name, data source connection strings, and security settings\) of the database objects. These properties must either be manually modified in the script after the script has been generated or modified in the deployed database after running the script.  
  
> [!IMPORTANT]  
>  The XML script will not contain the password if this is specified in either the connection string for a data source or for impersonation purposes. Since the password is required for processing purposes in this scenario, you will either need to add this manually to the XML script before it executes or add it after the XML script executes.  
  
## See Also  
 [Deploy Model Solutions Using the Deployment Wizard](../../Topics\TopicNameNotContainA/Deploy-Model-Solutions-Using-the-Deployment-Wizard.md)   
 [Synchronize Analysis Services Databases](../../Topics\TopicNameNotContainA/Synchronize-Analysis-Services-Databases.md)  
  
  