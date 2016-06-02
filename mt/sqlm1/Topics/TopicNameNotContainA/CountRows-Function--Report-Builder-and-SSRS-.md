---
title: CountRows Function (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5b1c403d-6afd-44c8-b5f6-5ecff2a29a45
---
# CountRows Function (Report Builder and SSRS)
  Returns the number of rows in the specified scope, including rows with null values.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
## Syntax  
  
```  
  
CountRows(scope, recursive)  
```  
  
#### Parameters  
 *scope*  
 \(**String**\) The name of a dataset, data region, or group that contains the report items to count.  
  
 *recursive*  
 \(**Enumerated Type**\) Optional. **Simple** \(default\) or **RdlRecursive**. Specifies whether to perform the aggregation recursively.  
  
## Return Type  
 Returns an **Integer**.  
  
## Remarks  
 **CountRows** counts all rows in the specified scope, including rows that have null values.  
  
 The value of *scope* cannot be an expression and must refer to the current scope or a containing scope.  
  
 For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](../Topic/Aggregate%20Functions%20Reference%20\(Report%20Builder%20and%20SSRS\).md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Scope%20for%20Totals,%20Aggregates,%20and%20Built-in%20Collections%20\(Report%20Builder%20and%20SSRS\).md).  
  
 For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](../Topic/Creating%20Recursive%20Hierarchy%20Groups%20\(Report%20Builder%20and%20SSRS\).md).  
  
## Example  
 The following code example shows an expression that calculates the number of rows in a row group named `GroupbyCategory` \(based on the expression `[Category]`\).  
  
```  
="Number of rows: " & CountRows("GroupbyCategory")  
```  
  
## See Also  
 [Expression Uses in Reports &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Uses%20in%20Reports%20\(Report%20Builder%20and%20SSRS\).md)   
 [Expression Examples &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Examples%20\(Report%20Builder%20and%20SSRS\).md)   
 [Data Types in Expressions &#40;Report Builder and SSRS&#41;](../Topic/Data%20Types%20in%20Expressions%20\(Report%20Builder%20and%20SSRS\).md)   
 [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Scope%20for%20Totals,%20Aggregates,%20and%20Built-in%20Collections%20\(Report%20Builder%20and%20SSRS\).md)  
  
  