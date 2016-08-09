---
title: "Create a Model (Master Data Services)"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9bb3b3b3-bde8-44aa-ad62-eaae21188141
caps.latest.revision: 14
caps.handback.revision: 0
manager: jhubbard
---
# Create a Model (Master Data Services)
In [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)], create a model to contain model objects.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **System Administration** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators (Master Data Services)](../../Topics/TopicNameNotContainA/Administrators--Master-Data-Services-.md).  
  
### To create a model  
  
1.  In [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)], click **System Administration**.  
  
2.  On the **Model View** page, from the menu bar, point to **Manage** and click **Models**.  
  
3.  On the **Manage Models** page, click **Add**. A panel is displayed on the right side.  
  
4.  In the **Name** box, type the name of the model.  
  
5.  (Optionally) In the **Description** field, type the model description.  
  
6.  In the **Log Retention Days** field, select one of the options for retaining log data. The default value is **System Setting**, which indicates that the value is inherited from system settings in the [!INCLUDE[ssMDScfgmgr](../../Topics/TopicNameContainA/tokens/ssMDScfgmgr_md.md)]. For more information, see [System Settings (Master Data Services)](../../Topics/TopicNameNotContainA/System-Settings--Master-Data-Services-.md).  
  
     To override the system setting and not remove transaction log data, select **NO**. To retain only today’s log data and truncate log data for all previous days, select **YES** and set the **Days** field to 0. To retain log data for a specified number of days, select **YES** and set the **Days** field to the number of days.  
  
7.  Optionally, select **Create entity with same name as model** to create an entity with the same name as the model.  
  
8.  Click **Save model**.  
  
 For each created model, a row with eight columns is added to the grid. The eight columns are:  
  
-   **Status**: The model status. When you click the **Save model** button, the ![Updating](../../Topics/TopicNameContainA/images/mds_model_status_updating.png "mds_model_status_updating") image is displayed, which indicates that the model is updating. If there are errors when creating or editing a model, the ![Error](../../Topics/TopicNameContainA/images/mds_model_status_error.png "mds_model_status_error") image is displayed. Otherwise, the status is OK and the ![OK](../../Topics/TopicNameContainA/images/mds_model_status_ok.png "mds_model_status_ok") image is displayed.  
  
-   **Name**: The model name.  
  
-   **Description**: The model description.  
  
-   **Log Retention Days**: The number of days the log is retained for the model.  
  
-   **Created By**: The username of the user who created the model.  
  
-   **Created Date and Time**: The date and time when the model was created.  
  
-   **Updated By**: The username of the user who last updated the model.  
  
-   **Updated Date and Time**: The date and time when the model was last updated.  
  
## Next Steps  
  
-   [Create an Entity (Master Data Services)](../../Topics/TopicNameNotContainA/Create-an-Entity--Master-Data-Services-.md)  
  
## See Also  
 [Models (Master Data Services)](../../Topics/TopicNameNotContainA/Models--Master-Data-Services-.md)   
 [Entities (Master Data Services)](../../Topics/TopicNameNotContainA/Entities--Master-Data-Services-.md)   
 [Delete a Model (Master Data Services)](../../Topics/TopicNameContainA/Delete-a-Model--Master-Data-Services-.md)   
 [Edit Model (Master Data Services)](../../Topics/TopicNameNotContainA/Edit-Model--Master-Data-Services-.md)   
 [Transactions (Master Data Services)](../../Topics/TopicNameNotContainA/Transactions--Master-Data-Services-.md)