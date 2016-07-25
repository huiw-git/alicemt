---
title: "Join Tables Automatically (Visual Database Tools)"
ms.custom: na
ms.date: 07/21/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f152af82-bcb6-49ca-af19-48cdb7fc9ac6
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
# Join Tables Automatically (Visual Database Tools)
When you add two or more tables to a query, the [Query and View Designer](../content/Query-and-View-Designer-Tools--Visual-Database-Tools-.md) attempts to determine if they are related. If they are, the Query and View Designer automatically puts join lines between the rectangles representing the tables or table-structured objects.  
  
The Query and View Designer will recognize tables as joined if:  
  
-   The database contains information that specifies that the tables are related.  
  
-   If two columns, one in each table, have the same name and data type. The column must be a primary key in at least one of the tables. For example, if you add `employee` and `jobs` tables, if the `job_id` column is the primary key in the `jobs` table, and if each table has a column called `job_id` with the same data type, the Query and View Designer will automatically join the tables.  
  
    > [!NOTE]  
    > The Query and View Designer will create only one join based on columns with the same name and data type. If more than one join is possible, the Query and View Designer stops after creating a join based on the first set of matching columns that it finds.  
  
-   The Query and View Designer detects that a search condition (a WHERE clause) is actually a join condition. For example, you might add the tables `employee` and `jobs`, then create a search condition that searches for the same value in the `job_id` column of both tables. When you do, the Query and View Designer detects that the search condition results in a join, and then creates a join condition based on the search condition.  
  
If the Query and View Designer has created a join that is not suitable to your query, you can modify the join or remove it. For details, see [Modify Join Operators &#40;Visual Database Tools&#41;](../content/Modify-Join-Operators--Visual-Database-Tools-.md) and [Remove Joins &#40;Visual Database Tools&#41;](../content/Remove-Joins--Visual-Database-Tools-.md).  
  
If the Query and View Designer does not automatically join the tables in your query, you can create a join yourself. For details, see [Join Tables Manually &#40;Visual Database Tools&#41;](../content/Join-Tables-Manually--Visual-Database-Tools-.md).  
  
## See Also  
[How the Query and View Designer Represents Joins &#40;Visual Database Tools&#41;](../content/How-the-Query-and-View-Designer-Represents-Joins--Visual-Database-Tools-.md)  
[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](../content/Design-Queries-and-Views-How-to-Topics--Visual-Database-Tools-.md)  
[Query with Joins &#40;Visual Database Tools&#41;](../content/Query-with-Joins--Visual-Database-Tools-.md)  
  
