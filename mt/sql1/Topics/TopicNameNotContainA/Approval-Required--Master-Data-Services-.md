---
title: "Approval Required (Master Data Services)"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b475a53d-269d-49f3-bb42-965c555f80be
caps.latest.revision: 8
caps.handback.revision: 0
manager: jhubbard
---
# Approval Required (Master Data Services)
In [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)], the administrator can set an entity to Approval Required. All the changes on this entity would require one of the entity administrators to review and approve the changes.  
  
> [!NOTE]  
>  Changes made on leaf members requires approval. The changes made on deprecated explicit hierarchies and collections  bypass the approval.  
>   
>  Changes made by the staging table process bypass the approval.  
>   
>  Changes made by a business rule bypass the approval.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the System Administration functional area  
  
-   You must be a model administrator. For more information, see [Administrators (Master Data Services)](../../Topics/TopicNameNotContainA/Administrators--Master-Data-Services-.md)  
  
-   An entity must exist. For more information, see [Create an Entity (Master Data Services)](../../Topics/TopicNameNotContainA/Create-an-Entity--Master-Data-Services-.md)  
  
## To enable Approval Required for an entity  
  
1.  In [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)], click **System Administration**.  
  
2.  On the **Manage Model** page, select a model from the grid, and then click **Entities**.  
  
3.  On the **Manage Entity** page, from the grid, select the row for the entity that you want to enable  **Approval Required** for.  
  
4.  Click **Edit**, select **Approval Required**, and then click **Save**.  
  
## See Also  
 [Changesets (Master Data Services)](../../Topics/TopicNameNotContainA/Changesets--Master-Data-Services-.md)