---
title: Remove Tables from Queries (Visual Database Tools)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8fea0b4f-99b7-4050-8d6f-a97ffb839619
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
# Remove Tables from Queries (Visual Database Tools)
You can remove a table — or any table\-valued object — from the query.  
  
> [!NOTE]  
> Removing a table or table\-valued object does not delete anything from the database; it only removes it from the current query. For details about removing a table from a database, see [How to: Delete Tables from a Database (Visual Database Tools)](assetId:///ca6aa3e9-9885-44c3-bafc-aec441fd97ec).  
  
### To remove a table or table\-structured object  
  
-   In the **Diagram Pane**, select the table, view, user\-defined function, synonym, or query, and then press DELETE, or right\-click the object and then choose **Remove** in the resulting dialog box. You can select and remove multiple objects at one time.  
  
    –or–  
  
-   Remove all references to the object in the **SQL Pane.**  
  
When you remove a table or table\-valued object, the Query and View Designer automatically removes joins that involve that table or table\-valued object and removes references to the object's columns in the **SQL Pane** and **Criteria Pane**. However, if the query contains complex expressions involving the object, the object is not automatically removed until all references to it are removed.  
  
## See Also  
[Add Tables to Queries &#40;Visual Database Tools&#41;](../content/Add-Tables-to-Queries--Visual-Database-Tools-.md)  
[Create Table Aliases &#40;Visual Database Tools&#41;](../content/Create-Table-Aliases--Visual-Database-Tools-.md)  
[Specify Search Criteria &#40;Visual Database Tools&#41;](../content/Specify-Search-Criteria--Visual-Database-Tools-.md)  
[Summarize Query Results &#40;Visual Database Tools&#41;](../content/Summarize-Query-Results--Visual-Database-Tools-.md)  
[Perform Basic Operations with Queries &#40;Visual Database Tools&#41;](../content/Perform-Basic-Operations-with-Queries--Visual-Database-Tools-.md)  
  
