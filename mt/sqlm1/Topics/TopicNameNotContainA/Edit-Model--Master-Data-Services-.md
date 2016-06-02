---
title: Edit Model (Master Data Services)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 399eed32-7c61-4239-9c06-996a65219518
---
# Edit Model (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], you can change the name and description of a model and indicate how many days you want to retain transaction logs.  
  
 For more information, see [Transactions &#40;Master Data Services&#41;](../Topic/Transactions%20\(Master%20Data%20Services\).md).  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **System Administration** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
### To change a model  
  
1.  In [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], click **System Administration**.  
  
2.  On the **Model View** page, from the menu bar, point to **Manage** and click **Models**.  
  
3.  On the **Manage Models** page, from the grid, select the row for the model with the name or description you want to change.  
  
4.  Click **Edit**.  
  
5.  In the **Name** box, type the updated name of the model.  
  
6.  In the **Description** field, type the updated description of the model.  
  
7.  In the **Log Retention Days** field, select one of the options for retaining log data. The default value is **System Setting**, which indicates that the value is inherited from system settings in the [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)]. For more information, see [System Settings &#40;Master Data Services&#41;](../Topic/System%20Settings%20\(Master%20Data%20Services\).md).  
  
     To override the system setting and not remove transaction log data, select **NO**. To retain only today’s log data and truncate log data for all previous days, select **YES** and set the **Days** field to 0. To retain log data for a specified number of days, select **YES** and set the **Days** field to the number of days.  
  
8.  Click **Save model**.  
  
 The **Status** column in the grid shows the status of the operation on the model. When you click the **Save model** button, the ![Updating](../../Images\Image\ImageNotContaina/mds_model_status_updating.png "mds_model_status_updating") image is displayed, which indicates that the model is updating. If there are errors when creating or editing a model, the ![Error](../../Images\Image\ImageNotContaina/mds_model_status_error.png "mds_model_status_error") image is displayed. Otherwise, the status is OK and the ![OK](../../Images\Image\ImageNotContaina/mds_model_status_ok.png "mds_model_status_ok") image is displayed.  
  
## See Also  
 [Create a Model &#40;Master Data Services&#41;](../Topic/Create%20a%20Model%20\(Master%20Data%20Services\).md)   
 [Delete a Model &#40;Master Data Services&#41;](../Topic/Delete%20a%20Model%20\(Master%20Data%20Services\).md)   
 [Models &#40;Master Data Services&#41;](../Topic/Models%20\(Master%20Data%20Services\).md)  
  
  