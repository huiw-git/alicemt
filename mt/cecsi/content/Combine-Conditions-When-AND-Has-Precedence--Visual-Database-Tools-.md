---
title: Combine Conditions When AND Has Precedence (Visual Database Tools)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 450eb2eb-6ea3-405b-8dd2-1ff926c016e7
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
# Combine Conditions When AND Has Precedence (Visual Database Tools)
To combine conditions with AND, you add the column to the query twice\-\-once for each condition. To combine conditions with OR, you put the first one in the Filter column and additional conditions into an **Or...** column.  
  
For example, imagine that you want to find either employees who have been with the company for more than five years in lower\-level jobs or employees with middle\-level jobs regardless of their hire date. This query requires three conditions, two of them linked with AND:  
  
-   Employees with a hire date earlier than five years ago AND with a job level of 100.  
  
    \-or\-  
  
-   Employees with a job level of 200.  
  
### To combine conditions when AND has precedence  
  
1.  In the [Criteria pane](../content/Criteria-Pane--Visual-Database-Tools-.md), add the data columns you want to search. If you want to search the same column using two or more conditions linked with AND, you must add the data column name to the grid once for each value you want to search.  
  
2.  In the **Filter** column, enter all the conditions that you want to link with AND. For example, to link conditions with AND that search the `hire_date` and `job_lvl` columns, enter the values `< '1/1/91'` and `= 100`, respectively, in the Filter column.  
  
    These grid entries produce the following WHERE clause in the statement in the [SQL Pane](../content/SQL-Pane--Visual-Database-Tools-.md):  
  
    ```  
    WHERE (hire_date < '01/01/91') AND  
      (job_lvl = 100)  
    ```  
  
3.  In the **Or...** grid column, enter conditions that you want to link with OR. For example, to add a condition that searches for another value in the `job_lvl` column, enter an additional value in the **Or...** column, such as `= 200`.  
  
    Adding a value in the **Or...** column adds another condition to the WHERE clause in the statement in the SQL pane:  
  
    ```  
    WHERE (hire_date < '01/01/91' ) AND  
      (job_lvl = 100) OR   
      (job_lvl = 200)  
    ```  
  
## See Also  
[Combine Conditions When OR Has Precedence &#40;Visual Database Tools&#41;](../content/Combine-Conditions-When-OR-Has-Precedence--Visual-Database-Tools-.md)  
[Conventions for Combining Search Conditions in the Criteria Pane &#40;Visual Database Tools&#41;](../content/Conventions-for-Combining-Search-Conditions-in-the-Criteria-Pane--Visual-Database-Tools-.md)  
[Rules for Entering Search Values &#40;Visual Database Tools&#41;](../content/Rules-for-Entering-Search-Values--Visual-Database-Tools-.md)  
[Specify Search Criteria &#40;Visual Database Tools&#41;](../content/Specify-Search-Criteria--Visual-Database-Tools-.md)  
  
