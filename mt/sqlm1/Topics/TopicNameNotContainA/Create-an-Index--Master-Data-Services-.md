---
title: Create an Index (Master Data Services)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d694a105-69b1-4ff6-99d3-1f408b916b81
---
# Create an Index (Master Data Services)
  Create a custom index on a list of attributes that you query frequently, to improve query performance.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the System Administration functional area. For more information, see [Functional Area Permissions &#40;Master Data Services&#41;](../Topic/Functional%20Area%20Permissions%20\(Master%20Data%20Services\).md).  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
 **To create an index**  
  
1.  In Master Data Manager, click **System Administration**.  
  
2.  On the **Manage Model** page, select a model from the grid and click then **Entities**.  
  
3.  On the **Manage Entity** page, from the **grid** , select the row for the entity that you want to create an index for.  
  
4.  Click **Indexes**.  
  
5.  In the **Name** box, type a name for the index.  
  
6.  Select **Is Unique** if you want to create a unique index. For more information about index types, see [Custom Index &#40;Master Data Services&#41;](../Topic/Custom%20Index%20\(Master%20Data%20Services\).md).  
  
7.  Click attributes in the **Available Attributes** box, and then click the **Add** arrow. To add all attributes, click the **Add All** arrow.  
  
8.  Click **Save**.  
  
 For each created index, a row with four columns is added to the grid. The following table describes the columns.  
  
|Column Name|Description|  
|-----------------|-----------------|  
|Status|The index status.<br /><br /> When you click **Save**, the ![Icon for updating status](../../Images\Image\ImageNotContaina/mds_StatusIcon_Updating.png "mds_StatusIcon_Updating") image displays indicating that the index is updating.<br /><br /> If there are errors when creating or editing an index, the ![Icon for error status](../../Images\Image\ImageNotContaina/mds_StatusIcon_Error.png "mds_StatusIcon_Error") image displays.<br /><br /> Otherwise, the status is OK, and the ![Icon for OK status](../../Images\Image\ImageNotContaina/mds_StatusIcon_OK.png "mds_StatusIcon_OK") image displays.|  
|Name|The index name.|  
|Is Unique|Specifies whether the index is unique.|  
|On Attributes|Shows the display names  of attributes that the index is defined on.|  
  
 When you click an index, the following information displays.  
  
-   **Created By**: The name of the user who created the index.  
  
-   **On**: The date and time when the index was created.  
  
-   **Updated By**: The name of the user who last updated the index.  
  
-   **On**: The date and time when the index was last updated.  
  
## Next Steps  
 [Edit and Delete an Index &#40;Master Data Services&#41;](../Topic/Edit%20and%20Delete%20an%20Index%20\(Master%20Data%20Services\).md)  
  
## See Also  
 [Custom Index &#40;Master Data Services&#41;](../Topic/Custom%20Index%20\(Master%20Data%20Services\).md)  
  
  