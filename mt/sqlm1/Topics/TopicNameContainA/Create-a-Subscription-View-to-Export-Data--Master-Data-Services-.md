---
title: Create a Subscription View to Export Data (Master Data Services)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a5e28961-af16-414a-9845-d2e06aac5214
---
# Create a Subscription View to Export Data (Master Data Services)
  Create a subscription view to export Master Data Services data to subscribing systems. You're creating a view of your data in the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **Integration Management** functional area. For more information, see [Functional Area Permissions &#40;Master Data Services&#41;](../Topic/Functional%20Area%20Permissions%20\(Master%20Data%20Services\).md).  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
### To create and edit a subscription view  
  
1.  In [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], click **Integration Management**.  
  
2.  From the menu bar, click **Create Views**.  
  
3.  On the **Subscription Views** page, click **Add** to create a view or click **Edit** to edit a view. A panel displays on the right side.  
  
4.  In the **Create Subscription View** pane, in the **Name** box, type a name for the view.  
  
     In the **Edit Subscription View** pane, in the **Name** box, type the updated name for the view.  
  
5.  From the **Model** list, select a model.  
  
6.  Select **Include soft\-deleted members**, to include soft\-deleted members in the view.  
  
7.  Select either **Version** or **Version Flag** in **Version Options**, and then select from the corresponding list.  
  
    > [!TIP]  
    >  Create a subscription view based on a version flag. When you lock a version, you can reassign the flag to an open version without updating the subscription view.  
  
8.  Select either **Entity** or **Derived hierarchy** in the **Data Sources** option, and then select from the corresponding list.  
  
9. From the **Format** list, select a subscription view format.  
  
10. If you chose **Explicit levels** or **Derived levels** from the **Format** list, type the number of levels in the hierarchy to include in the view.  
  
11. Click **Save**.  
  
## View Information  
 For each created view, a row with ten columns is added to the grid. The following table describes the columns.  
  
|Column|Description|  
|------------|-----------------|  
|Status|The view status.<br /><br /> When you click **Save**, the ![Icon for updating status](../../Images\Image\ImageNotContaina/mds_StatusIcon_Updating.png "mds_StatusIcon_Updating") image displays, indicating that the view is updating.<br /><br /> If there are errors when creating or editing a view, the ![Icon for error status](../../Images\Image\ImageNotContaina/mds_StatusIcon_Error.png "mds_StatusIcon_Error") image displays.<br /><br /> Otherwise, the status is OK and the ![Icon for OK status](../../Images\Image\ImageNotContaina/mds_StatusIcon_OK.png "mds_StatusIcon_OK") image displays.|  
|Name|The subscription view name.|  
|Model|The model name.|  
|Version|The version name.|  
|Version Flag|The version flag name.|  
|Derived Hierarchy|The derived hierarchy name.|  
|Entity|The entity name.|  
|Format|Specifies the type of the data in the view.|  
|Level|Specifies the number of levels in the view, which is only used for Explicit level or Derived level view formats|  
|Include delete members|Indicates whether soft\-deleted members are included in the view.|  
  
 When you click a view, the following information displays.  
  
-   **Created By**: The name of the user who created the view.  
  
-   **On**: The date and time when the view was created.  
  
-   **Updated By**: The name of the user who last updated the view.  
  
-   **On**: The date and time when the view was last updated.  
  
## See Also  
 [Overview: Exporting Data &#40;Master Data Services&#41;](../Topic/Overview:%20Exporting%20Data%20\(Master%20Data%20Services\).md)   
 [Delete a Subscription View &#40;Master Data Services&#41;](../Topic/Delete%20a%20Subscription%20View%20\(Master%20Data%20Services\).md)   
 [Create a Version Flag &#40;Master Data Services&#41;](../Topic/Create%20a%20Version%20Flag%20\(Master%20Data%20Services\).md)  
  
  