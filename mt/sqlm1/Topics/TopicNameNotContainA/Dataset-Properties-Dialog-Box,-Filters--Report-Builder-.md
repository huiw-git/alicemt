---
title: Dataset Properties Dialog Box, Filters (Report Builder)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 933a6f44-4eb7-4e73-9c40-ac0fd17b23d3
robots: noindex,nofollow
---
# Dataset Properties Dialog Box, Filters (Report Builder)
  Select **Filters** on the **Dataset Properties** dialog box to create filters for the dataset.  
  
 Filters that are part of a shared dataset definition on the report server affect all reports that use the shared dataset. Additional filters for the shared dataset can be specified after it is added to a report. These filters affect only the report in which they are defined.  
  
 Filters for an embedded dataset affect only the report in which they are defined.  
  
 For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../Topic/Filter,%20Group,%20and%20Sort%20Data%20\(Report%20Builder%20and%20SSRS\).md).  
  
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
 Type or choose the expression to which you want to apply a filter. Click the Expression \(**fx**\) button to edit the expression.  
  
 **Data type**  
 Choose the data type for **Value**. When possible, choose a data type that matches the data type for **Expression**.  
  
 The values in **Expression** and **Value** must evaluate to the same data type. For example, if **Expression** is set to a field that has the data type System.Int32 and **Value** is set to 7, from the drop\-down list, choose **Integer**.  
  
 If the data type option you need is not in the drop\-down list, write an expression to convert the value to the correct data type. For more information, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](../Topic/Filter%20Equation%20Examples%20\(Report%20Builder%20and%20SSRS\).md).  
  
 **Operator**  
 Choose the operator to use to compare the expression and the value.  
  
 **Value**  
 Type the expression or value to use when evaluating the expression specified in the **Expression** box. Click the Expression \(**fx**\) button to edit the expression.  
  
## See Also  
 [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../Topic/Report%20Embedded%20Datasets%20and%20Shared%20Datasets%20\(Report%20Builder%20and%20SSRS\).md)   
 [Report Parameters &#40;Report Builder and Report Designer&#41;](../Topic/Report%20Parameters%20\(Report%20Builder%20and%20Report%20Designer\).md)   
 [Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;](../Topic/Add%20a%20Filter%20to%20a%20Dataset%20\(Report%20Builder%20and%20SSRS\).md)   
 [Expression Uses in Reports &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Uses%20in%20Reports%20\(Report%20Builder%20and%20SSRS\).md)  
  
  