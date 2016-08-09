---
title: "Set Multidimensional Database Properties (Analysis Services)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a8be5b3f-3148-448a-976c-7222705155d9
caps.latest.revision: 25
caps.handback.revision: 0
manager: mblythe
---
# Set Multidimensional Database Properties (Analysis Services)
There are a number of [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] database properties that you can configure in the [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)] database designer.  
  
 In this designer, you can perform the following types of tasks:  
  
-   If you are connected to the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] database in online mode, you can change the name of the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] database. If you are working in project mode, you can change the database name for the next deployment of the project. For more information, see [Rename a Multidimensional Database (Analysis Services)](../../Topics/TopicNameContainA/Rename-a-Multidimensional-Database--Analysis-Services-.md) and [Configure Analysis Services Project Properties (SSDT)](../../Topics/TopicNameNotContainA/Configure-Analysis-Services-Project-Properties--SSDT-.md).  
  
-   You can provide a description of the database that can be presented to users. You can also view the name of the database, but cannot change it. To change the database name, you must edit the properties of the project.  
  
-   You can provide translations for the database name and description for one or more languages. For more information, see [Cube Translations](assetId:///4e4fd6a4-d324-4508-b75a-2a57de9ab8ff), [Dimension Translations](assetId:///38fc1e05-2ac9-4816-b52b-dfd19c3a43a2), and [Translation support in Analysis Services](../../Topics/TopicNameNotContainA/Translation-support-in-Analysis-Services.md).  
  
-   You can view and modify default account type mappings. Account type mappings are used when one or more measures use the *ByAccount* aggregation function. For each account type, you can specify an alias and modify the default aggregation function associated with the account type. For more information modifying the default aggregation, see [Define Semiadditive Behavior](../../Topics/TopicNameNotContainA/Define-Semiadditive-Behavior.md).  
  
## Database Properties  
 In addition to the above, there are a number of properties of a database that you can configure in the Properties window.  
  
|Property|Description|  
|--------------|-----------------|  
|Aggregation Prefix|The common prefix that can be used for aggregation names for all of the partitions in a database. For more information, see [AggregationPrefix Element (ASSL)](assetId:///1581e0df-ae8e-41ce-9c92-f0f7cac487f2).|  
|Collation|When the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] project is deployed to an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] instance, the database will inherit from the Collation server property unless a different value is provided here.|  
|DataSourceImpersonationInfo|Specifies the default impersonation mode for all data source objects in the database. This is the mode that the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] service uses when processing objects, synchronizing servers, and executing the OpenQuery and SystemOpenSchema data mining statements.|  
|Estimated Size|Provides an estimated size of the database files on disk. If data is stored in multiple locations, this estimate will be limited to just the data files stored under the database folder.<br /><br /> **EstimatedSize** can also be used as a basis for estimating memory. Typically, memory requirements are larger than the size of data on disk due to additional data structures that are created when the database is loaded into memory.<br /><br /> To further estimate memory requirements, you can also use Task Manager to look at the Analysis Services process memory before and after processing the database and observe the memory utilized as a method for understanding the memory requirements of the database.|  
|Language|When the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] project is deployed to an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] instance, the database will inherit from the Language server property unless a different value is provided here.|  
|MasterDataSource ID|Used with remote partitions. For more information, see [Remote Partitions](assetId:///63f5d9f5-c6b6-4ceb-94fe-7b6c396d10bb).|  
  
## See Also  
 [Database Properties Dialog Box (SSAS - Multidimensional)](../../Topics/TopicNameNotContainA/Database-Properties-Dialog-Box--SSAS---Multidimensional-.md)   
 [Configure Analysis Services Project Properties (SSDT)](../../Topics/TopicNameNotContainA/Configure-Analysis-Services-Project-Properties--SSDT-.md)