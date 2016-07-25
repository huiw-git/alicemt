---
title: "Create Column Aliases (Visual Database Tools)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2e1c166-8ea7-47a2-b6a7-e419bf0fa3bb
caps.latest.revision: 3
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
# Create Column Aliases (Visual Database Tools)
You can create aliases for column names to make it easier to work with column names, calculations, and summary values. For example, you can create a column alias to:  
  
-   Create a column name, such as "Total Amount," for an expression such as `(quantity * unit_price)` or for an aggregate function.  
  
-   Create a shortened form of a column name, such as `"d_id"` for `"discounts.stor_id."`  
  
After you have defined a column alias, you can use the alias in a Select query to specify query output.  
  
### To create a column alias  
  
1.  In the **Criteria Pane**, locate the row containing the data column for which you want to create an alias, and if necessary, mark it for output. If the data column is not already in the grid, add it.  
  
2.  In the **Alias** column for that row, enter the alias. The alias must follow all naming conventions for SQL. If the alias name you enter contains spaces, the Query and View Designer automatically puts delimiters around it.  
  
## See Also  
[Add Columns to Queries &#40;Visual Database Tools&#41;](../content/Add-Columns-to-Queries--Visual-Database-Tools-.md)  
[Sort and Group Query Results &#40;Visual Database Tools&#41;](../content/Sort-and-Group-Query-Results--Visual-Database-Tools-.md)  
[Summarize Query Results &#40;Visual Database Tools&#41;](../content/Summarize-Query-Results--Visual-Database-Tools-.md)  
[Perform Basic Operations with Queries &#40;Visual Database Tools&#41;](../content/Perform-Basic-Operations-with-Queries--Visual-Database-Tools-.md)  
  
