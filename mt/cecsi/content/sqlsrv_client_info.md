---
title: sqlsrv_client_info
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
  - sqlsrv_client_info
apitype: NA
ms.assetid: 3e2d3679-436a-45d8-8bdc-7c633b65a720
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
# sqlsrv_client_info
Returns information about the connection and client stack.  
  
## Syntax  
  
```  
  
sqlsrv_client_info( resource $conn)  
```  
  
#### Parameters  
*$conn*: The connection resource by which the client is connected.  
  
## Return Value  
An associative array with keys described in the table below, or **false** if the connection resource is null.  
  
**For PHP for SQL Server versions 3.2 and 3.1**:  
  
|Key|Description|  
|-------|---------------|  
|DriverDllName|MSODBCSQL11.DLL \(ODBC Driver 11 for SQL Server\)|  
|DriverODBCVer|ODBC version \(xx.yy\)|  
|DriverVer|ODBC Driver 11 for SQL Server DLL version:<br /><br />xx.yy.zzzz \([!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] version 3.2 or 3.1\)|  
|ExtensionVer|php\_sqlsrv.dll version:<br /><br />3.2.xxxx.x \(for [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] version 3.2\)<br /><br />3.1.xxxx.x \(for [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] version 3.1\)|  
  
**For PHP for SQL Server versions 3.0 and 2.0**:  
  
|Key|Description|  
|-------|---------------|  
|DriverDllName|SQLNCLI10.DLL \([!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] version 2.0\)|  
|DriverODBCVer|ODBC version \(xx.yy\)|  
|DriverVer|SQL Server Native Client DLL version:<br /><br />10.50.xxx \([!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] version 2.0\)|  
|ExtensionVer|php\_sqlsrv.dll version:<br /><br />2.0.xxxx.x \([!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] version 2.0\)|  
  
## Example  
The following example writes client information to the console when the example is run from the command line. The example assumes that SQL Server is installed on the local computer. All output is written to the console when the example is run from the command line.  
  
```  
<?php  
/*Connect to the local server using Windows Authentication and   
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$conn = sqlsrv_connect( $serverName);  
  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
if( $client_info = sqlsrv_client_info( $conn))  
{  
       foreach( $client_info as $key => $value)  
      {  
              echo $key.": ".$value."\n";  
      }  
}  
else  
{  
       echo "Client info error.\n";  
}  
  
/* Close connection resources. */  
sqlsrv_close( $conn);  
?>  
```  
  
## See Also  
[SQLSRV Driver API Reference](../content/SQLSRV-Driver-API-Reference.md)  
[About Code Examples in the Documentation](../content/About-Code-Examples-in-the-Documentation.md)  
  
