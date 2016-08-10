---
title: "Delete a Data Source in Solution Explorer (SSAS Multidimensional)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b45441ef-f909-4736-98b9-cc80d0acac99
caps.latest.revision: 47
caps.handback.revision: 0
manager: mblythe
---
# Delete a Data Source in Solution Explorer (SSAS Multidimensional)
You can delete a data source object to permanently remove it from an Analysis Services multidimensional model project.  
  
 In [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)], data sources provide the basis on which data source views are constructed, and data source views are in turn used to define dimensions, cubes, and mining structures in an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] project or database. Therefore, deleting a data source may invalidate other [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] objects in an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] project. You should always review the list of dependent objects that is provided before deleting the object.  
  
> [!IMPORTANT]  
>  Data sources on which other objects depend cannot be deleted from an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] database opened by [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)] in online mode. You must delete all objects in the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] database that depend on that data source before deleting the data source. For more information about online mode, see [Connect in Online Mode to an Analysis Services Database](../../Topics/TopicNameNotContainA/Connect-in-Online-Mode-to-an-Analysis-Services-Database.md).  
  
### To delete a data source  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)], open the project or connect to the database from which you want to delete a data source.  
  
2.  In **Solution Explorer**, expand the **Data Sources** folder.  
  
3.  Right-click the data source, and then click **Delete**. The **Delete Objects**  dialog box appears, showing the objects that will be invalidated if you delete the data source. Review this list carefully before clicking **OK** to delete the data source.  
  
4.  Save the project.  
  
     After deleting a data source from an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] project, you must save the modified project or you will receive an error the next time you open the project because the underlying XML file for the deleted data source will be missing when the project attempts to load the deleted data source.  
  
## See Also  
 [Data Sources in Multidimensional Models](../../Topics/TopicNameNotContainA/Data-Sources-in-Multidimensional-Models.md)   
 [Supported Data Sources (SSAS - Multidimensional)](../../Topics/TopicNameNotContainA/Supported-Data-Sources--SSAS---Multidimensional-.md)