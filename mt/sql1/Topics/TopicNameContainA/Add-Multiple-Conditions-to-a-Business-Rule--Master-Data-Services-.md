---
title: "Add Multiple Conditions to a Business Rule (Master Data Services)"
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
ms.assetid: 5f0f6958-6cf2-444b-bdcd-05b887637a0b
caps.latest.revision: 10
caps.handback.revision: 0
manager: jhubbard
---
# Add Multiple Conditions to a Business Rule (Master Data Services)
In [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)], add multiple **AND** or **OR** conditions to a business rule when you want a more complex rule.  
  
> [!NOTE]  
>  If you create a business rule that uses the **OR** operator, consider creating a separate rule for each conditional statement that can be evaluated independently. You can then exclude rules as needed, providing more flexibility and easier troubleshooting.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **System Administration** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators (Master Data Services)](../../Topics/TopicNameNotContainA/Administrators--Master-Data-Services-.md).  
  
-   A business rule must exist. For more information, see [Create and Publish a Business Rule (Master Data Services)](../../Topics/TopicNameContainA/Create-and-Publish-a-Business-Rule--Master-Data-Services-.md).  
  
### To add multiple conditions to a business rule  
  
1.  In [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)], click **System Administration**.  
  
2.  From the menu bar, point to **Manage** and click **Business Rules**.  
  
3.  On the **Business Rules/** page, from the **Model** drop-down list, select a model.  
  
4.  From the **Entity** drop-down list, select an entity.  
  
5.  From the **Member Types** drop-down list, select a type of member.  
  
6.  Click the row for the business rule you want to edit.  
  
7.  Click **Edit**.  
  
8.  Under the **If** block, on the left side from the logical operator drop-down list select **AND/OR/ NOT**.  
  
9. Click **Add**. A panel will be displayed.  
  
10. From the **Attribute** drop-down list, select an attribute.  
  
11. From the **Operator** drop-down list, select a condition.  
  
12. Complete any required fields.  
  
13. Click **Save**. A new row will be added to the **If** grid.  
  
14. Optionally, to add more conditions, complete steps 8-13.  
  
    > [!TIP]  
    >  To delete a condition, select the condition and right-click on it and click **Delete**.  
  
    > [!TIP]  
    >  You can select multiple conditions and right-click to group them inside a logical operator, or to ungroup conditions inside a specific logical operator.  
  
## See Also  
 [Business Rules (Master Data Services)](../../Topics/TopicNameNotContainA/Business-Rules--Master-Data-Services-.md)   
 [Change a Business Rule Name (Master Data Services)](../../Topics/TopicNameContainA/Change-a-Business-Rule-Name--Master-Data-Services-.md)   
 [Configure Business Rules to Send Notifications (Master Data Services)](../../Topics/TopicNameNotContainA/Configure-Business-Rules-to-Send-Notifications--Master-Data-Services-.md)