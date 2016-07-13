---
title: Retrieving Data
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3414992c-61c0-4e7d-b509-72517e52c1bb
manager: jhubbard
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
# Retrieving Data
This topic and the topics in this section discuss how to retrieve data.  
  
## SQLSRV Driver  
The SQLSRV driver of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] provides the following options for retrieving data from a result set:  
  
-   [sqlsrv_fetch_array](../content/sqlsrv_fetch_array.md)  
  
-   [sqlsrv_fetch_object](../content/sqlsrv_fetch_object.md)  
  
-   [sqlsrv_fetch](../content/sqlsrv_fetch.md)\/[sqlsrv_get_field](../content/sqlsrv_get_field.md)  
  
> [!NOTE]  
> When you use any of the functions mentioned above, avoid null comparisons as the criterion for exiting loops. Because **sqlsrv** functions return false when an error occurs, the following code could result in an infinite loop upon an error in [sqlsrv_fetch_array](../content/sqlsrv_fetch_array.md):  
>   
> `/*``This code could result in an infinite loop. It is recommended that`  
>   
> `you do NOT use null comparisons as the criterion for exiting loops,`  
>   
> `as is done here. */`  
>   
> `do{`  
>   
> `$result = sqlsrv_fetch_array($stmt);`  
>   
> `} while( !is_null($result));`  
  
If your query retrieves more than one result set, you can move to the next result set with [sqlsrv_next_result](../content/sqlsrv_next_result.md).  
  
Beginning in version 1.1 of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)], you can use [sqlsrv\_has\_rows](../content/sqlsrv_has_rows.md) to see if a result set has rows.  
  
## PDO\_SQLSRV Driver  
The PDO\_SQLSRV driver of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] provides the following options for retrieving data from a result set:  
  
-   [PDOStatement::fetch](../Topic/PDOStatement::fetch.md)  
  
-   [PDOStatement::fetchAll](../Topic/PDOStatement::fetchAll.md)  
  
-   [PDOStatement::fetchColumn](../Topic/PDOStatement::fetchColumn.md)  
  
-   [PDOStatement::fetchObject](../Topic/PDOStatement::fetchObject.md)  
  
If your query retrieves more than one result set, you can move to the next result set with [PDOStatement::nextRowset](../Topic/PDOStatement::nextRowset.md).  
  
You can see how many rows are in a result set if you specify a scrollable cursor, and then call [PDOStatement::rowCount](../Topic/PDOStatement::rowCount.md).  
  
[PDO::prepare](../Topic/PDO::prepare.md) lets you specify a cursor type. Then, with [PDOStatement::fetch](../Topic/PDOStatement::fetch.md) you can select a row. See [PDO::prepare](../Topic/PDO::prepare.md) for a sample and more information.  
  
## In This Section  
  
|Topic|Description|  
|---------|---------------|  
|[Retrieving Data as a Stream](../content/Retrieving-Data-as-a-Stream-Using-the-SQLSRV-Driver.md)|Provides an overview of how to stream data from the server, and provides links to specific use cases.|  
|[Using Directional Parameters](../content/Using-Directional-Parameters.md)|Describes how to use directional parameters when calling a stored procedure.|  
|[Specifying a Cursor Type and Selecting Rows](../content/Specifying-a-Cursor-Type-and-Selecting-Rows.md)|Demonstrates how to create a result set with rows that you can access in any order when using the SQLSRV driver.|  
|[How to: Retrieve Date and Time Type as Strings Using the SQLSRV Driver](../Topic/How%20to:%20Retrieve%20Date%20and%20Time%20Type%20as%20Strings%20Using%20the%20SQLSRV%20Driver.md)|Describes how to retrieve date and time types as strings.|  
  
## Related Sections  
[How to: Specify PHP Data Types](../Topic/How%20to:%20Specify%20PHP%20Data%20Types.md)  
  
## See Also  
[Programming Guide for PHP SQL Driver](../content/Programming-Guide-for-PHP-SQL-Driver.md)
[Retrieving Data](../content/Retrieving-Data.md)  
  
