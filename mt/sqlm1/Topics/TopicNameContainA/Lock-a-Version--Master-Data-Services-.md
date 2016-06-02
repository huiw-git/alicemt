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
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], lock a version of a model to prevent changes to the model's members and their attributes.  
  
> [!NOTE]  
>  When a version is locked, super users and model administrators can continue to add, edit, and remove members. Other users with permission to the model can view members only.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
-   The version's status must be **Open**.  
  
-   You must have permission to access the Version Management functional area. For more information, see [Functional Area Permissions &#40;Master Data Services&#41;](../Topic/Functional%20Area%20Permissions%20\(Master%20Data%20Services\).md).  
  
### To lock a version  
  
1.  In [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], click **Version Management**.  
  
2.  On the **Manage Versions** page, select the row for the version that you want to lock.  
  
3.  Click **Lock**.  
  
4.  In the confirmation dialog box, click **OK**.  
  
## Next Steps  
  
-   [Validate a Version against Business Rules &#40;Master Data Services&#41;](../Topic/Validate%20a%20Version%20against%20Business%20Rules%20\(Master%20Data%20Services\).md)  
  
-   [Commit a Version &#40;Master Data Services&#41;](../Topic/Commit%20a%20Version%20\(Master%20Data%20Services\).md)  
  
## See Also  
 [Versions &#40;Master Data Services&#41;](../Topic/Versions%20\(Master%20Data%20Services\).md)   
 [Unlock a Version &#40;Master Data Services&#41;](../Topic/Unlock%20a%20Version%20\(Master%20Data%20Services\).md)  
  
  