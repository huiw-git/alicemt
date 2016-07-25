---
title: "Add Columns to Queries (Visual Database Tools)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 82f3ba72-3d72-4fb1-8179-2a953a782787
caps.latest.revision: 4
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
# Add Columns to Queries (Visual Database Tools)
To use a column in a query, you must add it to the query. You might add a column to display it in query output, to use it for sorting, to search the contents of the column, or to summarize its contents. You can decide which of the columns you use in the query are included in the results pane when the query is run. For more information see [Remove Columns from Query Results &#40;Visual Database Tools&#41;](../content/Remove-Columns-from-Query-Results--Visual-Database-Tools-.md).  
  
> [!NOTE]  
> To view the data type of a column in Query and View Designer; select the table or table-valued object in the **Diagram Pane** and in the properties window click Column List. Then click the **ellipses (…)** to open the **Column List** dialog box.  
  
Wherever you use a column in a query, you can also use an expression that can consist of any combination of columns, literals, operators, and functions.  
  
### To add an individual column  
  
-   In the **Diagram Pane**, select the check box next to the column that you want to include.  
  
    -or-  
  
-   In the **Criteria Pane**, move to the first blank grid row, click the field in the **Column** column, and select a column name from the drop-down list.  
  
### To add all columns for one table or table-valued object  
  
-   In the **Diagram Pane**, select the check box next to **\&#42;(All Columns)**.  
  
### To add all columns for all tables and table-structured objects  
  
1.  Make sure no join lines in the **Table Operations Pane** are selected.  
  
2.  Right-click in the empty space of the Design window and choose **Properties** from the shortcut menu.  
  
3.  In the Properties window click **Output all columns** and choose **Yes** or **No** from the dropdown list.  
  
## See Also  
[Remove Columns from Query Results &#40;Visual Database Tools&#41;](../content/Remove-Columns-from-Query-Results--Visual-Database-Tools-.md)  
[Remove Columns from Queries &#40;Visual Database Tools&#41;](../content/Remove-Columns-from-Queries--Visual-Database-Tools-.md)  
[Specify Search Criteria &#40;Visual Database Tools&#41;](../content/Specify-Search-Criteria--Visual-Database-Tools-.md)  
[Summarize Query Results &#40;Visual Database Tools&#41;](../content/Summarize-Query-Results--Visual-Database-Tools-.md)  
[Perform Basic Operations with Queries &#40;Visual Database Tools&#41;](../content/Perform-Basic-Operations-with-Queries--Visual-Database-Tools-.md)  
  
