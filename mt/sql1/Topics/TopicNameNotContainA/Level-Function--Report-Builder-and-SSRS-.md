---
title: "Level Function (Report Builder and SSRS)"
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
ms.assetid: 41235402-bb9e-4cb7-b91e-431e77db19cf
caps.latest.revision: 8
caps.handback.revision: 0
manager: mblythe
---
# Level Function (Report Builder and SSRS)
Returns the current level of depth in a recursive hierarchy.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Topics/TopicNameContainA/tokens/ssRBRDDup_md.md)]  
  
## Syntax  
  
```  
  
Level(scope)  
```  
  
#### Parameters  
 *scope*  
 (**String**) (Optional). The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function. If *scope* is not specified, the current scope is used.  
  
## Return Type  
 Returns an **Integer**. If *scope* specifies a dataset or data region, or specifies a nonrecursive grouping (that is, a grouping with no **Parent** element), **Level** returns 0. If *scope* is omitted, it returns the level of the current scope.  
  
## Remarks  
 The value returned by the **Level** function is zero based; that is, the first level in a hierarchy is 0.  
  
 The **Level** function can be used to provide indentation in a recursive hierarchy, such as an employee list.  
  
 For more information about recursive hierarchies, see [Creating Recursive Hierarchy Groups (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Creating-Recursive-Hierarchy-Groups--Report-Builder-and-SSRS-.md).  
  
## Example  
 The following code example provides the level of row in the Employees group:  
  
```  
=Level("Employees")  
```  
  
## See Also  
 [Expression Uses in Reports (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Expression-Uses-in-Reports--Report-Builder-and-SSRS-.md)   
 [Expression Examples (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Expression-Examples--Report-Builder-and-SSRS-.md)   
 [Data Types in Expressions (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Data-Types-in-Expressions--Report-Builder-and-SSRS-.md)   
 [Expression Scope for Totals, Aggregates, and Built-in Collections (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Expression-Scope-for-Totals--Aggregates--and-Built-in-Collections--Report-Builder-and-SSRS-.md)