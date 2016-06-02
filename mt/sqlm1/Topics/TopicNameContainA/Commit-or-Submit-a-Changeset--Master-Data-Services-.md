---
title: Commit or Submit a Changeset (Master Data Services)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d323bbac-c8d4-4d2f-a7d2-a597e8b53e2d
---
# Commit or Submit a Changeset (Master Data Services)
  A changeset is a collection of the pending changes on the master data. If entity changes don’t require administrator approval, you can commit the changeset. If the entity changes require administrator approval, you can submit the changeset for approval.  
  
## Prerequisites  
  
-   You must have permission to access the **Explorer** functional area. For more information, see [Functional Area Permissions &#40;Master Data Services&#41;](../Topic/Functional%20Area%20Permissions%20\(Master%20Data%20Services\).md)  
  
-   If the entity changes don’t require administrator approval, you can commit the changeset only if you own the changeset and the changeset status is open.  
  
-   If the entity changes require administrator approval, you can submit the changeset for approval only if you own the changeset and the changeset status is open or rejected.  
  
## To commit a local changeset  
 The commit option is only available for local changesets on entities where the Entity Administrator has not enabled the need for approval.  
  
1.  On the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] home page, select the model and version and then click **Explorer**.  
  
2.  Click an entity on the **Entities** menu.  
  
3.  In the right pane, select **Changesets** and double click the changeset you want to commit.  
  
4.  Click **Commit**.  
  
## To submit a changeset  
 The submit option is only available on changesets on entities where the Entity Administrator has enabled the need for approval.  
  
1.  On the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] home page, select the model and version and then click **Explorer**.  
  
2.  Click an entity on the **Entities** menu.  
  
3.  In the right pane, select **Changesets** and double click the changeset you want to submit.  
  
4.  Click **Submit**.  
  
## Next Steps  
 [Approve or Reject a Changeset &#40;Master Data Services&#41;](../Topic/Approve%20or%20Reject%20a%20Changeset%20\(Master%20Data%20Services\).md)  
  
## See Also  
 [Create a Changeset &#40;Master Data Services&#41;](../Topic/Create%20a%20Changeset%20\(Master%20Data%20Services\).md)   
 [Apply and Update a Changeset &#40;Master Data Services&#41;](../Topic/Apply%20and%20Update%20a%20Changeset%20\(Master%20Data%20Services\).md)   
 [Approve or Reject a Changeset &#40;Master Data Services&#41;](../Topic/Approve%20or%20Reject%20a%20Changeset%20\(Master%20Data%20Services\).md)  
  
  