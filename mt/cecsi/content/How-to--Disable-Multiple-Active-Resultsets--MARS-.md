---
title: "How to: Disable Multiple Active Resultsets (MARS)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1912ad05-d0a4-40ff-8888-0d85bb36a807
caps.latest.revision: 20
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
# How to: Disable Multiple Active Resultsets (MARS)
If you need to connect to a SQL Server data source that does not enable Multiple Active Result Sets (MARS), you can use the MultipleActiveResultSets connection option to disable or enable MARS.  
  
## Procedure  
  
#### To disable MARS support  
  
-   Use the following connection option:  
  
    ```  
    'MultipleActiveResultSets'=>false  
    ```  
  
    If your application attempts to execute a query on a connection that has an open active result set, the second query attempt will return the following error information:  
  
    The connection cannot process this operation because there is a statement with pending results.  To make the connection available for other queries either fetch all results, cancel or free the statement. For more information about the MultipleActiveResultSets connection option, see [Connection Options](../content/Connection-Options.md).  
  
## Example  
The following example shows how to disable MARS support, using the SQLSRV driver of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)].  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks", 'MultipleActiveResultSets'=> false);  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_close( $conn);  
?>  
```  
  
## Example  
The following example shows how to disable MARS support, using the PDO_SQLSRV driver of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)].  
  
```  
<?php  
// Connect to the local server using Windows Authentication and AdventureWorks database  
$serverName = "(local)";   
$database = "AdventureWorks";  
  
try {  
   $conn = new PDO(" sqlsrv:server=$serverName ; Database=$database ; MultipleActiveResultSets=false ", NULL, NULL);   
   $conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );   
}  
  
catch( PDOException $e ) {  
   die( "Error connecting to SQL Server" );   
}  
  
$conn = null;   
?>  
```  
  
## See Also  
[Connecting to the Server](../content/Connecting-to-the-Server.md)  
  
