---
title: "Dataset Properties Dialog Box, Filters (Report Builder)"
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
ms.assetid: 933a6f44-4eb7-4e73-9c40-ac0fd17b23d3
caps.latest.revision: 15
manager: mblythe
robots: noindex,nofollow
---
# Dataset Properties Dialog Box, Filters (Report Builder)
Select **Filters** on the **Dataset Properties** dialog box to create filters for the dataset.  
  
 Filters that are part of a shared dataset definition on the report server affect all reports that use the shared dataset. Additional filters for the shared dataset can be specified after it is added to a report. These filters affect only the report in which they are defined.  
  
 Filters for an embedded dataset affect only the report in which they are defined.  
  
 For more information, see [Filter, Group, and Sort Data (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Filter--Group--and-Sort-Data--Report-Builder-and-SSRS-.md).  
  
## Options  
 **Add**  
 Add a new filter clause to the list.  
  
 **Delete**  
 Delete the selected filter clause from the list.  
  
 **Up arrow**  
 Move the selected filter up in the list.  
  
 **Down arrow**  
 Move the selected filter down in the list  
  
 **Expression**  
 Type or choose the expression to which you want to apply a filter. Click the Expression (**fx**) button to edit the expression.  
  
 **Data type**  
 Choose the data type for **Value**. When possible, choose a data type that matches the data type for **Expression**.  
  
 The values in **Expression** and **Value** must evaluate to the same data type. For example, if **Expression** is set to a field that has the data type System.Int32 and **Value** is set to 7, from the drop-down list, choose **Integer**.  
  
 If the data type option you need is not in the drop-down list, write an expression to convert the value to the correct data type. For more information, see [Filter Equation Examples (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Filter-Equation-Examples--Report-Builder-and-SSRS-.md).  
  
 **Operator**  
 Choose the operator to use to compare the expression and the value.  
  
 **Value**  
 Type the expression or value to use when evaluating the expression specified in the **Expression** box. Click the Expression (**fx**) button to edit the expression.  
  
## See Also  
 [Report Embedded Datasets and Shared Datasets (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Report-Embedded-Datasets-and-Shared-Datasets--Report-Builder-and-SSRS-.md)   
 [Report Parameters (Report Builder and Report Designer)](../../Topics/TopicNameNotContainA/Report-Parameters--Report-Builder-and-Report-Designer-.md)   
 [Add a Filter to a Dataset (Report Builder and SSRS)](../../Topics/TopicNameContainA/Add-a-Filter-to-a-Dataset--Report-Builder-and-SSRS-.md)   
 [Expression Uses in Reports (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Expression-Uses-in-Reports--Report-Builder-and-SSRS-.md)