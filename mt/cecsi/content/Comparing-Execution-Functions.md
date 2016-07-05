---
title: Comparing Execution Functions
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 130fc0fd-87dd-46b2-918f-de9dc572c769
translation.priority.ht: 
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
# Comparing Execution Functions
The [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] provides several options for executing functions.  
  
If you are using the SQLSRV driver, use [sqlsrv_query](../content/sqlsrv_query.md) to execute a single query and [sqlsrv_prepare](../content/sqlsrv_prepare.md) with [sqlsrv_execute](../content/sqlsrv_execute.md) to execute a prepared statement multiple times with different parameter values for each execution.  
  
If you are using the PDO\_SQLSRV driver, you can execute a query with one of the following:  
  
-   [PDO::exec](../Topic/PDO::exec.md)  
  
-   [PDO::query](../Topic/PDO::query.md)  
  
-   [PDO::prepare](../Topic/PDO::prepare.md) and [PDOStatement::execute](../Topic/PDOStatement::execute.md).  
  
## See Also  
[SQLSRV Driver API Reference](../content/SQLSRV-Driver-API-Reference.md)  
[PDO_SQLSRV Driver Reference](../content/PDO_SQLSRV-Driver-Reference.md)  
[Programming Guide for PHP SQL Driver](../content/Programming-Guide-for-PHP-SQL-Driver.md)
  
