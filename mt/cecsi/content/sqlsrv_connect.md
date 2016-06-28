---
title: sqlsrv_connect
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - sqlsrv_connect
apitype: NA
ms.assetid: 37836b49-258e-45ce-9549-b8bd85d6952d
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
# sqlsrv_connect
Creates a connection resource and opens a connection. By default, the connection is attempted using Windows Authentication.  
  
## Syntax  
  
```  
  
sqlsrv_connect( string $serverName [, array $connectionInfo])  
```  
  
#### Parameters  
*$serverName*: A string specifying the name of the server to which a connection is being established. An instance name \(for example, "myServer\\instanceName"\) or port number \(for example, "myServer, 1521"\) can be included as part of this string. For a complete description of the options available for this parameter, see the Server keyword in the ODBC Driver Connection String Keywords section of [Using Connection String Keywords with SQL Native Client](http://go.microsoft.com/fwlink/?LinkId=105504).  
  
Beginning in version 3.0 of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)], you can also specify a LocalDB instance with `"(localdb)\instancename"`. For more information, see [PHP Driver for SQL Server Support for LocalDB](../content/PHP-Driver-for-SQL-Server-Support-for-LocalDB.md).  
  
Also beginning in version 3.0 of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)], you can specify a virtual network name, to connect to an AlwaysOn availability group. For more information about [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] support for [!INCLUDE[ssHADR](../content/includes/ssHADR_md.md)], see [PHP Driver for SQL Server Support for High Availability, Disaster Recovery](../content/PHP-Driver-for-SQL-Server-Support-for-High-Availability--Disaster-Recovery.md).  
  
*$connectionInfo* \[OPTIONAL\]: An associative **array** that contains connection attributes \(for example, **array**\("Database" \=> "AdventureWorks"\)\). See [Connection Options](../content/Connection-Options.md) for a list of the supported keys for the array.  
  
## Return Value  
A PHP connection resource. If a connection cannot be successfully created and opened, **false** is returned.  
  
## Remarks  
If values for the *UID* and *PWD* keys are not specified in the optional *$connectionInfo* parameter, the connection will be attempted using Windows Authentication. For more information about connecting to the server, see [How to: Connect Using Windows Authentication](../Topic/How%20to:%20Connect%20Using%20Windows%20Authentication.md) and [How to: Connect Using SQL Server Authentication](../Topic/How%20to:%20Connect%20Using%20SQL%20Server%20Authentication.md).  
  
## Example  
The following example creates and opens a connection using Windows Authentication. The example assumes that SQL Server and the [AdventureWorks](http://www.codeplex.com/SqlServerSamples) database are installed on the local computer. All output is written to the console when the example is run from the command line.  
  
```  
<?php  
/*  
Connect to the local server using Windows Authentication and specify  
the AdventureWorks database as the database in use. To connect using  
SQL Server Authentication, set values for the "UID" and "PWD"  
 attributes in the $connectionInfo parameter. For example:  
$connectionInfo = array("UID" => $uid, "PWD" => $pwd, "Database"=>"AdventureWorks");  
*/  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
  
if( $conn )  
{  
     echo "Connection established.\n";  
}  
else  
{  
     echo "Connection could not be established.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
//-----------------------------------------------  
// Perform operations with connection.  
//-----------------------------------------------  
  
/* Close the connection. */  
sqlsrv_close( $conn);  
?>  
```  
  
## See Also  
[SQLSRV Driver API Reference](../content/SQLSRV-Driver-API-Reference.md)  
[Connecting to the Server](../content/Connecting-to-the-Server.md)  
[About Code Examples in the Documentation](../content/About-Code-Examples-in-the-Documentation.md)  
  
