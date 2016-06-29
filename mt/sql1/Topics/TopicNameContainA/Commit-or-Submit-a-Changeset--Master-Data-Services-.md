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
  
-   You must have permission to access the **Explorer** functional area. For more information, see [Functional Area Permissions &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Functional-Area-Permissions--Master-Data-Services-.md)  
  
-   If the entity changes don’t require administrator approval, you can commit the changeset only if you own the changeset and the changeset status is open.  
  
-   If the entity changes require administrator approval, you can submit the changeset for approval only if you own the changeset and the changeset status is open or rejected.  
  
## To commit a local changeset  
 The commit option is only available for local changesets on entities where the Entity Administrator has not enabled the need for approval.  
  
1.  On the [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/includes/ssMDSmdm_md.md)] home page, select the model and version and then click **Explorer**.  
  
2.  Click an entity on the **Entities** menu.  
  
3.  In the right pane, select **Changesets** and double click the changeset you want to commit.  
  
4.  Click **Commit**.  
  
## To submit a changeset  
 The submit option is only available on changesets on entities where the Entity Administrator has enabled the need for approval.  
  
1.  On the [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/includes/ssMDSmdm_md.md)] home page, select the model and version and then click **Explorer**.  
  
2.  Click an entity on the **Entities** menu.  
  
3.  In the right pane, select **Changesets** and double click the changeset you want to submit.  
  
4.  Click **Submit**.  
  
## Next Steps  
 [Approve or Reject a Changeset &#40;Master Data Services&#41;](../../Topics/TopicNameContainA/Approve-or-Reject-a-Changeset--Master-Data-Services-.md)  
  
## See Also  
 [Create a Changeset &#40;Master Data Services&#41;](../../Topics/TopicNameContainA/Create-a-Changeset--Master-Data-Services-.md)   
 [Apply and Update a Changeset &#40;Master Data Services&#41;](../../Topics/TopicNameContainA/Apply-and-Update-a-Changeset--Master-Data-Services-.md)   
 [Approve or Reject a Changeset &#40;Master Data Services&#41;](../../Topics/TopicNameContainA/Approve-or-Reject-a-Changeset--Master-Data-Services-.md)  
  
  