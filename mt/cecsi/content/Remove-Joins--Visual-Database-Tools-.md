---
title: Remove Joins (Visual Database Tools)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ccc212a1-fd13-48d6-85e5-5ff310c34bbd
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
# Remove Joins (Visual Database Tools)
If you do not want tables to be joined via an inner join or an outer join, you can remove the join between them. For example, you might remove a join that the [Query and View Designer](../content/Query-and-View-Designer-Tools--Visual-Database-Tools-.md) has been created automatically between two tables.  
  
> [!NOTE]  
> Removing a join from a query does not alter the underlying relationship in the database.  
  
If two joined tables are part of your query and you remove all join conditions between them, the resulting query becomes the product of both tables — that is, it becomes a CROSS JOIN.  
  
### To remove a join  
  
-   In the [Diagram pane](../content/Diagram-Pane--Visual-Database-Tools-.md), select the join line for the join to remove, and then press the DELETE key. You can select and delete multiple join lines at one time.  
  
The Query and View Designer removes the join line and alters the statement in the [SQL pane](../content/SQL-Pane--Visual-Database-Tools-.md).  
  
## See Also  
[Join Tables Automatically &#40;Visual Database Tools&#41;](../content/Join-Tables-Automatically--Visual-Database-Tools-.md)  
[Join Tables Manually &#40;Visual Database Tools&#41;](../content/Join-Tables-Manually--Visual-Database-Tools-.md)  
[Query with Joins &#40;Visual Database Tools&#41;](../content/Query-with-Joins--Visual-Database-Tools-.md)  
  
