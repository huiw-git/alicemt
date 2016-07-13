---
title: Summarize or Aggregate Values Using Custom Expressions (Visual Database Tools)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 34130ac1-0106-4766-b324-acb0b7bb6f6e
manager: jhubbard
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
# Summarize or Aggregate Values Using Custom Expressions (Visual Database Tools)
In addition to using aggregate functions to aggregate data, you can create custom expressions to produce aggregate values. You can use custom expressions in place of aggregate functions anywhere in an aggregate query.  
  
For example, in the `titles` table you might want to create a query that shows not just the average price, but what the average price would be if it were discounted.  
  
You cannot include an expression that is based on calculations involving only individual rows in the table; the expression must be based on an aggregate value, because only the aggregate values are available at the time the expression is calculated.  
  
### To specify a custom expression for a summary value  
  
1.  Specify the groups for your query. For details, see [Group Rows in Query Results &#40;Visual Database Tools&#41;](../content/Group-Rows-in-Query-Results--Visual-Database-Tools-.md).  
  
2.  Move to a blank row of the Criteria pane, and then type the expression in the **Columns** column.  
  
    The [Query and View Designer](../content/Query-and-View-Designer-Tools--Visual-Database-Tools-.md) automatically assigns a column alias to the expression to create a useful column heading in query output. For more details, see [Create Column Aliases &#40;Visual Database Tools&#41;](../content/Create-Column-Aliases--Visual-Database-Tools-.md).  
  
3.  In the **Group By** column for the expression, select **Expression**.  
  
4.  Run the query.  
  
## See Also  
[Sort and Group Query Results &#40;Visual Database Tools&#41;](../content/Sort-and-Group-Query-Results--Visual-Database-Tools-.md)  
[Summarize Query Results &#40;Visual Database Tools&#41;](../content/Summarize-Query-Results--Visual-Database-Tools-.md)  
  
