---
title: "Moving Data Mining Objects"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bc108407-2603-4387-b930-b5bb9df78069
caps.latest.revision: 46
caps.handback.revision: 0
manager: paulettm
---
# Moving Data Mining Objects
The most common scenarios for moving data mining objects are to deploy a model from a testing or analysis environment to a production environment, or to share models with other users.  
  
 This topic describes how you can use the tools and scripting languages provided by [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)], for moving data mining objects.  
  
## Moving Data Mining Objects between Databases or Servers  
 You can move data mining objects between [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] databases or between instances of [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] in the following ways:  
  
-   Re-deploying the solution to a different database.  
  
-   Scripting individual objects.  
  
-   Backing up and then restoring a copy of the database.  
  
-   Exporting and importing structures and models.  
  
 The following section explains these options in more detail.  
  
### Deploying  
 Deploying the solution to a different server or database requires that you have the solution file that was created by using [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)].  
  
 For more information about deploying Analysis Services solutions, see [Deploy Analysis Services Projects (SSDT)](../../Topics/TopicNameNotContainA/Deploy-Analysis-Services-Projects--SSDT-.md).  
  
### Scripting  
 [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] provides several languages that you can use to script objects.  
  
-   **XMLA**: You can script objects using XMLA by right-clicking objects in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)]. To execute the script, open it in an **XMLA Query** window on the target server.  
  
-   **DMX**: You can create scripts by using templates or one of the query builders provided in [!INCLUDE[ssBIDevStudio](../../Topics/TopicNameContainA/tokens/ssBIDevStudio_md.md)] and [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)].  
  
 Note, however, that there are differences in the tasks that you can perform with each scripting language:  
  
-   Properties such as the object description and data bindings can only by created or changed by using [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] DDL languages, not by using DMX.  
  
-   Only DMX supports the import and export of mining objects.  
  
-   Only DMX supports generating PMML or importing model definitions from PMML.  
  
-   Only DMX supports training a model with application data. Moreover, the DMX INSERT INTO statement supports training a model without providing values for a key column.  
  
 For more information, see [Scripting with ASSL](assetId:///ce9aca4d-b7ad-451e-bb7f-20c2b0c03f29).  
  
### Backup and Restore  
 Backup and restore of an entire Analysis Services database is the method of choice if your data mining solution relies on OLAP objects. [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] provides backup and restore functionality that makes database backups faster and easier.  
  
 For more information about backup, see [Backup and Restore of Analysis Services Databases](../../Topics/TopicNameNotContainA/Backup-and-Restore-of-Analysis-Services-Databases.md).  
  
### Exporting and Importing  
 Exporting and then re-importing mining models and structures by using DMX statements is the easiest way to move or back up individual relational data mining objects. For more information about the DMX syntax for these operations, see the following topics:  
  
-   [EXPORT (DMX)](assetId:///97617071-e560-4080-81af-a80276fc0823)  
  
-   [IMPORT (DMX)](assetId:///c053bc88-2daf-4ebb-81d7-5a330250536d)  
  
 If you specify the INCLUDE DEPENDENCIES option, [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] will also export the definition of any required data source views, and when you import the model or structure, it will re-create the data source view on the target server. After you have finished importing the model, make sure to set the necessary mining permissions on the object.  
  
> [!NOTE]  
>  You cannot export and import OLAP models by using DMX. If your mining model is based on an OLAP cube, you must use the functionality provided by [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] for backing up and restoring an entire database, or redeploy the cube and its models.  
  
## See Also  
 [Management of Data Mining Solutions and Objects](../../Topics/TopicNameNotContainA/Management-of-Data-Mining-Solutions-and-Objects.md)