---
title: Overview: Exporting Data (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8b74409a-ea70-45f8-84c7-da6905e4901a
---
# Overview: Exporting Data (Master Data Services)
  This article introduces the types of subscription view formats and how to determine when views need to be edited due to changes to model objects.  
  
 You create a subscription view to export [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/includes/ssMDSshort_md.md)] data to a subscribing system such as [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)]. You  use the subscribing system to view the data in the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/includes/ssMDSshort_md.md)] database.  For information on how to create the subscription view, see [Create a Subscription View to Export Data &#40;Master Data Services&#41;](../../Topics/TopicNameContainA/Create-a-Subscription-View-to-Export-Data--Master-Data-Services-.md)  
  
 For more information about views, see [Views](../../Topics/TopicNameNotContainA/Views.md).  
  
## Subscription View Formats  
 When you create a view in [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/includes/ssMDSmdm_md.md)], you choose from a set of standard view formats that [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/includes/ssMDSshort_md.md)] provides. You can use these formats to create views that show:  
  
-   All leaf members and their attributes.  
  
-   All consolidated members and their attributes.  
  
-   All collections and their attributes.  
  
-   The members explicitly added to a collection.  
  
-   The members in a derived hierarchy, in either a parent child or level format.  
  
-   The members in all explicit hierarchies for an entity, in either a parent child or level format.  
  
## Subscription Views Can Become Out-of-Date  
 After you create a subscription view for an entity or hierarchy, changes to the associated model objects are not automatically reflected in the view. You might need to regenerate a subscription view in [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/includes/ssMDSmdm_md.md)] to reflect changes to model objects. The **Changed** column on the **Export** page is updated to **True** when model objects change. **True** indicates that you should edit the subscription view and save it, which regenerates the view.  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Create a subscription view of your master data.|[Create a Subscription View to Export Data &#40;Master Data Services&#41;](../../Topics/TopicNameContainA/Create-a-Subscription-View-to-Export-Data--Master-Data-Services-.md)|  
|Delete an existing subscription view.|[Delete a Subscription View &#40;Master Data Services&#41;](../../Topics/TopicNameContainA/Delete-a-Subscription-View--Master-Data-Services-.md)|  
  
## Related Content  
  
-   [Subscription View Formats &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Subscription-View-Formats--Master-Data-Services-.md)  
  
-   [Views](../../Topics/TopicNameNotContainA/Views.md)  
  
  