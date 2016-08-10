---
title: "Create an Attribute Group (Master Data Services)"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 798c325e-e8d8-412a-b02e-118f2741d1c7
caps.latest.revision: 8
caps.handback.revision: 0
manager: jhubbard
---
# Create an Attribute Group (Master Data Services)
In [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)], create attribute groups when you want to display attributes on individual tabs in the **Explorer** grid.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **System Administration** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators (Master Data Services)](../../Topics/TopicNameNotContainA/Administrators--Master-Data-Services-.md).  
  
-   At least one attribute must exist. For more information, see [Create a Text Attribute (Master Data Services)](../../Topics/TopicNameContainA/Create-a-Text-Attribute--Master-Data-Services-.md).  
  
### To create an attribute group  
  
1.  In [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)], click **System Administration**.  
  
2.  On the **Manage Model** page, select a model from the grid and then click **Entities**.  
  
3.  On the **Manage Entity** page, from the grid, select the row for the entity that you want to create an attribute group for.  
  
4.  Click **Attribute Groups**.  
  
5.  On the Manage Attribute Groups page, do one of the following and then click **Add**.  
  
     If the attribute group is for leaf members, select **Leaf** from the **Member Types** drop-down list at the top of the page.  
  
     If the attribute group is for consolidated members, select **Consolidated** from the **Member Types** drop-down list.  
  
     If the attribute group is for collections, select **Collection** from the **Member Types** drop-down list.  
  
6.  Click **Leaf Groups**, **Consolidated Groups**, or **Collection Groups** to create an attribute group of leaf members, consolidated members, or collections respectively.  
  
7.  In the **Name** box, type a name for the attribute group. This name is displayed on the tab in **Explorer**.  
  
8.  To add an attribute, click the attribute in the **Available Attributes** box, and then click the **Add** arrow. To add all attributes, click the **Add All** arrow.  
  
9. Click the **Up** and **Down** arrows to change the left-to-right order of the attributes.  
  
10. Click users in the **Available Users** box, and then click the **Add** arrow. To add all users, click the **Add All** arrow.  
  
11. Click groups in the **Available Groups** box, and then click the **Add** arrow. To add all groups, click the **Add All** arrow.  
  
12. Click **Save**.  
  
## Next Steps  
  
-   [Make an Attribute Group Visible to Users (Master Data Services)](../../Topics/TopicNameNotContainA/Make-an-Attribute-Group-Visible-to-Users--Master-Data-Services-.md)  
  
## See Also  
 [Attribute Groups (Master Data Services)](../../Topics/TopicNameNotContainA/Attribute-Groups--Master-Data-Services-.md)   
 [Attributes (Master Data Services)](../../Topics/TopicNameNotContainA/Attributes--Master-Data-Services-.md)   
 [Change an Attribute Group Name (Master Data Services)](../../Topics/TopicNameNotContainA/Change-an-Attribute-Group-Name--Master-Data-Services-.md)   
 [Delete an Attribute Group (Master Data Services)](../../Topics/TopicNameNotContainA/Delete-an-Attribute-Group--Master-Data-Services-.md)   
 [Leaf Permissions (Master Data Services)](../../Topics/TopicNameNotContainA/Leaf-Permissions--Master-Data-Services-.md)   
 [Consolidated Permissions (Master Data Services)](assetId:///084055a3-5fd3-43f3-b620-ac6afab42a3d)