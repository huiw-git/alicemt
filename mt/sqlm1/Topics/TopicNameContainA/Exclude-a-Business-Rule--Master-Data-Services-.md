---
title: Exclude a Business Rule (Master Data Services)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bdbc9df0-23f7-40b9-8aba-4445c1482580
---
# Exclude a Business Rule (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], exclude a business rule when you do not want to delete the rule permanently, but you do not want to validate data against it.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **System Administration** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
### To exclude a business rule  
  
1.  In [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], click **System Administration**.  
  
2.  From the menu bar, point to **Manage** and click **Business Rules**.  
  
3.  On the **Business Rules** page, from the **Model** drop\-down list, select a model.  
  
4.  From the **Entity** drop\-down list, select an entity.  
  
5.  From the **Member Types** drop\-down list, select a type of member.  
  
6.  In the grid, select the row for the business rule you want to exclude and click **Edit**.  
  
7.  Mark the **Excluded** check\-box.  
  
8.  Click **Save**.  
  
9. Click **Publish All**.  
  
10. In the confirmation dialog box, click **OK**. The value in the **Business Rule Status** column is **Excluded** and the **Excluded** column is **Yes**.  
  
## See Also  
 [Delete a Business Rule &#40;Master Data Services&#41;](../Topic/Delete%20a%20Business%20Rule%20\(Master%20Data%20Services\).md)   
 [Create and Publish a Business Rule &#40;Master Data Services&#41;](../Topic/Create%20and%20Publish%20a%20Business%20Rule%20\(Master%20Data%20Services\).md)   
 [Business Rules &#40;Master Data Services&#41;](../Topic/Business%20Rules%20\(Master%20Data%20Services\).md)  
  
  