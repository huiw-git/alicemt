---
title: Lock a Version (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7bb62a84-12d8-4b29-9b6e-6aa25410618e
---
# Lock a Version (Master Data Services)
In [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/includes/ssMDSshort_md.md)], lock a version of a model to prevent changes to the model's members and their attributes.  
  
> [!NOTE]  
>  When a version is locked, super users and model administrators can continue to add, edit, and remove members. Other users with permission to the model can view members only.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must be a model administrator. For more information, see [Administrators (Master Data Services)](../../Topics/TopicNameNotContainA/Administrators--Master-Data-Services-.md).  
  
-   The version's status must be **Open**.  
  
-   You must have permission to access the Version Management functional area. For more information, see [Functional Area Permissions (Master Data Services)](../../Topics/TopicNameNotContainA/Functional-Area-Permissions--Master-Data-Services-.md).  
  
### To lock a version  
  
1.  In [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/includes/ssMDSmdm_md.md)], click **Version Management**.  
  
2.  On the **Manage Versions** page, select the row for the version that you want to lock.  
  
3.  Click **Lock**.  
  
4.  In the confirmation dialog box, click **OK**.  
  
## Next Steps  
  
-   [Validate a Version against Business Rules (Master Data Services)](../../Topics/TopicNameContainA/Validate-a-Version-against-Business-Rules--Master-Data-Services-.md)  
  
-   [Commit a Version (Master Data Services)](../../Topics/TopicNameContainA/Commit-a-Version--Master-Data-Services-.md)  
  
## See Also  
 [Versions (Master Data Services)](../../Topics/TopicNameNotContainA/Versions--Master-Data-Services-.md)   
 [Unlock a Version (Master Data Services)](../../Topics/TopicNameContainA/Unlock-a-Version--Master-Data-Services-.md)