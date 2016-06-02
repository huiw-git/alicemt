---
title: Reactivate a Member or Collection (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bb4884c0-3658-4763-92d1-636804278b1c
---
# Reactivate a Member or Collection (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], you can reactivate a member that was either:  
  
-   Deactivated by the staging process.  
  
-   Deleted in the MDS [!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)].  
  
-   Deleted in the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application.  
  
 When you reactivate a member, its attributes and its membership in hierarchies and collections are restored.  
  
 You can also reactivate collections. When you do, the collection’s attributes and the members that belong to the collection are restored.  
  
 When either a collection or member is reactivated, all previous transactions are restored.  
  
## Prerequisites  
 To perform this procedure:  
  
-   In [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], you must have permission to the **Version Management** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
### To reactivate a member or collection  
  
1.  On the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] home page, click **Version Management**.  
  
2.  On the menu bar, click **Transactions**.  
  
3.  On the **Transactions** page, from the **Model** list, select a model.  
  
4.  From the **Version** list, select a version.  
  
5.  In the **Transactions** pane, click the row for the member or collection you want to reactivate. This row should have **Active** displayed in the **Prior Value** column and **De\-Activated** in the **New Value** column.  
  
6.  Click **Reverse Transaction**.  
  
7.  On the confirmation dialog box, click **OK**. A new transaction is added, showing **Active** in the **New Value** column.  
  
## See Also  
 [Delete a Member or Collection &#40;Master Data Services&#41;](../Topic/Delete%20a%20Member%20or%20Collection%20\(Master%20Data%20Services\).md)   
 [Members &#40;Master Data Services&#41;](../Topic/Members%20\(Master%20Data%20Services\).md)   
 [Collections &#40;Master Data Services&#41;](../Topic/Collections%20\(Master%20Data%20Services\).md)  
  
  