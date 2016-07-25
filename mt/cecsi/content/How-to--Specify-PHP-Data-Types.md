---
title: "How to: Specify PHP Data Types"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fee6e6b8-aad9-496b-84a2-18d2950470a4
caps.latest.revision: 32
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
# How to: Specify PHP Data Types
When using the PDO_SQLSRV driver, you can specify the PHP data type when retrieving data from the server with PDOStatement::bindColumn and PDOStatement::bindParam. See [PDOStatement::bindColumn](../Topic/PDOStatement::bindColumn.md) and [PDOStatement::bindParam](../Topic/PDOStatement::bindParam.md) for more information.  
  
The following steps summarize how to specify PHP data types when retrieving data from the server using the SQLSRV driver:  
  
1.  Set up and execute a Transact-SQL query with [sqlsrv_query](../content/sqlsrv_query.md) or the combination of [sqlsrv_prepare](../content/sqlsrv_prepare.md)/[sqlsrv_execute](../content/sqlsrv_execute.md).  
  
2.  Make a row of data available for reading with [sqlsrv_fetch](../content/sqlsrv_fetch.md).  
  
3.  Retrieve field data from a returned row using [sqlsrv_get_field](../content/sqlsrv_get_field.md) with the desired PHP data type specified as the optional third parameter. If the optional third parameter is not specified, data will be returned according to the default PHP types. For information about the default PHP return types, see [Default PHP Data Types](../content/Default-PHP-Data-Types.md).  
  
    For information about the constants used to specify the PHP data type, see the PHPTYPEs section of [Constants &#40;Microsoft Drivers for PHP for SQL Server&#41;](../content/Constants--Microsoft-Drivers-for-PHP-for-SQL-Server-.md).  
  
## Example  
The following example retrieves rows from the *Production.ProductReview* table of the AdventureWorks database. In each returned row the *ReviewDate* field is retrieved as a string and the *Comments* field is retrieved as a stream. The stream data is displayed by using the PHP [fpassthru](http://php.net/manual/en/function.fpassthru.php) function.  
  
The example assumes that SQL Server and the [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) database are installed on the local computer. All output is written to the console when the example is run from the command line.  
  
```  
<?php  
/*Connect to the local server using Windows Authentication and specify  
the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up the Transact-SQL query. */  
$tsql = "SELECT ReviewerName,   
                ReviewDate,  
                Rating,   
                Comments   
         FROM Production.ProductReview   
         WHERE ProductID = ?   
         ORDER BY ReviewDate DESC";  
  
/* Set the parameter value. */  
$productID = 709;  
$params = array( $productID);  
  
/* Execute the query. */  
$stmt = sqlsrv_query($conn, $tsql, $params);  
if( $stmt === false )  
{  
     echo "Error in statement execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve and display the data. The first and third fields are  
retrieved according to their default types, strings. The second field  
is retrieved as a string with 8-bit character encoding. The fourth  
field is retrieved as a stream with 8-bit character encoding.*/  
while ( sqlsrv_fetch( $stmt))  
{  
   echo "Name: ".sqlsrv_get_field( $stmt, 0 )."\n";  
   echo "Date: ".sqlsrv_get_field( $stmt, 1,   
                       SQLSRV_PHPTYPE_STRING( SQLSRV_ENC_CHAR))."\n";  
   echo "Rating: ".sqlsrv_get_field( $stmt, 2 )."\n";  
   echo "Comments: ";  
   $comments = sqlsrv_get_field( $stmt, 3,   
                            SQLSRV_PHPTYPE_STREAM(SQLSRV_ENC_CHAR));  
   fpassthru( $comments);  
   echo "\n";   
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
In the example, retrieving the second field (*ReviewDate*) as a string preserves millisecond accuracy of the SQL Server DATETIME data type. By default, the SQL Server DATETIME data type is retrieved as a PHP DateTime object in which the millisecond accuracy is lost.  
  
Retrieving the fourth field (*Comments*) as a stream is for demonstration purposes. By default, the SQL Server data type nvarchar(3850) is retrieved as a string, which is acceptable for most situations.  
  
> [!NOTE]  
> The [sqlsrv_field_metadata](../content/sqlsrv_field_metadata.md) function provides a way to obtain field information, including type information, before executing a query.  
  
## See Also  
[Retrieving Data](../content/Retrieving-Data.md)  
[About Code Examples in the Documentation](../content/About-Code-Examples-in-the-Documentation.md)  
[How to: Retrieve Output Parameters Using the SQLSRV Driver](../Topic/How%20to:%20Retrieve%20Output%20Parameters%20Using%20the%20SQLSRV%20Driver.md)  
[How to: Retrieve Input and Output Parameters Using the SQLSRV Driver](../Topic/How%20to:%20Retrieve%20Input%20and%20Output%20Parameters%20Using%20the%20SQLSRV%20Driver.md)  
  
