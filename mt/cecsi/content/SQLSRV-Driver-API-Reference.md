---
title: SQLSRV Driver API Reference
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0b55da26-ddeb-4e89-872a-91e0aba57103
manager:jhubbard
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
# SQLSRV Driver API Reference
The API name for the SQLSRV driver in the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] is **sqlsrv**. All **sqlsrv** functions begin with **sqlsrv\_** and are followed by a verb or a noun. Those followed by a verb perform some action and those followed by a noun return some form of metadata.  
  
## In This Section  
The SQLSRV driver contains the following functions:  
  
|Function|Description|  
|------------|---------------|  
|[sqlsrv\_begin\_transaction](../content/sqlsrv_begin_transaction.md)|Begins a transaction.|  
|[sqlsrv\_cancel](../content/sqlsrv_cancel.md)|Cancels a statement; discards any pending results for the statement.|  
|[sqlsrv\_client\_info](../content/sqlsrv_client_info.md)|Provides information about the client.|  
|[sqlsrv\_close](../content/sqlsrv_close.md)|Closes a connection. Frees all resources associated with the connection.|  
|[sqlsrv\_commit](../content/sqlsrv_commit.md)|Commits a transaction.|  
|[sqlsrv\_configure](../content/sqlsrv_configure.md)|Changes error handling and logging configurations.|  
|[sqlsrv\_connect](../content/sqlsrv_connect.md)|Creates and opens a connection.|  
|[sqlsrv\_errors](../content/sqlsrv_errors.md)|Returns error and\/or warning information about the last operation.|  
|[sqlsrv\_execute](../content/sqlsrv_execute.md)|Executes a prepared statement.|  
|[sqlsrv\_fetch](../content/sqlsrv_fetch.md)|Makes the next row of data available for reading.|  
|[sqlsrv\_fetch\_array](../content/sqlsrv_fetch_array.md)|Retrieves the next row of data as a numerically indexed array, an associative array, or both.|  
|[sqlsrv\_fetch\_object](../content/sqlsrv_fetch_object.md)|Retrieves the next row of data as an object.|  
|[sqlsrv\_field\_metadata](../content/sqlsrv_field_metadata.md)|Returns field metadata.|  
|[sqlsrv\_free\_stmt](../content/sqlsrv_free_stmt.md)|Closes a statement. Frees all resources associated with the statement.|  
|[sqlsrv\_get\_config](../content/sqlsrv_get_config.md)|Returns the value of the specified configuration setting.|  
|[sqlsrv\_get\_field](../content/sqlsrv_get_field.md)|Retrieves a field in the current row by index. The PHP return type can be specified.|  
|[sqlsrv_has_rows](../content/sqlsrv_has_rows.md)|Detects if a result set has one or more rows.|  
|[sqlsrv\_next\_result](../content/sqlsrv_next_result.md)|Makes the next result available for processing.|  
|[sqlsrv_num_rows](../content/sqlsrv_num_rows.md)|Reports the number of rows in a result set.|  
|[sqlsrv\_num\_fields](../content/sqlsrv_num_fields.md)|Retrieves the number of fields in an active result set.|  
|[sqlsrv\_prepare](../content/sqlsrv_prepare.md)|Prepares a Transact\-SQL query without executing it. Implicitly binds parameters.|  
|[sqlsrv\_query](../content/sqlsrv_query.md)|Prepares and executes a Transact\-SQL query.|  
|[sqlsrv\_rollback](../content/sqlsrv_rollback.md)|Rolls back a transaction.|  
|[sqlsrv\_rows\_affected](../content/sqlsrv_rows_affected.md)|Returns the number of modified rows.|  
|[sqlsrv\_send\_stream\_data](../content/sqlsrv_send_stream_data.md)|Sends up to eight kilobytes \(8 KB\) of data to the server with each call to the function.|  
|[sqlsrv\_server\_info](../content/sqlsrv_server_info.md)|Provides information about the server.|  
  
## Reference  
[PHP Manual](http://go.microsoft.com/fwlink/?LinkId=105500)  
  
## See Also  
[Overview of the PHP SQL Driver](../content/Overview-of-the-PHP-SQL-Driver.md)
[Constants &#40;Microsoft Drivers for PHP for SQL Server&#41;](../content/Constants--Microsoft-Drivers-for-PHP-for-SQL-Server-.md)  
[Programming Guide for PHP SQL Driver](../content/Programming-Guide-for-PHP-SQL-Driver.md)
[Getting Started with the PHP SQL Driver](../content/Getting-Started-with-the-PHP-SQL-Driver.md)
  
