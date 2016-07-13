---
title: sqlsrv_fetch_array
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - sqlsrv_fetch_array
apitype: NA
ms.assetid: 69270b9e-0791-42f4-856d-412da39dea63
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
# sqlsrv_fetch_array
Retrieves the next row of data as a numerically indexed array, associative array, or both.  
  
## Syntax  
  
```  
  
sqlsrv_fetch_array( resource $stmt[, int $fetchType [, row[, ]offset]])  
```  
  
#### Parameters  
*$stmt*: A statement resource corresponding to an executed statement.  
  
*$fetchType* \[OPTIONAL\]: A predefined constant. This parameter can take on one of the values listed in the following table:  
  
|Value|Description|  
|---------|---------------|  
|SQLSRV\_FETCH\_NUMERIC|The next row of data is returned as a numeric array.|  
|SQLSRV\_FETCH\_ASSOC|The next row of data is returned as an associative array. The array keys are the column names in the result set.|  
|SQLSRV\_FETCH\_BOTH|The next row of data is returned as both a numeric array and an associative array. This is the default value.|  
  
*row* \[OPTIONAL\]: Added in version 1.1. One of the following values, specifying the row to access in a result set that uses a scrollable cursor. \(When *row* is specified, *fetchtype* must be explicitly specified, even if you specify the default value.\)  
  
-   SQLSRV\_SCROLL\_NEXT  
-   SQLSRV\_SCROLL\_PRIOR  
-   SQLSRV\_SCROLL\_FIRST  
-   SQLSRV\_SCROLL\_LAST  
-   SQLSRV\_SCROLL\_ABSOLUTE  
-   SQLSRV\_SCROLL\_RELATIVE  
  
For more information about these values, see [Specifying a Cursor Type and Selecting Rows](../content/Specifying-a-Cursor-Type-and-Selecting-Rows.md). Scrollable cursor support was added in version 1.1 of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)].  
  
*offset* \[OPTIONAL\]: Used with SQLSRV\_SCROLL\_ABSOLUTE and SQLSRV\_SCROLL\_RELATIVE to specify the row to retrieve. The first record in the result set is 0.  
  
## Return Value  
If a row of data is retrieved, an **array** is returned. If there are no more rows to retrieve, **null** is returned. If an error occurs, **false** is returned.  
  
Based on the value of the *$fetchType* parameter, the returned **array** can be a numerically indexed **array**, an associative **array**, or both. By default, an **array** with both numeric and associative keys is returned. The data type of a value in the returned array will be the default PHP data type. For information about default PHP data types, see [Default PHP Data Types](../content/Default-PHP-Data-Types.md).  
  
## Remarks  
If a column with no name is returned, the associative key for the array element will be an empty string \(""\). For example, consider this Transact\-SQL statement that inserts a value into a database table and retrieves the server\-generated primary key:  
  
```
INSERT INTO Production.ProductPhoto (LargePhoto) VALUES (?);  
SELECT SCOPE_IDENTITY()
```
  
If the result set returned by the `SELECT SCOPE_IDENTITY()` portion of this statement is retrieved as an associative array, the key for the returned value will be an empty string \(""\) because the returned column has no name. To avoid this, you can retrieve the result as a numeric array, or you can specify a name for the returned column in the Transact\-SQL statement. The following is one way to specify a column name in Transact\-SQL:  
  
```
SELECT SCOPE_IDENTITY() AS PictureID
```
  
If a result set contains multiple columns without names, the value of the last unnamed column will be assigned to the empty string \(""\) key.  
  
## Example  
The following example retrieves each row of a result set as an associative **array**. The example assumes that the SQL Server and the [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) database are installed on the local computer. All output is written to the console when the example is run from the command line.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up and execute the query. */  
$tsql = "SELECT FirstName, LastName  
         FROM Person.Contact  
         WHERE LastName='Alan'";  
$stmt = sqlsrv_query( $conn, $tsql);  
if( $stmt === false)  
{  
     echo "Error in query preparation/execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve each row as an associative array and display the results.*/  
while( $row = sqlsrv_fetch_array( $stmt, SQLSRV_FETCH_ASSOC))  
{  
      echo $row['LastName'].", ".$row['FirstName']."\n";  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## Example  
The following example retrieves each row of a result set as a numerically indexed array.  
  
The example retrieves product information from the *Purchasing.PurchaseOrderDetail* table of the AdventureWorks database for products that have a specified date and a stocked quantity \(*StockQty*\) less than a specified value.  
  
The example assumes that SQL Server and the [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) database are installed on the local computer. All output is written to the console when the example is run from the command line.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Define the query. */  
$tsql = "SELECT ProductID,  
                UnitPrice,  
                StockedQty   
         FROM Purchasing.PurchaseOrderDetail  
         WHERE StockedQty < 3   
         AND DueDate='2002-01-29'";  
  
/* Execute the query. */  
$stmt = sqlsrv_query( $conn, $tsql);  
if ( $stmt )  
{  
     echo "Statement executed.\n";  
}   
else   
{  
     echo "Error in statement execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Iterate through the result set printing a row of data upon each  
iteration.*/  
while( $row = sqlsrv_fetch_array( $stmt, SQLSRV_FETCH_NUMERIC))  
{  
     echo "ProdID: ".$row[0]."\n";  
     echo "UnitPrice: ".$row[1]."\n";  
     echo "StockedQty: ".$row[2]."\n";  
     echo "-----------------\n";  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
The **sqlsrv\_fetch\_array** function always returns data according to the [Default PHP Data Types](../content/Default-PHP-Data-Types.md). For information about how to specify the PHP data type, see [How to: Specify PHP Data Types](../Topic/How%20to:%20Specify%20PHP%20Data%20Types.md).  
  
If a field with no name is retrieved, the associative key for the array element will be an empty string \(""\). For more information, see [sqlsrv_fetch_array](../content/sqlsrv_fetch_array.md).  
  
## See Also  
[SQLSRV Driver API Reference](../content/SQLSRV-Driver-API-Reference.md)  
[Retrieving Data](../content/Retrieving-Data.md)  
[About Code Examples in the Documentation](../content/About-Code-Examples-in-the-Documentation.md)  
[Programming Guide for PHP SQL Driver](../content/Programming-Guide-for-PHP-SQL-Driver.md)
  
