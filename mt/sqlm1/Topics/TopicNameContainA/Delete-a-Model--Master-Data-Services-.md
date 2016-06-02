---
title: Delete a Model (Master Data Services)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f0ad3cc4-aed7-47c8-94bc-2971fe9fe871
---
# Delete a Model (Master Data Services)
  Delete a model to remove the model and all of its data from [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)].  
  
> [!NOTE]  
>  When you complete this procedure, all objects and all data from all versions of the model will be permanently deleted.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **System Administration** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
### To delete a model  
  
1.  In [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], click **System Administration**.  
  
2.  On the **Model View** page, from the menu bar, point to **Manage** and click **Models**.  
  
3.  On the **Manage Models** page, from the grid, select the row for the model that you want to delete.  
  
4.  Click **Delete**.  
  
5.  In the confirmation dialog box, click **OK**.  
  
6.  In the additional confirmation dialog box, click **OK**.  
  
 The **Status** column in the grid shows the status of the operation on the model. When you click the **Save model** button, the ![Updating](../../Images\Image\ImageNotContaina/mds_model_status_updating.png "mds_model_status_updating") image is displayed, which indicates that the model is updating. If there are errors when creating or editing a model, the ![Error](../../Images\Image\ImageNotContaina/mds_model_status_error.png "mds_model_status_error") image is displayed. Otherwise, the status is OK and the ![OK](../../Images\Image\ImageNotContaina/mds_model_status_ok.png "mds_model_status_ok") image is displayed.  
  
## See Also  
 [Models &#40;Master Data Services&#41;](../Topic/Models%20\(Master%20Data%20Services\).md)   
 [Create a Model &#40;Master Data Services&#41;](../Topic/Create%20a%20Model%20\(Master%20Data%20Services\).md)  
  
  