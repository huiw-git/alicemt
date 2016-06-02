---
title: Create an Explicit Hierarchy (Master Data Services)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ba768393-6990-4eda-8cb0-d58cb3cfc2e2
---
# Create an Explicit Hierarchy (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], create an explicit hierarchy when you need a ragged hierarchy in which members can exist at any level. Explicit hierarchies contain members from a single entity.  
  
 After you create an explicit hierarchy, you can add members to it in the **Explorer** functional area.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **System Administration** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
-   The entity must be enabled for explicit hierarchies and collections.  
  
### To create an explicit hierarchy  
  
1.  In [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], click **System Administration**.  
  
2.  On the **Manage Model** page, select a model from the grid and then click **Entities**.  
  
3.  On the **Manage Entity** page, from the grid, select the row for the entity that you want to create an explicit hierarchy for.  
  
4.  Click **Explicit Hierarchies**.  
  
5.  On the **Manage Explicit Hierarchy** page, click **Add**.  
  
6.  In the **Name** box, type a name for the hierarchy.  
  
7.  Optionally, clear the **Mandatory hierarchy** check box to create the hierarchy as a non\-mandatory hierarchy. For more information about hierarchy types, see [Explicit Hierarchies &#40;Master Data Services&#41;](../Topic/Explicit%20Hierarchies%20\(Master%20Data%20Services\).md).  
  
8.  Click **Save**.  
  
## Grid Columns  
 For each explicit hierarchy that you create, a row with seven columns is added to the grid. The following is a description of the columns.  
  
|Name|Description|  
|----------|-----------------|  
|Status|The entity status. When you click **Save** the following image is displayed that indicates that the entity is updating.<br /><br /> ![Icon for updating status](../../Images\Image\ImageNotContaina/mds_StatusIcon_Updating.png "mds_StatusIcon_Updating")<br /><br /> If there are errors when creating or editing an entity, the following image is displayed.<br /><br /> ![Icon for error status](../../Images\Image\ImageNotContaina/mds_StatusIcon_Error.png "mds_StatusIcon_Error")<br /><br /> If the status is OK, then the following image is displayed.<br /><br /> ![Icon for OK status](../../Images\Image\ImageNotContaina/mds_StatusIcon_OK.png "mds_StatusIcon_OK")|  
|Name|The explicit hierarchy name.|  
|Is Mandatory|Specifies whether the explicit hierarchy is mandatory.|  
|Created By|The username of the user who created the explicit hierarchy.|  
|Created On|The date and time when the explicit hierarchy was created.|  
|Updated By|The username of the user who last updated the explicit hierarchy.|  
|Updated On|The date and time when the explicit hierarchy was last updated.|  
  
## Next Steps  
  
-   [Create a Consolidated Member &#40;Master Data Services&#41;](../Topic/Create%20a%20Consolidated%20Member%20\(Master%20Data%20Services\).md)  
  
-   [Move Members within a Hierarchy &#40;Master Data Services&#41;](../Topic/Move%20Members%20within%20a%20Hierarchy%20\(Master%20Data%20Services\).md)  
  
## See Also  
 [Explicit Hierarchies &#40;Master Data Services&#41;](../Topic/Explicit%20Hierarchies%20\(Master%20Data%20Services\).md)   
 [Derived Hierarchies with Explicit Caps &#40;Master Data Services&#41;](../Topic/Derived%20Hierarchies%20with%20Explicit%20Caps%20\(Master%20Data%20Services\).md)   
 [Change an Explicit Hierarchy Name &#40;Master Data Services&#41;](../Topic/Change%20an%20Explicit%20Hierarchy%20Name%20\(Master%20Data%20Services\).md)  
  
  