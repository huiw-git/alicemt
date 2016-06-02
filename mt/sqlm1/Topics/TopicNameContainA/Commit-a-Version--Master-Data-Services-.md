---
title: Commit a Version (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6b967a39-b333-4b84-9e5f-4fb07e156826
---
# Commit a Version (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], commit a version of a model to prevent changes to the model's members and their attributes. Committed versions cannot be unlocked.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **Version Management** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
-   The version's status must be **Locked**. For more information, see [Lock a Version &#40;Master Data Services&#41;](../Topic/Lock%20a%20Version%20\(Master%20Data%20Services\).md).  
  
-   All members must have validated successfully.  
  
-   You must have permission to access the Version Management functional area. For more information, see [Functional Area Permissions &#40;Master Data Services&#41;](../Topic/Functional%20Area%20Permissions%20\(Master%20Data%20Services\).md).  
  
### To commit a version  
  
1.  In [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], click **Version Management**.  
  
2.  On the **Manage Versions** page, on the menu bar, click **Validate Version**.  
  
3.  On the **Validate Version** page, select the model and version you want to commit.  
  
4.  Click **Commit**.  
  
5.  In the confirmation dialog box, click **OK**.  
  
## Next Steps  
  
-   [Create a Version Flag &#40;Master Data Services&#41;](../Topic/Create%20a%20Version%20Flag%20\(Master%20Data%20Services\).md)  
  
-   [Assign a Flag to a Version &#40;Master Data Services&#41;](../Topic/Assign%20a%20Flag%20to%20a%20Version%20\(Master%20Data%20Services\).md)  
  
-   [Copy a Version &#40;Master Data Services&#41;](../Topic/Copy%20a%20Version%20\(Master%20Data%20Services\).md)  
  
## See Also  
 [Versions &#40;Master Data Services&#41;](../Topic/Versions%20\(Master%20Data%20Services\).md)  
  
  