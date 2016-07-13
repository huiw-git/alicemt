---
title: Specify Conditions for Groups (Visual Database Tools)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 269ad9c5-3261-4526-badf-7be3c869f229
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
# Specify Conditions for Groups (Visual Database Tools)
You can limit the groups that appear in a query by specifying a condition that applies to groups as a whole — a HAVING clause. After the data has been grouped and aggregated, the conditions in the HAVING clause are applied. Only the groups that meet the conditions appear in the query.  
  
For example, you might want to see the average price of all books for each publisher in a `titles` table, but only if the average price exceeds $10.00. In that case, you could specify a HAVING clause with a condition such as `AVG(price) > 10`.  
  
> [!NOTE]  
> In some instances, you might want to exclude individual rows from groups before applying a condition to groups as a whole. For details, see [Use HAVING and WHERE Clauses in the Same Query &#40;Visual Database Tools&#41;](../content/Use-HAVING-and-WHERE-Clauses-in-the-Same-Query--Visual-Database-Tools-.md).  
  
You can create complex conditions for a HAVING clause by using AND and OR to link conditions. For details about using AND and OR in search conditions, see [Specify Multiple Search Conditions for One Column &#40;Visual Database Tools&#41;](../content/Specify-Multiple-Search-Conditions-for-One-Column--Visual-Database-Tools-.md).  
  
### To specify a condition for a group  
  
1.  Specify the groups for your query. For details, see [Group Rows in Query Results &#40;Visual Database Tools&#41;](../content/Group-Rows-in-Query-Results--Visual-Database-Tools-.md).  
  
2.  If it is not already in the [Criteria pane](../content/Criteria-Pane--Visual-Database-Tools-.md), add the column on which you want to base the condition. (Most often the condition involves a column that is already a group or summary column.) You cannot use a column that is not part of an aggregate function or of the GROUP BY clause.  
  
3.  In the **Filter** column, specify the condition to apply to the group.  
  
    The [Query and View Designer](../content/Query-and-View-Designer-Tools--Visual-Database-Tools-.md) automatically creates a HAVING clause in the statement in the [SQL pane](../content/SQL-Pane--Visual-Database-Tools-.md), such as in the following example:  
  
    ```  
    SELECT pub_id, AVG(price)  
    FROM titles  
    GROUP BY pub_id  
    HAVING (AVG(price) > 10)  
    ```  
  
4.  Repeat steps 2 and 3 for each additional condition you want to specify.  
  
## See Also  
[Sort and Group Query Results &#40;Visual Database Tools&#41;](../content/Sort-and-Group-Query-Results--Visual-Database-Tools-.md)  
  
