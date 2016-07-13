---
title: Results Pane (Visual Database Tools)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6309a1bc-a628-4141-8bb5-b35924bd19f9
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
# Results Pane (Visual Database Tools)
The Results pane shows the results of the most recently executed SELECT query. (The results of other query types are displayed in message boxes.) To open the results pane, open or create a query or view or return a table's data. If the results pane doesn't show by default, from the **Query Designer** menu, point to **Pane**, and then click **Results**.  
  
## What You Can Do in the Results Pane  
  
-   View the result set for the most recently executed SELECT query in a spreadsheet\-like grid.  
  
-   For queries or views that show data from a single table or view, you can edit the values in individual columns in the result set, add new rows, and delete existing rows.  
  
## Limitations in the Results Pane  
  
-   Results returned by table\-valued functions can only be updated in some cases.  
  
-   Queries or views that include columns from more than one table or view cannot be updated.  
  
-   Results returned by a stored procedure cannot be updated.  
  
-   Queries or views using the GROUP BY or DISTINCT clauses are not updatable.  
  
## Navigating in the Results Pane  
You can quickly navigate through the records using the navigation bar at the bottom of the Results pane.  
  
There are buttons for going to the first and last records, the next and previous records, and for going to a particular record.  
  
To go to a particular record, type the number of the row in the text box in the navigation bar and then press ENTER.  
  
For information about using keyboard shortcuts in the Query and View Designer see [Navigate in the Query and View Designer &#40;Visual Database Tools&#41;](../content/Navigate-in-the-Query-and-View-Designer--Visual-Database-Tools-.md).  
  
## Keeping the Results Set Synchronized with the Query Definition  
While you are working on the results of a query or view it is possible for the records in the results pane to get out of synchronization with the query's definition. For example, if you run a query for four out of five columns in a table, and then use the Diagram pane to add the fifth column to the definition of the query, that fifth column's data will not automatically be added to the Results pane. To make the results pane reflect the new query definition, run the query again.  
  
If a query changes, an alert icon and the text "Query Changed" appears in the lower\-right corner of the results pane. The icon is repeated in the upper\-left corner of the pane.  
  
## See Also  
[Create Queries &#40;Visual Database Tools&#41;](../content/Create-Queries--Visual-Database-Tools-.md)  
[Run Queries &#40;Visual Database Tools&#41;](../content/Run-Queries--Visual-Database-Tools-.md)  
[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](../content/Design-Queries-and-Views-How-to-Topics--Visual-Database-Tools-.md)  
[Diagram Pane &#40;Visual Database Tools&#41;](../content/Diagram-Pane--Visual-Database-Tools-.md)  
[Criteria Pane &#40;Visual Database Tools&#41;](../content/Criteria-Pane--Visual-Database-Tools-.md)  
[Work with Data in the Results Pane &#40;Visual Database Tools&#41;](../content/Work-with-Data-in-the-Results-Pane--Visual-Database-Tools-.md)  
  
