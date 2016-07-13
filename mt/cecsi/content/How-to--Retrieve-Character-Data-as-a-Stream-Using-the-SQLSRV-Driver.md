---
title: How to: Retrieve Character Data as a Stream Using the SQLSRV Driver
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3c0dbca4-abfc-4449-b133-66c819681840
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
# How to: Retrieve Character Data as a Stream Using the SQLSRV Driver
Retrieving data as a stream is only available in the SQLSRV driver of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)], and is not available in the PDO\_SQLSRV driver.  
  
The SQLSRV driver takes advantage of PHP streams for retrieving large amounts of data from the server. The example in this topic demonstrates how to retrieve character data as a stream.  
  
## Example  
The following example retrieves a row from the *Production.ProductReview* table of the AdventureWorks database. The *Comments* field of the returned row is retrieved as a stream and displayed by using the PHP [fpassthru](http://go.microsoft.com/fwlink/?LinkId=217496) function.  
  
Retrieving data as a stream is accomplished by using [sqlsrv_fetch](../content/sqlsrv_fetch.md) and [sqlsrv_get_field](../content/sqlsrv_get_field.md) with the return type specified as a character stream. The return type is specified by using the constant **SQLSRV\_PHPTYPE\_STREAM**. For information about **sqlsrv** constants, see [Constants &#40;Microsoft Drivers for PHP for SQL Server&#41;](../content/Constants--Microsoft-Drivers-for-PHP-for-SQL-Server-.md).  
  
The example assumes that [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] and the [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) database are installed on the local computer. All output is written to the console when the example is run from the command line.  
  
```  
<?php  
/*Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
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
               CONVERT(varchar(32), ReviewDate, 107) AS [ReviewDate],  
               Rating,   
               Comments   
         FROM Production.ProductReview   
         WHERE ProductReviewID = ? ";  
  
/* Set the parameter value. */  
$productReviewID = 1;  
$params = array( $productReviewID);  
  
/* Execute the query. */  
$stmt = sqlsrv_query($conn, $tsql, $params);  
if( $stmt === false )  
{  
     echo "Error in statement execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve and display the data. The first three fields are retrieved  
as strings and the fourth as a stream with character encoding. */  
if(sqlsrv_fetch( $stmt ) === false )  
{  
     echo "Error in retrieving row.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
echo "Name: ".sqlsrv_get_field( $stmt, 0 )."\n";  
echo "Date: ".sqlsrv_get_field( $stmt, 1 )."\n";  
echo "Rating: ".sqlsrv_get_field( $stmt, 2 )."\n";  
echo "Comments: ";  
$comments = sqlsrv_get_field( $stmt, 3,   
                             SQLSRV_PHPTYPE_STREAM(SQLSRV_ENC_CHAR));  
fpassthru($comments);  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
Because no PHP return type is specified for the first three fields, each field is returned according to its default PHP type. For information about default PHP data types, see [Default PHP Data Types](../content/Default-PHP-Data-Types.md). For information about how to specify PHP return types, see [How to: Specify PHP Data Types](../Topic/How%20to:%20Specify%20PHP%20Data%20Types.md).  
  
## See Also  
[Retrieving Data](../content/Retrieving-Data.md)  
[Retrieving Data as a Stream Using the SQLSRV Driver](../content/Retrieving-Data-as-a-Stream-Using-the-SQLSRV-Driver.md)  
[About Code Examples in the Documentation](../content/About-Code-Examples-in-the-Documentation.md)  
  
