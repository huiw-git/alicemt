---
title: "Create a Derived Hierarchy (Master Data Services)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fec653c4-11cc-46a2-8dd8-b605341ebb40
caps.latest.revision: 8
caps.handback.revision: 0
manager: jhubbard
---
# Create a Derived Hierarchy (Master Data Services)
In [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)], create a derived hierarchy when you want a level-based hierarchy that ensures that members exist at the correct level. Derived hierarchies are based on the domain-based attribute relationships that exist in a model.  
  
> [!NOTE]  
>  If a domain-based attribute value doesn't exist for a member, the member is not included in the derived hierarchy. See [Require Attribute Values (Master Data Services)](../../Topics/TopicNameNotContainA/Require-Attribute-Values--Master-Data-Services-.md) to require a domain-based attribute value for all members.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **System Administration** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators (Master Data Services)](../../Topics/TopicNameNotContainA/Administrators--Master-Data-Services-.md).  
  
### To create a derived hierarchy  
  
1.  In [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)], click **System Administration**.  
  
2.  From the menu bar, point to **Manage** and click **Derived Hierarchies**.  
  
3.  On the **Derived Hierarchy Maintenance** page, from the **Model** list, select a model.  
  
4.  Click **Add**.  
  
5.  On the **Add Derived Hierarchy** page, in the **Derived hierarchy name** box, type a name for the hierarchy.  
  
    > [!TIP]  
    >  Use a name that describes the levels in the hierarchy, for example **Product to Subcategory to Category**.  
  
6.  Click **Save derived hierarchy**.  
  
7.  On the **Edit Derived Hierarchy** page, in the **Available Entities and Hierarchies** pane, click an entity or hierarchy and drag it to the **Drop Parent Here** in **Current Levels** pane.  
  
8.  Continue dragging entities or hierarchies until your hierarchy is complete.  
  
9. Click **Back**.  
  
## See Also  
 [Derived Hierarchies (Master Data Services)](../../Topics/TopicNameNotContainA/Derived-Hierarchies--Master-Data-Services-.md)   
 [Derived Hierarchies with Explicit Caps (Master Data Services)](../../Topics/TopicNameNotContainA/Derived-Hierarchies-with-Explicit-Caps--Master-Data-Services-.md)   
 [Domain-Based Attributes (Master Data Services)](../../Topics/TopicNameNotContainA/Domain-Based-Attributes--Master-Data-Services-.md)