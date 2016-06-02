---
title: Automatically Generate Attribute Values Other Than Code (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b82f6f81-6e9c-4918-9ea9-4ab5f5d11b15
---
# Automatically Generate Attribute Values Other Than Code (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], automatically generate values for an entity’s attribute values when you want an integer to be automatically assigned as the value each time business rules are applied.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **System Administration** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
-   A numeric attribute must exist. For more information, see [Create a Numeric Attribute &#40;Master Data Services&#41;](../Topic/Create%20a%20Numeric%20Attribute%20\(Master%20Data%20Services\).md).  
  
### To automatically generate an attribute value  
  
1.  In [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], click **System Administration**.  
  
2.  From the menu bar, point to **Manage** and click **Business Rules**.  
  
3.  On the **Business Rule Maintenance** page, from the **Model** list, select a model.  
  
4.  From the **Entity** list, select an entity.  
  
5.  From the **Member Type** list, select a type of member for the business rule to apply to.  
  
6.  From the **Attribute** list, leave the default of **All**.  
  
7.  Click **Add business rule**.  
  
8.  Click **Edit selected business rule**.  
  
9. In the **Components** pane, expand the **Actions** node.  
  
10. In the Default Value node, click **defaults to a generated value** and drag it to the **THEN** pane’s **Actions** label.  
  
11. In the **Attributes** pane, click the attribute with the value you want to generated and drag it to the **Edit Action** pane's **Select attribute** label.  
  
12. Type a value in the **Start with** and **Increment by** boxes. If members already exist, the value will be set based on the highest existing value. For example, if the highest existing value is 299 and you set **Increment by** to **1**, the next member’s value will be set to 300.  
  
13. In the **Edit Action** pane, click **Save item**.  
  
14. Click **Back**.  
  
15. Optionally, on the **Business Rules Maintenance** page, for the row that contains your business rule, double\-click a cell in the **Name**, **Description**, or **Notification** column to update the value.  
  
16. Click **Publish business rules**.  
  
17. On the confirmation dialog box, click **OK**. The rule's status changes to **Active**.  
  
## Next Steps  
  
-   [Validate Specific Members against Business Rules &#40;Master Data Services&#41;](../Topic/Validate%20Specific%20Members%20against%20Business%20Rules%20\(Master%20Data%20Services\).md)  
  
-   [Validate a Version against Business Rules &#40;Master Data Services&#41;](../Topic/Validate%20a%20Version%20against%20Business%20Rules%20\(Master%20Data%20Services\).md)  
  
## See Also  
 [Automatic Code Creation &#40;Master Data Services&#41;](../Topic/Automatic%20Code%20Creation%20\(Master%20Data%20Services\).md)   
 [Business Rules &#40;Master Data Services&#41;](../Topic/Business%20Rules%20\(Master%20Data%20Services\).md)   
 [Validation &#40;Master Data Services&#41;](../Topic/Validation%20\(Master%20Data%20Services\).md)  
  
  