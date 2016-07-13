---
title: Sort in Ascending or Descending Order (Visual Database Tools)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d61cc55b-9ee8-4ecf-a32f-6459ae43910b
manager:jhubbard
translation.priority.mt: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Sort in Ascending or Descending Order (Visual Database Tools)
You can sort query results in ascending or descending order on one or more of the columns in the result set by using the **ASC** or **DESC** keywords with the **ORDER BY** clause.  
  
> [!NOTE]  
> The sort order is determined in part by the column's collation sequence. You can change the collation sequence in the [Collation Dialog Box](../content/Collation-Dialog-Box--Visual-Database-Tools-.md).  
  
The following procedure assumes that you have a query open in Query and View Designer that uses the ORDER BY clause to sort one or more columns.  
  
### To specify or change the order in which results are sorted  
  
1.  In the [Criteria pane](../content/Criteria-Pane--Visual-Database-Tools-.md), click the **Sort Type** field for the column that you want to reorder.  
  
2.  Choose **Ascending** or **Descending** to specify the sort order for the column.  
  
Notice that as you work in the Criteria pane, your query's UNION clause changes to match your most recent actions.  
  
> [!NOTE]  
> When sorting results by more than one column, specify the order in which columns are searched relative to each other by using the Sort Order column. For more information, see [Sort Multiple Columns in Queries &#40;Visual Database Tools&#41;](../content/Sort-Multiple-Columns-in-Queries--Visual-Database-Tools-.md).  
  
## See Also  
[Sort and Group Query Results &#40;Visual Database Tools&#41;](../content/Sort-and-Group-Query-Results--Visual-Database-Tools-.md)  
[Summarize Query Results &#40;Visual Database Tools&#41;](../content/Summarize-Query-Results--Visual-Database-Tools-.md)  
[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](../content/Design-Queries-and-Views-How-to-Topics--Visual-Database-Tools-.md)  
  
