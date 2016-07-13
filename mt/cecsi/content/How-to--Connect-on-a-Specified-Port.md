---
title: How to: Connect on a Specified Port
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 65a154d1-375c-439b-a653-7815c9d70ff3
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
# How to: Connect on a Specified Port
This topic describes how to connect to SQL Server on a specified port with the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)].  
  
### To connect on a specified port  
  
1.  Verify the port on which the server is configured to accept connections. For information about configuring a server to accept connections on a specified port, see [How to: Configure a Server to Listen on a Specific TCP Port \(SQL Server Configuration Manager\)](http://go.microsoft.com/fwlink/?LinkId=121865).  
  
2.  Add the desired port to the *$serverName* parameter of the [sqlsrv\_connect](../content/sqlsrv_connect.md) function. Separate the server name and the port with a comma. For example, the following lines of code use the SQLSRV driver to demonstrate how to connect to a server named *myServer* on port 1521:  
  
    ```  
    $serverName = "myServer, 1521";  
    sqlsrv_connect( $serverName );  
    ```  
  
    The following lines of code use the PDO\_SQLSRV driver to demonstrate how to connect to a server named *myServer* on port 1521:  
  
    ```  
    $serverName = "(local), 1521";  
    $database = "AdventureWorks";  
    $conn = new PDO( "sqlsrv:server=$serverName;Database=$database", "", "");  
    ```  
  
## See Also  
[Connecting to the Server](../content/Connecting-to-the-Server.md)  
[Programming Guide for PHP SQL Driver](../content/Programming-Guide-for-PHP-SQL-Driver.md)
[Getting Started with the PHP SQL Driver](../content/Getting-Started-with-the-PHP-SQL-Driver.md) 
[SQLSRV Driver API Reference](../content/SQLSRV-Driver-API-Reference.md)  
[PDO_SQLSRV Driver Reference](../content/PDO_SQLSRV-Driver-Reference.md)  
  
