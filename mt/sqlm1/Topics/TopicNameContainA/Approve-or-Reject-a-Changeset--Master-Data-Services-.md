---
title: Approve or Reject a Changeset (Master Data Services)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 45bd01f9-ae15-4fc5-a2ba-eee565a26ef8
---
# Approve or Reject a Changeset (Master Data Services)
  A changeset is a collection of the pending changes on the master data. If the entity changes require administrator approval and a changeset is submitted for approval, you can review and then approve or reject the changeset.  
  
## Prerequisites  
  
-   You must have permission to access the **Explorer** functional area. For more information, see [Functional Area Permissions &#40;Master Data Services&#41;](../Topic/Functional%20Area%20Permissions%20\(Master%20Data%20Services\).md).  
  
-   You must have administrator permission for the entity.  
  
-   The entity changes must require administrator approval.  
  
-   If the changeset status is pending, you can review and then approve or reject the changeset.  
  
-   Users are not allowed to approve their own changes. If you are the entity administrator, you must assign a secondary administrator to approve your own changeset.  
  
## To approve or reject a changeset  
  
1.  On the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] home page, select the model and version and then click **Explorer**.  
  
2.  Click an entity on the **Entities** menu.  
  
3.  In the right pane, select **Changesets** and double click the changeset you want to approve or reject.  
  
4.  Click **Apply** to apply the changeset and review the pending changes.  
  
5.  Click **Reject** to reject the changeset and send it back to the owner.  
  
6.  Click **Approve** to approve the changeset. The changeset is committed automatically.  
  
## See Also  
 [Create a Changeset &#40;Master Data Services&#41;](../Topic/Create%20a%20Changeset%20\(Master%20Data%20Services\).md)   
 [Apply and Update a Changeset &#40;Master Data Services&#41;](../Topic/Apply%20and%20Update%20a%20Changeset%20\(Master%20Data%20Services\).md)   
 [Commit or Submit a Changeset &#40;Master Data Services&#41;](../Topic/Commit%20or%20Submit%20a%20Changeset%20\(Master%20Data%20Services\).md)  
  
  