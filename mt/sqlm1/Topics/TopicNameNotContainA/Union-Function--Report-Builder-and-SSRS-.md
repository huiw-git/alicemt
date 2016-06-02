---
title: Union Function (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c87e16fe-c12a-4c9d-a9df-7a94e229fd04
---
# Union Function (Report Builder and SSRS)
  Returns the union of all the non\-null numeric values specified by the expression, evaluated in the given scope.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
## Syntax  
  
```  
  
Union(expression, scope, recursive)  
```  
  
#### Parameters  
 *expression*  
 \(**SqlGeometry** or **SqlGeography**\) The expression on which to perform the aggregation.  
  
 *scope*  
 \(**String**\) Optional. The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function. If *scope* is not specified, the current scope is used.  
  
 *recursive*  
 \(**Enumerated Type**\) Optional. **Simple** \(default\) or **RdlRecursive**. Specifies whether to perform the aggregation recursively.  
  
## Return  
 Returns a spatial object, either **SqlGeometry** or **SqlGeography**, based on the expression type. For more information about **SqlGeometry** and **SqlGeography** spatial data types, see [Spatial Data Types Overview](../../Topics\TopicNameNotContainA/Spatial-Data-Types-Overview.md).  
  
## Remarks  
 The set of data specified in the expression must have the same data type.  
  
 The value of *scope* must be a string constant and cannot be an expression. For outer aggregates or aggregates that do not specify other aggregates, *scope* must refer to the current scope or a containing scope. Dataset scopes are not supported. For aggregates of aggregates, nested aggregates can specify a child scope.  
  
 *Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:  
  
-   *Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate. For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.  
  
-   *Scope* for nested aggregates cannot be the name of a dataset.  
  
-   *Expression* must not contain **First**, **Last**, **Previous**, or **RunningValue** functions.  
  
-   *Expression* must not contain nested aggregates that specify *recursive*.  
  
 For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](../Topic/Aggregate%20Functions%20Reference%20\(Report%20Builder%20and%20SSRS\).md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Scope%20for%20Totals,%20Aggregates,%20and%20Built-in%20Collections%20\(Report%20Builder%20and%20SSRS\).md).  
  
 For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](../Topic/Creating%20Recursive%20Hierarchy%20Groups%20\(Report%20Builder%20and%20SSRS\).md).  
  
## Example  
 The following table shows examples of **SqlGeometry** expressions and **Union** result expression, shown in WKT \(Well Known Text\) format for spatial data.  
  
|Field with spatial data|Example|Union result|  
|-----------------------------|-------------|------------------|  
|\[PointLocation\]|POINT\(1 2\)<br /><br /> POINT\(3 4\)|MULTIPOINT\(\(1 2\), \(3 4\)\)|  
|\[PathDefinition\]|LINESTRING\(1 2, 3 4\)<br /><br /> LINESTRING\(5 6, 7 8\)|MULTILINESTRING\(\(7 8, 5 6\), \(3 4, 1 2\)\)|  
|\[PolygonDefinition\]|POLYGON\(\(1 2, 3 4, 5 2, 1 2\)\)<br /><br /> POLYGON\(\(\-1 2, \-3 4, \-5 2, \-1 2\)\)|MULTIPOLYGON\(\(\(1 2, 5 2, 3 4, 1 2\)\), \(\(\-5 2, \-1 2, \-3 4, \-5 2\)\)\)|  
  
```  
=Union(Fields!PointLocation.Value)  
=Union(Fields!PathDefinition.Value)  
=Union(Fields!PolygonDefinition.Value, "Group1")  
```  
  
## See Also  
 [Expression Uses in Reports &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Uses%20in%20Reports%20\(Report%20Builder%20and%20SSRS\).md)   
 [Expression Examples &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Examples%20\(Report%20Builder%20and%20SSRS\).md)   
 [Data Types in Expressions &#40;Report Builder and SSRS&#41;](../Topic/Data%20Types%20in%20Expressions%20\(Report%20Builder%20and%20SSRS\).md)   
 [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Scope%20for%20Totals,%20Aggregates,%20and%20Built-in%20Collections%20\(Report%20Builder%20and%20SSRS\).md)  
  
  