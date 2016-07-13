---
title: Add Tables to Queries (Visual Database Tools)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6551aa7e-31a1-4636-852a-819bc53d658b
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
# Add Tables to Queries (Visual Database Tools)
When you create a query, you are retrieving data from a table or other objects structured like tables — views and certain user\-defined functions. To work with any of these objects in your query, you add them to the **Diagram Pane**.  
  
### To add a table or table\-valued object to a query  
  
1.  In the **Diagram pane** of the Query and View Designer, right\-click the background and choose **Add Table** from the shortcut menu.  
  
2.  In the **Add Table** dialog box, select the tab for the type of object you want to add to the query.  
  
3.  In the list of items, double\-click each item you want to add.  
  
4.  When you finish adding items, click **Close**.  
  
    The Query and View Designer updates the **Diagram Pane**, **Criteria Pane**, and **SQL Pane** accordingly.  
  
Tables and views are automatically added to the query when you reference them in the statement in the SQL pane.  
  
The Query and View Designer will not display data columns for a table or table\-structured object if you do not have sufficient access rights to it or if the provider cannot return information about it. In such cases, only a title bar and the \* (All Columns) check box are displayed for the table or table\-valued object.  
  
### To add an existing query to a new query  
  
1.  Make sure the **SQL Pane** is displayed in the new query you are creating.  
  
2.  In the **SQL Pane**, type a right and left parentheses () after the word FROM.  
  
3.  Open the Query Designer for the existing query. (You now have two Query Designers open.)  
  
4.  Display the **SQL Pane** for the inner query – the existing query you are including in the new, outer query.  
  
5.  Select all the text in the **SQL Pane**, and copy it to the Clipboard.  
  
6.  Click in the **SQL Pane** of the new query, situate the cursor between the parentheses you added, and paste the contents of the Clipboard.  
  
7.  Still in the **SQL Pane**, add an alias after the right parenthesis.  
  
## See Also  
[Create Table Aliases &#40;Visual Database Tools&#41;](../content/Create-Table-Aliases--Visual-Database-Tools-.md)  
[Remove Tables from Queries &#40;Visual Database Tools&#41;](../content/Remove-Tables-from-Queries--Visual-Database-Tools-.md)  
[Specify Search Criteria &#40;Visual Database Tools&#41;](../content/Specify-Search-Criteria--Visual-Database-Tools-.md)  
[Summarize Query Results &#40;Visual Database Tools&#41;](../content/Summarize-Query-Results--Visual-Database-Tools-.md)  
[Perform Basic Operations with Queries &#40;Visual Database Tools&#41;](../content/Perform-Basic-Operations-with-Queries--Visual-Database-Tools-.md)  
  
