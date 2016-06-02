---
title: Multidimensional Model Databases (SSAS)
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
ms.assetid: 78b2f22a-b7bd-4a2b-b6fc-0bff4d2b3168
---
# Multidimensional Model Databases (SSAS)
  An [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database is a collection of data sources, data source views, cubes, dimensions, and roles. Optionally, an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database can include structures for data mining, and custom assemblies that provide a way for you to add user\-defined functions to the database.  
  
 Cubes are the fundamental query objects in Analysis Services. When you connect to an Analysis Services database via a client application, you connect to a cube within that database. A database might contain multiple cubes if you are reusing dimensions, assemblies, roles, or mining structures across multiple contexts.  
  
 You can create and modify a [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database programmatically or by using one of these interactive methods:  
  
-   Deploy an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project from [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] to a designated instance of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]. This process creates an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database, if a database with that name does not already exist within that instance, and instantiates the designed objects within the newly created database. When working with an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database in [!INCLUDE[ssBIDevStudio](../../Token\Other/ssBIDevStudio_md.md)], changes made to objects in the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project take effect only when the project is deployed to an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance.  
  
-   Create an empty [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database within an instance of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)], by using either [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], and then connect directly to that database using [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] and create objects within it \(rather than within a project\). When working with an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database in this manner, changes made to objects take effect in the database to which you are connecting when the changed object is saved.  
  
 [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] uses integration with source control software to support multiple developers working with different objects within an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project at the same time. A developer can also interact with an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database directly, rather than through an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project, but the risk of this is that the objects in an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database can become out of sync with the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project that was used for its deployment. After deployment, you administer an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. Certain changes can also be made to an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], such as to partitions and roles, which can also cause the objects in an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database to become out of sync with the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project that was used for its deployment.  
  
## Related Tasks  
 [Attach and Detach Analysis Services Databases](../../Topics\TopicNameNotContainA/Attach-and-Detach-Analysis-Services-Databases.md)  
  
 [Backup and Restore of Analysis Services Databases](../../Topics\TopicNameNotContainA/Backup-and-Restore-of-Analysis-Services-Databases.md)  
  
 [Document and Script an Analysis Services Database](../../Topics\TopicNameNotContainA/Document-and-Script-an-Analysis-Services-Database.md)  
  
 [Modify or Delete an Analysis Services Database](../../Topics\TopicNameNotContainA/Modify-or-Delete-an-Analysis-Services-Database.md)  
  
 [Move an Analysis Services Database](../../Topics\TopicNameNotContainA/Move-an-Analysis-Services-Database.md)  
  
 [Rename a Multidimensional Database &#40;Analysis Services&#41;](../Topic/Rename%20a%20Multidimensional%20Database%20\(Analysis%20Services\).md)  
  
 [Compatibility Level of a Multidimensional Database &#40;Analysis Services&#41;](../Topic/Compatibility%20Level%20of%20a%20Multidimensional%20Database%20\(Analysis%20Services\).md)  
  
 [Set Multidimensional Database Properties &#40;Analysis Services&#41;](../Topic/Set%20Multidimensional%20Database%20Properties%20\(Analysis%20Services\).md)  
  
 [Synchronize Analysis Services Databases](../../Topics\TopicNameNotContainA/Synchronize-Analysis-Services-Databases.md)  
  
 [Switch an Analysis Services database between ReadOnly and ReadWrite modes](../../Topics\TopicNameNotContainA/Switch-an-Analysis-Services-database-between-ReadOnly-and-ReadWrite-modes.md)  
  
## See Also  
 [Connect in Online Mode to an Analysis Services Database](../../Topics\TopicNameNotContainA/Connect-in-Online-Mode-to-an-Analysis-Services-Database.md)   
 [Create an Analysis Services Project &#40;SSDT&#41;](../Topic/Create%20an%20Analysis%20Services%20Project%20\(SSDT\).md)   
 [Querying Multidimensional Data with MDX](../../Topics\TopicNameNotContainA/Querying-Multidimensional-Data-with-MDX.md)  
  
  