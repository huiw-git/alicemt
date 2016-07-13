---
title: Verify Queries (Visual Database Tools)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1382c0c0-46dc-45f9-ab38-9bba1d347eea
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
# Verify Queries (Visual Database Tools)
To avoid problems, you can check the query you have built to ensure its syntax is correct. This option is especially useful when you enter statements in the [SQL pane](../content/SQL-Pane--Visual-Database-Tools-.md).  
  
Some notes to keep in mind about verifying queries:  
  
-   A statement can be valid, and therefore be verified successfully, even if it cannot be represented in the **Diagram Pane** and **Criteria Pane**.  
  
-   SQL Verification can detect some, but not all SQL errors. If a query contains an error not detected during SQL verification, the database will detect the error when you run the query.  
  
-   Queries that contain parameters cannot be verified.  
  
### To verify an SQL statement  
  
-   Right\-click in the **SQL Pane**, and select **Verify SQL Syntax** from the shortcut menu.  
  
## See Also  
[Run Queries &#40;Visual Database Tools&#41;](../content/Run-Queries--Visual-Database-Tools-.md)  
[Perform Basic Operations with Queries &#40;Visual Database Tools&#41;](../content/Perform-Basic-Operations-with-Queries--Visual-Database-Tools-.md)  
  
