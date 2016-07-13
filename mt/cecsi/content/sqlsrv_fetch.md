---
title: sqlsrv_fetch
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
  - sqlsrv_fetch
apitype: NA
ms.assetid: a5a640a1-6e7d-452e-8b66-850a4dc2ce89
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
# sqlsrv_fetch
Makes the next row of a result set available for reading. Use [sqlsrv\_get\_field](../content/sqlsrv_get_field.md) to read fields of the row.  
  
## Syntax  
  
```  
  
sqlsrv_fetch( resource $stmt[, row[, ]offset])  
```  
  
#### Parameters  
*$stmt*: A statement resource corresponding to an executed statement.  
  
> [!NOTE]  
> A statement must be executed before results can be retrieved. For information on executing a statement, see [sqlsrv_query](../content/sqlsrv_query.md) and [sqlsrv_execute](../content/sqlsrv_execute.md).  
  
*row* \[OPTIONAL\]: One of the following values, specifying the row to access in a result set that uses a scrollable cursor:  
  
-   SQLSRV\_SCROLL\_NEXT  
  
-   SQLSRV\_SCROLL\_PRIOR  
  
-   SQLSRV\_SCROLL\_FIRST  
  
-   SQLSRV\_SCROLL\_LAST  
  
-   SQLSRV\_SCROLL\_ABSOLUTE  
  
-   SQLSRV\_SCROLL\_RELATIVE  
  
For more information on these values, see [Specifying a Cursor Type and Selecting Rows](../content/Specifying-a-Cursor-Type-and-Selecting-Rows.md).  
  
*offset* \[OPTIONAL\]: Used with SQLSRV\_SCROLL\_ABSOLUTE and SQLSRV\_SCROLL\_RELATIVE to specify the row to retrieve. The first record in the result set is 0.  
  
## Return Value  
If the next row of the result set was successfully retrieved, **true** is returned. If there are no more results in the result set, **null** is returned. If an error occurred, **false** is returned.  
  
## Example  
The following example uses **sqlsrv\_fetch** to retrieve a row of data containing a product review and the name of the reviewer. To retrieve data from the result set, [sqlsrv\_get\_field](../content/sqlsrv_get_field.md) is used. The example assumes that SQL Server and the [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) database are installed on the local computer. All output is written to the console when the example is run from the command line.  
  
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
  
/* Set up and execute the query. Note that both ReviewerName and  
Comments are of SQL Server type nvarchar. */  
$tsql = "SELECT ReviewerName, Comments   
         FROM Production.ProductReview  
         WHERE ProductReviewID=1";  
$stmt = sqlsrv_query( $conn, $tsql);  
if( $stmt === false )  
{  
     echo "Error in statement preparation/execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Make the first row of the result set available for reading. */  
if( sqlsrv_fetch( $stmt ) === false)  
{  
     echo "Error in retrieving row.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Note: Fields must be accessed in order.  
Get the first field of the row. Note that no return type is  
specified. Data will be returned as a string, the default for  
a field of type nvarchar.*/  
$name = sqlsrv_get_field( $stmt, 0);  
echo "$name: ";  
  
/*Get the second field of the row as a stream.  
Because the default return type for a nvarchar field is a  
string, the return type must be specified as a stream. */  
$stream = sqlsrv_get_field( $stmt, 1,   
                            SQLSRV_PHPTYPE_STREAM( SQLSRV_ENC_CHAR));  
while( !feof( $stream ))  
{   
    $str = fread( $stream, 10000);  
    echo $str;  
}  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## See Also  
[Retrieving Data](../content/Retrieving-Data.md)  
[SQLSRV Driver API Reference](../content/SQLSRV-Driver-API-Reference.md)  
[About Code Examples in the Documentation](../content/About-Code-Examples-in-the-Documentation.md)  
  
