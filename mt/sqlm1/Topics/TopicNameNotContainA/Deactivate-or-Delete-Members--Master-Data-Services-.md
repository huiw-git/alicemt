---
title: Deactivate or Delete Members (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7034280e-4eee-4f67-87a0-19d62c2271a1
robots: noindex,nofollow
---
# Deactivate or Delete Members (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], you can deactivate members or delete them completely.  
  
 Deactivating means the member can be reactivated. If you reactivate a member, its attributes and its membership in hierarchies and collections are restored. All previous transactions are intact. Deactivation transactions are visible to administrators in the **Version Management** functional area of the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application.  
  
 Deleting means purging the member from the system permanently. All transactions for the member, all relationships, and all attributes are permanently deleted.  
  
 **Notes:**  
  
-   You cannot use staging to reactivate members. You must do it manually in the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application. For more information, see [Reactivate a Member or Collection &#40;Master Data Services&#41;](../Topic/Reactivate%20a%20Member%20or%20Collection%20\(Master%20Data%20Services\).md).  
  
-   You cannot use staging to delete or deactivate collections. For more information on manually deactivating collections, see [Delete a Member or Collection &#40;Master Data Services&#41;](../Topic/Delete%20a%20Member%20or%20Collection%20\(Master%20Data%20Services\).md).  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to insert data into the stg.name\_Leaf \(for leaf members\) or stg.name\_Consolidated \(for consolidated members\) table in the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database.  
  
-   You must have permission to execute either the stg.udp\_name\_Leaf \(for leaf members\) or stg.udp\_name\_Consolidated \(for consolidated members\) stored procedure in the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database.  
  
-   The model must not have a status of **Committed**.  
  
### To deactivate or delete members  
  
-   Follow the procedure to load or update members. For more information, see [Load or Update Members &#40;Master Data Services&#41;](../Topic/Load%20or%20Update%20Members%20\(Master%20Data%20Services\).md). For the **ImportType** field, use **3** to deactivate members, and **4** to permanently delete.  
  
## See Also  
 [Reactivate a Member or Collection &#40;Master Data Services&#41;](../Topic/Reactivate%20a%20Member%20or%20Collection%20\(Master%20Data%20Services\).md)   
 [Create a Leaf Member &#40;Master Data Services&#41;](../Topic/Create%20a%20Leaf%20Member%20\(Master%20Data%20Services\).md)   
 [Delete a Member or Collection &#40;Master Data Services&#41;](../Topic/Delete%20a%20Member%20or%20Collection%20\(Master%20Data%20Services\).md)  
  
  