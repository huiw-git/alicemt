---
title: "How to: Connect Using Windows Authentication"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f403a4e0-b0a8-4939-9dc1-e1209626367e
caps.latest.revision: 35
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
# How to: Connect Using Windows Authentication
By default, the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] use Windows Authentication to connect to SQL Server. It is important to notice that in most scenarios, this means that the Web server's process identity or thread identity (if the Web server is using impersonation) is used to connect to the server, not an end-user's identity.  
  
The following points must be considered when you use Windows Authentication to connect to SQL Server:  
  
-   The credentials under which the Web server's process (or thread) is running must map to a valid SQL Server login in order to establish a connection.  
  
-   If SQL Server and the Web server are on different computers, SQL Server must be configured to enable remote connections.  
  
> [!NOTE]  
> Connection attributes such as *Database* and *ConnectionPooling* can be set when you establish a connection. For a complete list of supported connection attributes, see [Connection Options](../content/Connection-Options.md).  
  
Windows Authentication should be used to connect to SQL Server whenever possible for the following reasons:  
  
-   No credentials are passed over the network during authentication; user names and passwords are not embedded in the database connection string. This means that malicious users or attackers cannot obtain the credentials by monitoring the network or by viewing connection strings inside configuration files.  
  
-   Users are subject to centralized account management; security policies such as password expiration periods, minimum password lengths, and account lockout after multiple invalid logon requests are enforced.  
  
If Windows Authentication is not a practical option, see [How to: Connect Using SQL Server Authentication](../Topic/How%20to:%20Connect%20Using%20SQL%20Server%20Authentication.md).  
  
## Example  
Using the SQLSRV driver of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)], the following example uses the Windows Authentication to connect to a local instance of SQL Server. After the connection has been established, the server is queried for the login of the user who is accessing the database.  
  
The example assumes that SQL Server and the [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) database are installed on the local computer. All output is written to the browser when the example is run from the browser.  
  
```  
<?php  
/* Specify the server and connection string attributes. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
  
/* Connect using Windows Authentication. */  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Unable to connect.</br>";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Query SQL Server for the login of the user accessing the  
database. */  
$tsql = "SELECT CONVERT(varchar(32), SUSER_SNAME())";  
$stmt = sqlsrv_query( $conn, $tsql);  
if( $stmt === false )  
{  
     echo "Error in executing query.</br>";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve and display the results of the query. */  
$row = sqlsrv_fetch_array($stmt);  
echo "User login: ".$row[0]."</br>";  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## Example  
The following example uses the PDO_SQLSRV driver to accomplish the same task as the previous sample.  
  
```  
<?php  
try {  
   $conn = new PDO( "sqlsrv:Server=(local);Database=AdventureWorks", NULL, NULL);   
   $conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );  
}  
  
catch( PDOException $e ) {  
   die( "Error connecting to SQL Server" );   
}  
  
echo "Connected to SQL Server\n";  
  
$query = 'select * from Person.ContactType';   
$stmt = $conn->query( $query );   
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){   
   print_r( $row );   
}  
?>  
```  
  
## See Also  
[How to: Connect Using SQL Server Authentication](../Topic/How%20to:%20Connect%20Using%20SQL%20Server%20Authentication.md)  
[Programming Guide for PHP SQL Driver](../content/Programming-Guide-for-PHP-SQL-Driver.md)
[About Code Examples in the Documentation](../content/About-Code-Examples-in-the-Documentation.md)  
[How to: Create a SQL Server Login](http://go.microsoft.com/fwlink/?LinkId=106325)  
[How to: Create a Database User](http://go.microsoft.com/fwlink/?LinkId=106327)  
[Managing Users, Roles, and Logins](http://go.microsoft.com/fwlink/?LinkId=106329)  
[User-Schema Separation](http://go.microsoft.com/fwlink/?LinkId=106330)  
[Grant Object Permissions (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=106332)  
  
