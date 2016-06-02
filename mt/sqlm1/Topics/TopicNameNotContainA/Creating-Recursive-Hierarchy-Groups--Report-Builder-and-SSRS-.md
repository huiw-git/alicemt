---
title: Creating Recursive Hierarchy Groups (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 06eccab6-4089-46e8-a84f-5bf3bbe0c23b
---
# Creating Recursive Hierarchy Groups (Report Builder and SSRS)
  To display recursive data where the relationship between parent and child is represented by fields in the dataset, you can set the data region group expression based on the child field and set the Parent property based on the parent field.  
  
 Displaying hierarchical data is a common use for recursive hierarchy groups, for example, employees in an organizational chart. The dataset includes a list of employees and the managers, where the manager names also appear in the list of employees.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
## Creating Recursive Hierarchies  
 To build a recursive hierarchy in a tablix data region, you must set the group expression to the field that specifies the child data and the Parent property of the group to the field that specifies the parent data. For example, for a dataset that includes fields for employee ID and manager ID where employees report to managers, set the group expression to employee ID and the Parent property to manager ID.  
  
 A group that is defined as a recursive hierarchy \(that is, a group that uses the Parent property\) can have only one group expression. You can use the **Level** function in text box padding to indent employee names based on their level in the hierarchy.  
  
 For more information, see [Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;](../Topic/Add%20or%20Delete%20a%20Group%20in%20a%20Data%20Region%20\(Report%20Builder%20and%20SSRS\).md) and  [Create a Recursive Hierarchy Group &#40;Report Builder and SSRS&#41;](../Topic/Create%20a%20Recursive%20Hierarchy%20Group%20\(Report%20Builder%20and%20SSRS\).md).  
  
### Aggregate Functions that support Recursion  
 You can use Reporting Services aggregate functions that accept the parameter *Recursive* to calculate summary data for a recursive hierarchy. The following functions accept **Recursive** as a parameter: [Sum](../Topic/Sum%20Function%20\(Report%20Builder%20and%20SSRS\).md), [Avg](../Topic/Avg%20Function%20\(Report%20Builder%20and%20SSRS\).md), [Count](../Topic/Count%20Function%20\(Report%20Builder%20and%20SSRS\).md), [CountDistinct](../Topic/CountDistinct%20Function%20\(Report%20Builder%20and%20SSRS\).md), [CountRows](../Topic/CountRows%20Function%20\(Report%20Builder%20and%20SSRS\).md), [Max](../Topic/Max%20Function%20\(Report%20Builder%20and%20SSRS\).md), [Min](../Topic/Min%20Function%20\(Report%20Builder%20and%20SSRS\).md), [StDev](../Topic/StDev%20Function%20\(Report%20Builder%20and%20SSRS\).md), [StDevP](../Topic/StDevP%20Function%20\(Report%20Builder%20and%20SSRS\).md), [Sum](../Topic/Sum%20Function%20\(Report%20Builder%20and%20SSRS\).md), [Var](../Topic/Var%20Function%20\(Report%20Builder%20and%20SSRS\).md), and [VarP](../Topic/VarP%20Function%20\(Report%20Builder%20and%20SSRS\).md). For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](../Topic/Aggregate%20Functions%20Reference%20\(Report%20Builder%20and%20SSRS\).md).  
  
## See Also  
 [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](../Topic/Tables,%20Matrices,%20and%20Lists%20\(Report%20Builder%20and%20SSRS\).md)   
 [Tablix Data Region &#40;Report Builder and SSRS&#41;](../Topic/Tablix%20Data%20Region%20\(Report%20Builder%20and%20SSRS\).md)   
 [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](../Topic/Aggregate%20Functions%20Reference%20\(Report%20Builder%20and%20SSRS\).md)   
 [Tables &#40;Report Builder  and SSRS&#41;](../Topic/Tables%20\(Report%20Builder%20%20and%20SSRS\).md)   
 [Matrices &#40;Report Builder and SSRS&#41;](../Topic/Matrices%20\(Report%20Builder%20and%20SSRS\).md)   
 [Lists &#40;Report Builder and SSRS&#41;](../Topic/Lists%20\(Report%20Builder%20and%20SSRS\).md)   
 [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](../Topic/Tables,%20Matrices,%20and%20Lists%20\(Report%20Builder%20and%20SSRS\).md)  
  
  