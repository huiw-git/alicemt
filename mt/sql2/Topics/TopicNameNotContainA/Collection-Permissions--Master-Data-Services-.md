---
title: Collection Permissions (Master Data Services)
H1: na
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 703e1bf5-4b4b-4830-8a5b-f979b09f677d
---
# Collection Permissions (Master Data Services)
  Collection permissions apply to all collections for an entity. You cannot give permission to a specific collection; permissions apply to all collections.  
  
> [!NOTE]  
>  These permissions apply to the **Explorer** functional area of the user interface only.  
  
|Permission|Description|  
|----------------|-----------------|  
|**Read**|User can read collection members and the member attributes.|  
|**Create**|User can create collection members and assign attribute values.|  
|**Update**|User can update collection members, attributes and relationships.|  
|**Delete**|User can delete collection members.|  
|**Deny**|Deny all access to the collection members.|  
  
 The Read, Create, Update, and Delete permissions can be combined. When Create, Update and Delete are assigned, the read permission is assigned automatically.  
  
## See Also  
 [Assign Model Object Permissions &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Assign-Model-Object-Permissions--Master-Data-Services-.md)   
 [Collections &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Collections--Master-Data-Services-.md)   
 [Model Object Permissions &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Model-Object-Permissions--Master-Data-Services-.md)  
  
  