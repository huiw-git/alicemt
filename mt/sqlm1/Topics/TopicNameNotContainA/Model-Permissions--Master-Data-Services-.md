---
title: Model Permissions (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 210f440b-2cc1-4c49-94b1-3a97e2af7bc3
---
# Model Permissions (Master Data Services)
  Model permissions apply to all entities, derived hierarchies, explicit hierarchies, and collections that exist within the model. Permissions assigned to the model can be overridden for any individual object.  
  
> [!NOTE]  
>  If a user is a model administrator, the model is displayed in all functional areas of the user interface. Otherwise, the model is displayed in the **Explorer** functional area only. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
|Permission|Description|  
|----------------|-----------------|  
|**Read**|User can read members, attributes, hierarchy memberships, or collection memberships.|  
|**Create**|User can create members, and assign attribute values during create.|  
|**Update**|User can update members, attributes, hierarchy memberships, or collection memberships.|  
|**Delete**|User can delete members|  
|**Deny**|Deny all access to the model|  
|**Admin**|Administrator permission on the model. Admin permission is only available at the model level.|  
  
 The Read, Create, Update, and Delete permissions can be combined with each other. When Create, Update and Delete permissions are assigned, the read permission will be assigned automatically.  
  
## See Also  
 [Assign Model Object Permissions &#40;Master Data Services&#41;](../Topic/Assign%20Model%20Object%20Permissions%20\(Master%20Data%20Services\).md)   
 [Model Object Permissions &#40;Master Data Services&#41;](../Topic/Model%20Object%20Permissions%20\(Master%20Data%20Services\).md)   
 [Entity Permissions &#40;Master Data Services&#41;](../Topic/Entity%20Permissions%20\(Master%20Data%20Services\).md)   
 [Collection Permissions &#40;Master Data Services&#41;](../Topic/Collection%20Permissions%20\(Master%20Data%20Services\).md)  
  
  