---
title: "Filters page, Chart Dialog Boxes (Report Builder and SSRS)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fab97b2f-d53f-42f2-900c-c159653d89ed
caps.latest.revision: 16
caps.handback.revision: 0
manager: mblythe
---
# Filters page, Chart Dialog Boxes (Report Builder and SSRS)
Click **Filters** in the:  
  
-   **Category Group Properties** dialog box to filter data points in a series that has been grouped by category.  
  
-   **Chart Properties** dialog box to define filtering options for the chart.  
  
-   **Series Group Properties** dialog box to limit the number of series in the selected group.  
  
## Options  
 **Add**  
 Click to add a new filter clause to the list.  
  
 **Delete**  
 Click to delete the selected filter clause from the list.  
  
 **Up arrow**  
 Click to move the selected filter up in the list.  
  
 **Down arrow**  
 Click to move the selected filter down in the list.  
  
 **Expression**  
 Type or choose the expression to which you want to apply a filter. Click the Expression (**fx**) button to edit the expression.  
  
 **Data type**  
 Choose the data type for **Value**. When possible, choose a data type that matches the data type for **Expression**.  
  
 The values in **Expression** and **Value** must evaluate to the same data type. For example, if **Expression** is set to a field that has the data type System.Int32 and **Value** is set to 7, from the drop-down list, choose **Integer**.  
  
 If the data type option you need is not in the drop-down list, write an expression to convert the value to the correct data type. For more information, see [Filter Equation Examples (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Filter-Equation-Examples--Report-Builder-and-SSRS-.md).  
  
 **Operator**  
 Choose the operator to use to compare the expression and the value.  
  
 **Value**  
 Type the expression or value against which to evaluate the expression in **Expression**.  
  
## See Also  
 [Add Dataset Filters, Data Region Filters, and Group Filters (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Add-Dataset-Filters--Data-Region-Filters--and-Group-Filters--Report-Builder-and-SSRS-.md)   
 [Expression Examples (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Expression-Examples--Report-Builder-and-SSRS-.md)   
 [Expressions (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Expressions--Report-Builder-and-SSRS-.md)   
 [Filter, Group, and Sort Data (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Filter--Group--and-Sort-Data--Report-Builder-and-SSRS-.md)