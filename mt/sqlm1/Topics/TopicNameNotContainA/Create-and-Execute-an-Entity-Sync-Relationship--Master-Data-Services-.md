---
title: Create and Execute an Entity Sync Relationship (Master Data Services)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0ddceab4-d2b3-4bc1-bd9c-6b852200b414
---
# Create and Execute an Entity Sync Relationship (Master Data Services)
  Entity sync is a one\-way and repeatable synchronization between entity versions. It provides a way to share entity data between different models.  
  
## Prerequisites  
 Prerequisites to create an entity sync relationship:  
  
-   You must have permission to access the System Administration functional area. For more information, see [Functional Area Permissions &#40;Master Data Services&#41;](../Topic/Functional%20Area%20Permissions%20\(Master%20Data%20Services\).md).  
  
-   You must be a model administrator of the target model. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
-   You must have at least read access to the source entity and all its attributes and members.  
  
 Prerequisites to execute an entity sync relationship:  
  
-   You must have permission to access the System Administration functional area. For more information, see [Functional Area Permissions &#40;Master Data Services&#41;](../Topic/Functional%20Area%20Permissions%20\(Master%20Data%20Services\).md).  
  
-   You must be a model administrator of the target model. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
 Consider the following when creating an entity sync relationship.  
  
-   The source and target entities must be in different models.  
  
-   A target entity version status must not be committed.  
  
-   Once a sync relationship has been established, the target is immediately synced with the source.  
  
-   A target entity version cannot be a source entity version of another sync relationship.  
  
 Consider the following when executing an entity sync relationship.  
  
-   Only leaf members will be copied  
  
-   Domain\-based attributes will not be copied.  
  
-   Soft deleted members will not be copied.  
  
-   Sync does not generate target entity transactions\/histories.  
  
 **To create an entity sync relationship**  
  
1.  In Master Data Manager, click **System Administration**.  
  
2.  On the **Model View** page, from the menu bar, point to **Manage** and click **Entity Sync**.  
  
3.  On the **Entity Sync Maintenance** page, click **Add**. A panel shows up on the right side.  
  
4.  From the source **Model** list, select a model.  
  
5.  From the source **Version** list, select a version.  
  
6.  From the source **Entity** list, select an entity.  
  
7.  From the target **Model** list, select a model.  
  
8.  From the target **Version** list, select a version.  
  
9. Choose **Existing Entity** and select an entity from the Entity list if you want to sync an existing entity, or choose **New Entity** and enter the target entity name if you want to sync to a new entity  
  
10. Select **Sync On Demand**, or select **Auto Sync** and set a frequency.  
  
11. Click **Save**.  
  
 **To execute an entity sync relationship**  
  
1.  In Master Data Manager, click **System Administration**.  
  
2.  On the **Model View** page, from the menu bar, point to **Manage** and click **Entity Sync**.  
  
3.  On the **Entity Sync Maintenance** page, select a sync relationship in the grid.  
  
4.  Click **Execute**.  
  
## Sync Relationship Information  
 For each created sync relationship, a row with ten columns is added to the grid. The following table describes the columns.  
  
|Column|Description|  
|------------|-----------------|  
|Status|The sync relationship status.<br /><br /> When you click **Save** or execute a sync relationship, the ![Icon for updating status](../../Images\Image\ImageNotContaina/mds_StatusIcon_Updating.png "mds_StatusIcon_Updating") image displays, indicating that the sync relationship is updating.<br /><br /> If there are errors when creating, editing, or executing a sync relationship, the ![Icon for error status](../../Images\Image\ImageNotContaina/mds_StatusIcon_Error.png "mds_StatusIcon_Error") image displays.<br /><br /> Otherwise, the status is OK and the ![Icon for OK status](../../Images\Image\ImageNotContaina/mds_StatusIcon_OK.png "mds_StatusIcon_OK") image displays.|  
|Source Model|The source model name.|  
|Source Version|The source version name.|  
|Source Entity|The source entity name.|  
|Target Model|The target model name.|  
|Target Version|The target version name.|  
|Target Entity|The target entity name.|  
|Frequency|Specifies the sync relationship's frequency.|  
|Last Attempt Time|Shows the time at which the last sync attempt occurred.|  
|Last Successful Time|Shows the time at which the last successful sync attempt occurred.|  
  
 When you click an index, the following information displays.  
  
-   **Last Attempt Error**: Shows the error information about the last sync attempt.  
  
-   **Created By**: The name of the user who created the sync.  
  
-   **On**: The date and time when the sync was created.  
  
-   **Updated By**: The name of the user who last updated the sync.  
  
-   **On**: The date and time when the sync was last updated.  
  
## Next Steps  
 [Edit and Delete an Entity Sync Relationship &#40;Master Data Services&#41;](../Topic/Edit%20and%20Delete%20an%20Entity%20Sync%20Relationship%20\(Master%20Data%20Services\).md)  
  
  