---
title: Edit and Delete an Entity Sync Relationship (Master Data Services)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9a5e37f3-352e-45a6-b4a0-6f98f83b4bd8
---
# Edit and Delete an Entity Sync Relationship (Master Data Services)
  Entity sync is a one\-way and repeatable synchronization between entity versions. It provides a way to share entity data between different models. You can edit and delete a sync relationship that you've created.  
  
## Prerequisites  
 Prerequisites to edit an entity sync relationship.  
  
-   You must have permission to access the System Administration functional area. For more information, see [Functional Area Permissions &#40;Master Data Services&#41;](../Topic/Functional%20Area%20Permissions%20\(Master%20Data%20Services\).md).  
  
-   You must be a model administrator of the target model. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
-   You must have at least read access to the source entity and all its attributes and members.  
  
 Prerequisites to delete an entity sync relationship.  
  
-   You must have permission to access the System Administration functional area. For more information, see [Functional Area Permissions &#40;Master Data Services&#41;](../Topic/Functional%20Area%20Permissions%20\(Master%20Data%20Services\).md).  
  
-   You must be a model administrator of the target model. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
 Consider the following when editing an entity sync relationship.  
  
-   The source and target entities must be in different models.  
  
-   A target entity version status must not be committed.  
  
-   Once a sync relationship has been established, the target is immediately synced with the source.  
  
-   A target entity version cannot be a source entity version of another sync relationship.  
  
 Consider the following when executing an entity sync relationship  
  
-   Only leaf members will be copied.  
  
-   Domain\-based attributes will not be copied.  
  
-   Soft\-deleted members will not be copied.  
  
-   Sync does not generate target entity transactions\/histories.  
  
 **To edit an entity sync relationship**  
  
1.  In Master Data Manager, click **System Administration**.  
  
2.  On the **Model View** page, from the menu bar, point to **Manage** and click **Entity Sync**.  
  
3.  On the **Entity Sync Maintenance** page, select a sync relationship in the grid.  
  
4.  Click **Edit**. A panel shows up on the right side.  
  
5.  Change **Frequency**. Select **Sync On Demand**, or select **Auto Sync** and set a frequency.  
  
6.  Click **Save**.  
  
 **To delete an entity sync relationship**  
  
1.  In Master Data Manager, click **System Administration**.  
  
2.  On the **Model View** page, from the menu bar, point to **Manage** and click **Entity Sync**.  
  
3.  On the **Entity Sync Maintenance** page, select a sync relationship in the grid.  
  
4.  Click **Delete**.  
  
5.  In the confirmation dialog, click **OK**.  
  
## See Also  
 [Create and Execute an Entity Sync Relationship &#40;Master Data Services&#41;](../Topic/Create%20and%20Execute%20an%20Entity%20Sync%20Relationship%20\(Master%20Data%20Services\).md)   
 [Entity Sync Relationship &#40;Master Data Services&#41;](../Topic/Entity%20Sync%20Relationship%20\(Master%20Data%20Services\).md)  
  
  