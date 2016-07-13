---
title: Create Self-Joins Automatically (Visual Database Tools)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f9ec90e8-3aad-415c-a5c4-8dfa9540e37f
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
# Create Self-Joins Automatically (Visual Database Tools)
If a table has a reflexive relationship in the database, you can join it to itself automatically.  
  
### To create a self\-join automatically  
  
1.  Add to the [Diagram pane](../content/Diagram-Pane--Visual-Database-Tools-.md) the table you want to work with.  
  
2.  Add the same table again, so that the Diagram pane shows the same table twice within the Diagram pane.  
  
    The [Query and View Designer](../content/Query-and-View-Designer-Tools--Visual-Database-Tools-.md) assigns an alias to the second instance by adding a sequential number to the table name. In addition, the Query and View Designer creates a join line between the two rectangles representing the two different ways the table participates in the query.  
  
## See Also  
[Query with Joins &#40;Visual Database Tools&#41;](../content/Query-with-Joins--Visual-Database-Tools-.md)  
  
