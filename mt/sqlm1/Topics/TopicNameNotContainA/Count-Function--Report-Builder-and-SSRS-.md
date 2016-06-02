---
title: Count Function (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b50b101-daf8-4fb0-ae04-57384755779f
---
# Count Function (Report Builder and SSRS)
  Returns a count of non\-null values specified by the expression, evaluated in the context of the given scope.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
## Syntax  
  
```  
  
Count(expression, scope, recursive)  
```  
  
#### Parameters  
 *expression*  
 \(**Variant** or **Binary**\) The expression on which to perform the aggregation, for example, `=Fields!FieldName.Value`.  
  
 *scope*  
 \(**String**\) The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function. If *scope* is not specified, the current scope is used.  
  
 *recursive*  
 \(**Enumerated Type**\) Optional. **Simple** \(default\) or **RdlRecursive**. Specifies whether to perform the aggregation recursively.  
  
## Return Type  
 Returns an **Integer**.  
  
## Remarks  
 The value of *scope* must be a string constant and cannot be an expression. For outer aggregates or aggregates that do not specify other aggregates, *scope* must refer to the current scope or a containing scope. For aggregates of aggregates, nested aggregates can specify a child scope.  
  
 *Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:  
  
-   *Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate. For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.  
  
-   *Scope* for nested aggregates cannot be the name of a dataset.  
  
-   *Expression* must not contain **First**, **Last**, **Previous**, or **RunningValue** functions.  
  
-   *Expression* must not contain nested aggregates that specify *recursive*.  
  
 For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](../Topic/Aggregate%20Functions%20Reference%20\(Report%20Builder%20and%20SSRS\).md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Scope%20for%20Totals,%20Aggregates,%20and%20Built-in%20Collections%20\(Report%20Builder%20and%20SSRS\).md).  
  
 For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](../Topic/Creating%20Recursive%20Hierarchy%20Groups%20\(Report%20Builder%20and%20SSRS\).md).  
  
 Example  
  
## Description  
 The following code example shows an expression that calculates the number of non\-null values of `Size` for the default scope and for a parent group scope. The expression is added to a cell in a row that belongs to the child group `GroupbySubcategory`. The parent group is `GroupbyCategory`. The expression displays the results for `GroupbySubcategory` \(the default scope\) and then for `GroupbyCategory` \(the parent group scope\).  
  
> [!NOTE]  
>  Expressions should not contain actual carriage returns and line breaks; these are included in the example to support documentation renderers. If you copy the following example, remove carriage returns from each line.  
  
## Code  
  
```  
="Count (Subcategory): " & Count(Fields!Size.Value) &   
"Count (Category): " & Count(Fields!Size.Value,"GroupbyCategory")  
```  
  
## See Also  
 [Expression Uses in Reports &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Uses%20in%20Reports%20\(Report%20Builder%20and%20SSRS\).md)   
 [Expression Examples &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Examples%20\(Report%20Builder%20and%20SSRS\).md)   
 [Data Types in Expressions &#40;Report Builder and SSRS&#41;](../Topic/Data%20Types%20in%20Expressions%20\(Report%20Builder%20and%20SSRS\).md)   
 [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Scope%20for%20Totals,%20Aggregates,%20and%20Built-in%20Collections%20\(Report%20Builder%20and%20SSRS\).md)  
  
  