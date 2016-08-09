---
title: "Change an Attribute Name and Data Type (Master Data Services)"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d348f238-f59d-41c7-ad20-3ccd55bfd9e5
caps.latest.revision: 10
caps.handback.revision: 0
manager: mblythe
robots: noindex,nofollow
---
# Change an Attribute Name and Data Type (Master Data Services)
In [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)], you can change the name of an attribute.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **System Administration** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators (Master Data Services)](../../Topics/TopicNameNotContainA/Administrators--Master-Data-Services-.md).  
  
### To change an attribute name and type  
  
1.  In [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)], click **System Administration**.  
  
2.  On the **Manage Model** page, select a model from the grid and then click **Entities**.  
  
3.  On the **Manage Entity** page, select the row for the entity that you want to create an attribute for.  
  
4.  Click **Attributes**.  
  
5.  On the **Manage Attributes** page, do one of the following.  
  
    -   If the attribute is for leaf members, select **Leaf** from the **Member Types** list box.  
  
    -   If the attribute is for consolidated members, select **Consolidated** from the **Member Types** list box.  
  
    -   If the attribute is for collections, select **Collection** from the **Member Types** list box.  
  
6.  Select the row for the attribute you want to edit, and then click **Edit**.  
  
7.  In the **Name** box, type the updated name of the attribute. For a list of words that should not be used as attribute names, see [Reserved Words (Master Data Services)](../../Topics/TopicNameNotContainA/Reserved-Words--Master-Data-Services-.md).  
  
8.  From the **Attribute type** list, select another type.  
  
9. Click **Save**.  
  
## See Also  
 [Create a Text Attribute (Master Data Services)](../../Topics/TopicNameContainA/Create-a-Text-Attribute--Master-Data-Services-.md)   
 [Delete an Attribute (Master Data Services)](../../Topics/TopicNameNotContainA/Delete-an-Attribute--Master-Data-Services-.md)   
 [Attributes (Master Data Services)](../../Topics/TopicNameNotContainA/Attributes--Master-Data-Services-.md)