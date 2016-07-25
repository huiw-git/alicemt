---
title: "sqlsrv_execute"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - sqlsrv_execute
apitype: NA
ms.assetid: 38331bc2-4391-4f9f-aa83-9873dad605a0
caps.latest.revision: 24
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
# sqlsrv_execute
Executes a previously prepared statement. See [sqlsrv_prepare](../content/sqlsrv_prepare.md) for information on preparing a statement for execution.  
  
> [!NOTE]  
> This function is ideal for executing a prepared statement multiple times with different parameter values.  
  
## Syntax  
  
```  
  
sqlsrv_execute( resource $stmt)  
```  
  
#### Parameters  
*$stmt*: A resource specifying the statement to be executed. For more information about how to create a statement resource, see [sqlsrv_prepare](../content/sqlsrv_prepare.md).  
  
## Return Value  
A Boolean value: **true** if the statement was successfully executed. Otherwise, **false**.  
  
## Example  
The following example executes a statement that updates a field in the *Sales.SalesOrderDetail* table in the [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) database. The example assumes that SQL Server and the AdventureWorks database are installed on the local computer. All output is written to the console when the example is run from the command line.  
  
```  
<?php  
/*Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false)  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up the Transact-SQL query. */  
$tsql = "UPDATE Sales.SalesOrderDetail   
         SET OrderQty = ( ?)   
         WHERE SalesOrderDetailID = ( ?)";  
  
/* Set up the parameters array. Parameters correspond, in order, to  
question marks in $tsql. */  
$params = array( 5, 10);  
  
/* Create the statement. */  
$stmt = sqlsrv_prepare( $conn, $tsql, $params);  
if( $stmt )  
{  
     echo "Statement prepared.\n";  
}  
else  
{  
     echo "Error in preparing statement.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Execute the statement. Display any errors that occur. */  
if( sqlsrv_execute( $stmt))  
{  
      echo "Statement executed.\n";  
}  
else  
{  
     echo "Error in executing statement.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## See Also  
[SQLSRV Driver API Reference](../content/SQLSRV-Driver-API-Reference.md)  
[About Code Examples in the Documentation](../content/About-Code-Examples-in-the-Documentation.md)  
[sqlsrv_query](../content/sqlsrv_query.md)  
  
