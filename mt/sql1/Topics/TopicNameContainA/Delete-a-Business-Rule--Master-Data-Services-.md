---
title: "Delete a Business Rule (Master Data Services)"
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
ms.assetid: b97aa4f9-569f-451d-ad62-65b81f980299
caps.latest.revision: 8
caps.handback.revision: 0
manager: jhubbard
---
# Delete a Business Rule (Master Data Services)
In [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)], delete a business rule when it is no longer needed.  
  
> [!NOTE]  
>  You can prevent data from being validated against a business rule by excluding it, rather than deleting it. For more information, see [Exclude a Business Rule (Master Data Services)](../../Topics/TopicNameContainA/Exclude-a-Business-Rule--Master-Data-Services-.md).  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **System Administration** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators (Master Data Services)](../../Topics/TopicNameNotContainA/Administrators--Master-Data-Services-.md).  
  
### To delete a business rule  
  
1.  In [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)], click **System Administration**.  
  
2.  From the menu bar, point to **Manage** and click **Business Rules**.  
  
3.  On the **Business Rules** page, from the **Model** drop-down list, select a model.  
  
4.  From the **Entity** drop-down list, select an entity.  
  
5.  From the **Member Types** drop-down list, select a type of member for the business rule to apply to.  
  
6.  In the grid, click the row for the business rule you want to delete.  
  
7.  Click **Delete**.  
  
8.  In the confirmation dialog box, click **OK**. The value in the **Business Rule State** column is **Deletion pending**.  
  
9. Click **Publish All**.  
  
10. In the confirmation dialog box, click **OK**. The deleted business rule is no longer displayed in the grid.  
  
## See Also  
 [Exclude a Business Rule (Master Data Services)](../../Topics/TopicNameContainA/Exclude-a-Business-Rule--Master-Data-Services-.md)   
 [Create and Publish a Business Rule (Master Data Services)](../../Topics/TopicNameContainA/Create-and-Publish-a-Business-Rule--Master-Data-Services-.md)   
 [Business Rules (Master Data Services)](../../Topics/TopicNameNotContainA/Business-Rules--Master-Data-Services-.md)