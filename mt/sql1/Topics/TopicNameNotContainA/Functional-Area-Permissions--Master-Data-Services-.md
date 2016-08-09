---
title: "Functional Area Permissions (Master Data Services)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a80b87b3-b904-4cda-8582-0761c2617c57
caps.latest.revision: 11
caps.handback.revision: 0
manager: jhubbard
---
# Functional Area Permissions (Master Data Services)
You can assign permission to each of the functional areas of the [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)] user interface (UI). The following are the functional areas:  
  
-   **Explorer**  
  
-   **Version Management**  
  
-   **Integration Management**  
  
-   **System Administration**  
  
-   **User and Group Permissions**  
  
-   **Super user**  
  
 When you assign permission to a functional area, you are making an area of the UI visible to the user or group.  
  
 Within the **Explorer** functional area, additional permissions assigned to model objects and hierarchy members determine which data a user can access. Within all other functional areas, a user must be a model administrator to view a model and act on it. For more information, see [Administrators (Master Data Services)](../../Topics/TopicNameNotContainA/Administrators--Master-Data-Services-.md).  
  
> [!IMPORTANT]  
>  A user with Super User permissions effectively has Admin permission on all models and has all other functional permissions.  
  
 A user or group must have permission to at least one functional area and one model on the **Models** tab in order to access [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)].  
  
## See Also  
 [Assign Functional Area Permissions (Master Data Services)](../../Topics/TopicNameNotContainA/Assign-Functional-Area-Permissions--Master-Data-Services-.md)   
 [Model Object Permissions (Master Data Services)](../../Topics/TopicNameNotContainA/Model-Object-Permissions--Master-Data-Services-.md)   
 [Hierarchy Member Permissions (Master Data Services)](../../Topics/TopicNameNotContainA/Hierarchy-Member-Permissions--Master-Data-Services-.md)   
 [How Permissions Are Determined (Master Data Services)](../../Topics/TopicNameNotContainA/How-Permissions-Are-Determined--Master-Data-Services-.md)