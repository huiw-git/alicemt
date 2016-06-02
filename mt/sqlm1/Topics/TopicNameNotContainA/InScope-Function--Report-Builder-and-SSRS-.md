---
title: InScope Function (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a8cd209a-e5d3-4dce-ab2d-f271f6c54955
---
# InScope Function (Report Builder and SSRS)
  Indicates whether the current instance of an item is in the specified scope.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
## Syntax  
  
```  
InScope(scope)  
```  
  
#### Parameters  
 *scope*  
 \(**String**\) The name of a dataset, data region, or group that specifies a scope.  
  
## Return Type  
 Returns a **Boolean**.  
  
## Remarks  
 The **InScope** function tests the scope of the current instance of a report item for membership in the scope specified by the *scope*parameter.  
  
 *Scope* cannot be an expression.  
  
 A typical use for the **InScope** function is in data regions that have dynamic scoping. For example, **InScope** can be used in a drillthrough link in a data region cells to provide a different report name and different sets of parameters depending on which cell is clicked. An example of this is as follows:  
  
-   The following expression, used as the report name in a drillthrough link, opens the `ProductDetail` report if the clicked cell is in the `Month` group, and the `ProductSummary` report if it is not.  
  
    ```  
    =Iif(InScope("Month"), "ProductDetail", "ProductSummary")  
    ```  
  
-   The following expression, used in the **Omit** property of a drillthrough report parameter, will pass the parameter to the target report only if the clicked cell is in the `Product` group.  
  
    ```  
    =Not(InScope("Product"))  
    ```  
  
 For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](../Topic/Aggregate%20Functions%20Reference%20\(Report%20Builder%20and%20SSRS\).md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Scope%20for%20Totals,%20Aggregates,%20and%20Built-in%20Collections%20\(Report%20Builder%20and%20SSRS\).md).  
  
## Example  
 The following code example indicates whether the current instance of the item is in the `Product` dataset, data region, or group scope.  
  
```  
=InScope("Product")  
```  
  
## See Also  
 [Expression Uses in Reports &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Uses%20in%20Reports%20\(Report%20Builder%20and%20SSRS\).md)   
 [Expression Examples &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Examples%20\(Report%20Builder%20and%20SSRS\).md)   
 [Data Types in Expressions &#40;Report Builder and SSRS&#41;](../Topic/Data%20Types%20in%20Expressions%20\(Report%20Builder%20and%20SSRS\).md)   
 [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Scope%20for%20Totals,%20Aggregates,%20and%20Built-in%20Collections%20\(Report%20Builder%20and%20SSRS\).md)  
  
  