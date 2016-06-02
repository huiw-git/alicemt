---
title: Create a Leaf Member (Master Data Services)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0499d3b3-d508-4d43-a740-19cf53ade9f1
---
# Create a Leaf Member (Master Data Services)
  In [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], create a leaf member when you want to add master data to your system. If you want to add data in bulk, use staging tables instead. For more information, see  [Import Data from Tables &#40;Master Data Services&#41;](../Topic/Import%20Data%20from%20Tables%20\(Master%20Data%20Services\).md)  
  
 You can also use [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)] to import data.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **Explorer** functional area.  
  
-   You must have a minimum of **Create** or **Update** permission to the leaf model object for the entity you are adding a member to. The Create permission enables you to create a member and edit only the Code attribute. The Update permission enables you to update other attributes.  
  
     For more information, see [Security &#40;Master Data Services&#41;](../Topic/Security%20\(Master%20Data%20Services\).md).  
  
### To create a leaf member  
  
1.  On the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] home page, from the **Model** list, select a model.  
  
2.  If you are a user, select an open version from the **Version** list. If you are an administrator, select a version with open or locked status from the **Version** list.  
  
3.  Click **Explorer**.  
  
4.  From the menu bar, point to **Entities** and click the name of the entity you want to add a member to.  
  
5.  Click **Add member**.  
  
6.  In the **Details** pane, complete the fields.  
  
     If an attribute is domain\-based and a filter has been applied to the attribute, the list of attribute values will be constrained by the filter parent attribute.  
  
     For more information about filter parent attributes and domain\-based attributes, see [Create a Domain-Based Attribute &#40;Master Data Services&#41;](../Topic/Create%20a%20Domain-Based%20Attribute%20\(Master%20Data%20Services\).md)  
  
7.  Optional. In the **Annotations** box, type a comment about why the member was added. All users who have access to the member can view the annotation.  
  
8.  Click **OK**.  
  
## See Also  
 [Create a Consolidated Member &#40;Master Data Services&#41;](../Topic/Create%20a%20Consolidated%20Member%20\(Master%20Data%20Services\).md)   
 [Members &#40;Master Data Services&#41;](../Topic/Members%20\(Master%20Data%20Services\).md)  
  
  