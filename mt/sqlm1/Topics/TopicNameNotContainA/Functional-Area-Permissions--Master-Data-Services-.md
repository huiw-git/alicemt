---
title: Functional Area Permissions (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a80b87b3-b904-4cda-8582-0761c2617c57
---
# Functional Area Permissions (Master Data Services)
  You can assign permission to each of the functional areas of the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] user interface \(UI\). The following are the functional areas:  
  
-   **Explorer**  
  
-   **Version Management**  
  
-   **Integration Management**  
  
-   **System Administration**  
  
-   **User and Group Permissions**  
  
-   **Super user**  
  
 When you assign permission to a functional area, you are making an area of the UI visible to the user or group.  
  
 Within the **Explorer** functional area, additional permissions assigned to model objects and hierarchy members determine which data a user can access. Within all other functional areas, a user must be a model administrator to view a model and act on it. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
> [!IMPORTANT]  
>  A user with Super User permissions effectively has Admin permission on all models and has all other functional permissions.  
  
 A user or group must have permission to at least one functional area and one model on the **Models** tab in order to access [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)].  
  
## See Also  
 [Assign Functional Area Permissions &#40;Master Data Services&#41;](../Topic/Assign%20Functional%20Area%20Permissions%20\(Master%20Data%20Services\).md)   
 [Model Object Permissions &#40;Master Data Services&#41;](../Topic/Model%20Object%20Permissions%20\(Master%20Data%20Services\).md)   
 [Hierarchy Member Permissions &#40;Master Data Services&#41;](../Topic/Hierarchy%20Member%20Permissions%20\(Master%20Data%20Services\).md)   
 [How Permissions Are Determined &#40;Master Data Services&#41;](../Topic/How%20Permissions%20Are%20Determined%20\(Master%20Data%20Services\).md)  
  
  