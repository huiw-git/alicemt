---
title: Direct Statement Execution and Prepared Statement Execution in the PDO_SQLSRV Driver
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 05544ca6-1e07-486c-bf03-e8c2c25b3024
manager: jhubbard
---
# Direct Statement Execution and Prepared Statement Execution in the PDO_SQLSRV Driver
This topic discusses how you can use the PDO::SQLSRV\_ATTR\_DIRECT\_QUERY attribute to specify direct statement execution instead of the default, which is prepared statement execution.  When the driver prepares a statement, it can result in better performance if the statement will be executed more than once using bound parameters.  
  
## Remarks  
If you want to send a [!INCLUDE[tsql](../content/includes/tsql_md.md)] statement directly to the server without statement preparation by the driver, you can set the PDO::SQLSRV\_ATTR\_DIRECT\_QUERY attribute with [PDO::setAttribute](../Topic/PDO::setAttribute.md) \(or as a driver option passed to [PDO::__construct](../Topic/PDO::__construct.md)\) or when you call [PDO::prepare](../Topic/PDO::prepare.md). By default, the value of PDO::SQLSRV\_ATTR\_DIRECT\_QUERY is False \(use prepared statement execution\).  
  
If you use [PDO::query](../Topic/PDO::query.md), you might want direct execution. Before calling [PDO::query](../Topic/PDO::query.md), call [PDO::setAttribute](../Topic/PDO::setAttribute.md) and set PDO::SQLSRV\_ATTR\_DIRECT\_QUERY to True.  Each call to [PDO::query](../Topic/PDO::query.md) can be executed with a different setting for PDO::SQLSRV\_ATTR\_DIRECT\_QUERY.  
  
If you use [PDO::prepare](../Topic/PDO::prepare.md) and [PDOStatement::execute](../Topic/PDOStatement::execute.md) to execute a query multiple times using bound parameters, prepared statement execution will optimize execution of the repeated query.  In that situation, call [PDO::prepare](../Topic/PDO::prepare.md) with PDO::SQLSRV\_ATTR\_DIRECT\_QUERY set to False in the driver options array parameter. When necessary, you can execute prepared statements with PDO::SQLSRV\_ATTR\_DIRECT\_QUERY set to False.  
  
After you call [PDO::prepare](../Topic/PDO::prepare.md), the value of PDO::SQLSRV\_ATTR\_DIRECT\_QUERY cannot change when executing the prepared query.  
  
If a query requires the context that was set in a previous query, you should execute your queries with PDO::SQLSRV\_ATTR\_DIRECT\_QUERY set to True. For example, if you use temporary tables in your queries, PDO::SQLSRV\_ATTR\_DIRECT\_QUERY must be set to True.  
  
The following sample shows that when context from a previous statement is required, you need to set PDO::SQLSRV\_ATTR\_DIRECT\_QUERY to True.  This sample uses temporary tables, which are only available to subsequent statements in your program when queries are executed directly.  
  
```  
<?php  
   $conn = new PDO('sqlsrv:Server=(local)', '', '');  
   $conn->setAttribute(constant('PDO::SQLSRV_ATTR_DIRECT_QUERY'), true);  
  
   $stmt1 = $conn->query("DROP TABLE #php_test_table");  
  
   $stmt2 = $conn->query("CREATE TABLE #php_test_table ([c1_int] int, [c2_int] int)");  
  
   $v1 = 1;  
   $v2 = 2;  
  
   $stmt3 = $conn->prepare("INSERT INTO #php_test_table (c1_int, c2_int) VALUES (:var1, :var2)");  
  
   if ($stmt3) {  
      $stmt3->bindValue(1, $v1);  
      $stmt3->bindValue(2, $v2);  
  
      if ($stmt3->execute())  
         echo "Execution succeeded\n";       
      else  
         echo "Execution failed\n";  
   }  
   else  
      var_dump($conn->errorInfo());  
  
   $stmt4 = $conn->query("DROP TABLE #php_test_table");  
?>  
```  
  
## See Also  
[Programming Guide for PHP SQL Driver](../content/Programming-Guide-for-PHP-SQL-Driver.md)
  
