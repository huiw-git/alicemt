---
title: "Create a Domain-based Attribute (MDS Add-in for Excel)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b3e30dc-8f41-4a5d-8009-ae5a4426a64b
caps.latest.revision: 7
caps.handback.revision: 0
manager: jhubbard
---
# Create a Domain-based Attribute (MDS Add-in for Excel)
In the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Topics/TopicNameContainA/tokens/ssMDSXLS_md.md)], administrators can create a domain-based attribute when they want to constrain the values in a column to a specific set of values.  
  
 The values can already be in the worksheet or they can come from an existing entity.  
  
> [!NOTE]  
>  If users type a value in the constrained column, rather than selecting from the list, errors are displayed in the **$InputStatus$** column when they publish.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **System Administration** and **Explorer** functional areas.  
  
-   You must be a model administrator. For more information, see [Administrators (Master Data Services)](../../Topics/TopicNameNotContainA/Administrators--Master-Data-Services-.md).  
  
-   The model and entity must already exist.  
  
### To perform this procedure:  
  
1.  In Excel, load the entity that contains the column (attribute) you want to constrain. For more information, see [Export Data to Excel from Master Data Services](../../Topics/TopicNameNotContainA/Export-Data-to-Excel-from-Master-Data-Services.md).  
  
2.  Click any cell in the column you want to constrain.  
  
3.  In the **Build Model** group, click **Attribute Properties**.  
  
4.  In the **Attribute Properties** dialog box, in the **Attribute type** list, choose **Constrained list (domain-based)**.  
  
5.  In the **Populate the attribute with values from** list:  
  
    -   To use values from the worksheet, choose **the selected column**. A new entity and new staging table will be created with the values from the selected column.  
  
    -   To use values from an existing entity, choose the name of the entity.  
  
6.  If you chose **the selected column** in the previous step, in the **New entity name** box, type a name for the new entity. This can be the same as the column (attribute) name.  
  
7.  Click **OK**. Each cell in the column now has a list of values for users to choose from.  
  
## Next Steps  
  
-   To add and delete values in the constrained list, load the entity that the attribute is based on. For more information on loading entities, see [Export Data to Excel from Master Data Services](../../Topics/TopicNameNotContainA/Export-Data-to-Excel-from-Master-Data-Services.md).  
  
## See Also  
 [Domain-Based Attributes (Master Data Services)](../../Topics/TopicNameNotContainA/Domain-Based-Attributes--Master-Data-Services-.md)   
 [Create an Entity (MDS Add-in for Excel)](../../Topics/TopicNameNotContainA/Create-an-Entity--MDS-Add-in-for-Excel-.md)   
 [Building a Model (MDS Add-in for Excel)](../../Topics/TopicNameContainA/Building-a-Model--MDS-Add-in-for-Excel-.md)