---
title: Connection Options
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6d1ea295-8e34-438e-8468-4bbc0f76192c
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
# Connection Options
This topic lists the options that are permitted in the associative array \(when using [sqlsrv_connect](../content/sqlsrv_connect.md) in the SQLSRV driver\) or the keywords that are permitted in the data source name \(dsn\) \(when using [PDO::__construct](../Topic/PDO::__construct.md) in the PDO\_SQLSRV driver\).  
  
|Key|Value|Description|Default|  
|-------|---------|---------------|-----------|  
|APP|String|Specifies the application name used in tracing.|No value set.|  
|ApplicationIntent|String|Declares the application workload type when connecting to a server. Possible values are ReadOnly and ReadWrite.<br /><br />For more information about [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] support for [!INCLUDE[ssHADR](../content/includes/ssHADR_md.md)], see [PHP Driver for SQL Server Support for High Availability, Disaster Recovery](../content/PHP-Driver-for-SQL-Server-Support-for-High-Availability--Disaster-Recovery.md).|ReadWrite|  
|AttachDBFileName|String|Specifies which database file the server should attach.|No value set.|  
|CharacterSet<br /><br />\(not supported in the PDO\_SQLSRV driver\)|String|Specifies the character set used to send data to the server.<br /><br />Possible values are SQLSRV\_ENC\_CHAR and UTF\-8. For more information, see [How to: Send and Retrieve UTF-8 Data Using Built-In UTF-8 Support](../Topic/How%20to:%20Send%20and%20Retrieve%20UTF-8%20Data%20Using%20Built-In%20UTF-8%20Support.md).|SQLSRV\_ENC\_CHAR|  
|ConnectionPooling|1 or **true** for connection pooling on.<br /><br />0 or **false** for connection pooling off.|Specifies whether the connection is assigned from a connection pool \(1 or **true**\) or not \(0 or **false**\).|**true** \(1\)|  
|Database|String|Specifies the name of the database in use for the connection being established<sup>1</sup>.|The default database for the login being used.|  
|Encrypt|1 or **true** for encryption on.<br /><br />0 or **false** for encryption off.|Specifies whether the communication with SQL Server is encrypted \(1 or **true**\) or unencrypted \(0 or **false**\)<sup>2</sup>.|**false** \(0\)|  
|Failover\_Partner|String|Specifies the server and instance of the database's mirror \(if enabled and configured\) to use when the primary server is unavailable.<br /><br />There are restrictions to using Failover\_Partner with MultiSubnetFailover. For more information, see [PHP Driver for SQL Server Support for High Availability, Disaster Recovery](../content/PHP-Driver-for-SQL-Server-Support-for-High-Availability--Disaster-Recovery.md).|No value set.|  
|LoginTimeout|Integer \(SQLSRV driver<br /><br />String \(PDO\_SQLSRV driver|Specifies the number of seconds to wait before failing the connection attempt.|No timeout.|  
|MultipleActiveResultSets|1 or **true** to use multiple active result sets.<br /><br />0 or **false** to disable multiple active result sets.|Disables or explicitly enables support for multiple active Result sets \(MARS\).<br /><br />For more information, see [How to: Disable Multiple Active Resultsets &#40;MARS&#41;](../Topic/How%20to:%20Disable%20Multiple%20Active%20Resultsets%20(MARS).md).|true \(1\)|  
|MultiSubnetFailover|String|Always specify **multiSubnetFailover\=yes** when connecting to the availability group listener of a [!INCLUDE[ssSQL11](../content/includes/ssSQL11_md.md)] availability group or a [!INCLUDE[ssSQL11](../content/includes/ssSQL11_md.md)] Failover Cluster Instance. **multiSubnetFailover\=yes** configures [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] to provide faster detection of and connection to the \(currently\) active server. Possible values are Yes and No.<br /><br />For more information about [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] support for [!INCLUDE[ssHADR](../content/includes/ssHADR_md.md)], see [PHP Driver for SQL Server Support for High Availability, Disaster Recovery](../content/PHP-Driver-for-SQL-Server-Support-for-High-Availability--Disaster-Recovery.md).|No|  
|PWD<br /><br />\(not supported in the PDO\_SQLSRV driver\)|String|Specifies the password associated with the User ID to be used when connecting with SQL Server Authentication<sup>3</sup>.|No value set.|  
|QuotedId|1 or **true** to use SQL\-92 rules.<br /><br />0 or **false** to use legacy rules.|Specifies whether to use SQL\-92 rules for quoted identifiers \(1 or **true**\) or to use legacy Transact\-SQL rules \(0 or **false**\).|**true** \(1\)|  
|ReturnDatesAsStrings<br /><br />\(not supported in the PDO\_SQLSRV driver\)|1 or **true** to return date and time types as strings.<br /><br />0 or **false** to return date and time types as PHP **DateTime** types.|Retrieves date and time types \(datetime, date, time, datetime2, and datetimeoffset\) as strings or as PHP types. When using the PDO\_SQLSRV driver, dates are returned as strings. The PDO\_SQLSRV driver has no **datetime** type.<br /><br />For more information, see [How to: Retrieve Date and Time Type as Strings Using the SQLSRV Driver](../Topic/How%20to:%20Retrieve%20Date%20and%20Time%20Type%20as%20Strings%20Using%20the%20SQLSRV%20Driver.md).|**false**|  
|Scrollable|String|"buffered" indicates that you want a client\-side \(buffered\) cursor, which allows you to cache an entire result set in memory. See [Cursor Types &#40;SQLSRV Driver&#41;](../content/Cursor-Types--SQLSRV-Driver-.md) for more information.|Forward\-only cursor|  
|Server<br /><br />\(not supported in the SQLSRV driver\)|String|The [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] instance to connect to.<br /><br />You can also specify a virtual network name, to connect to an AlwaysOn availability group. For more information about [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] support for [!INCLUDE[ssHADR](../content/includes/ssHADR_md.md)], see [PHP Driver for SQL Server Support for High Availability, Disaster Recovery](../content/PHP-Driver-for-SQL-Server-Support-for-High-Availability--Disaster-Recovery.md).|Server is a required keyword \(although it does not have to be the first keyword in the connection string\). If a server name is not passed to the keyword, an attempt will be made to connect to the local instance.<br /><br />The value passed to Server can be the name of a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] instance, or the IP address of the instance. You can optionally specify a port number \(for example, `sqlsrv:server=(local),1033`\).<br /><br />Beginning in version 3.0 of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)] you can also specify a LocalDB instance with `server=(localdb)\instancename`. For more information, see [PHP Driver for SQL Server Support for LocalDB](../content/PHP-Driver-for-SQL-Server-Support-for-LocalDB.md).|  
|TraceFile|String|Specifies the path for the file used for trace data.|No value set.|  
|TraceOn|1 or **true** to enable tracing.<br /><br />0 or **false** to disable tracing.|Specifies whether ODBC tracing is enabled \(1 or **true**\) or disabled \(0 or **false**\) for the connection being established.|**false** \(0\)|  
|TransactionIsolation|The SQLSRV driver uses the following values:<br /><br />SQLSRV\_TXN\_READ\_UNCOMMITTED<br /><br />SQLSRV\_TXN\_READ\_COMMITTED<br /><br />SQLSRV\_TXN\_REPEATABLE\_READ<br /><br />SQLSRV\_TXN\_SNAPSHOT<br /><br />SQLSRV\_TXN\_SERIALIZABLE<br /><br />The PDO\_SQLSRV driver uses the following values:<br /><br />PDO::SQLSRV\_TXN\_READ\_UNCOMMITTED<br /><br />PDO::SQLSRV\_TXN\_READ\_COMMITTED<br /><br />PDO::SQLSRV\_TXN\_REPEATABLE\_READ<br /><br />PDO::SQLSRV\_TXN\_SNAPSHOT<br /><br />PDO::SQLSRV\_TXN\_SERIALIZABLE|Specifies the transaction isolation level.<br /><br />For more information about transaction isolation, see [SET TRANSACTION ISOLATION LEVEL](http://go.microsoft.com/fwlink/?LinkID=191497) in the SQL Server documentation.|SQLSRV\_TXN\_READ\_COMMITTED<br /><br />or<br /><br />PDO::SQLSRV\_TXN\_READ\_COMMITTED|  
|TrustServerCertificate|1 or **true** to trust certificate.<br /><br />0 or **false** to not trust certificate.|Specifies whether the client should trust \(1 or **true**\) or reject \(0 or **false**\) a self\-signed server certificate.|**false** \(0\)|  
|UID<br /><br />\(not supported in the PDO\_SQLSRV driver\)|String|Specifies the User ID to be used when connecting with SQL Server Authentication<sup>3</sup>.|No value set.|  
|WSID|String|Specifies the name of the computer for tracing.|No value set.|  
  
1. All queries executed on the established connection will be made to the database that is specified by the *Database* attribute. However, data in other databases can be accessed by using a fully\-qualified name if the user has the appropriate permissions. For example, if the *master* database is set with the *Database* connection attribute, it is still possible to execute a Transact\-SQL query that accesses the *AdventureWorks.HumanResources.Employee* table by using the fully\-qualified name.  
  
2. Enabling *Encryption* can impact the performance of some applications due to the computational overhead required to encrypt data.  
  
3. The *UID* and *PWD* attributes must both be set when connecting with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Authentication.  
  
Many of the supported keys are ODBC connection string attributes. For information about ODBC connection strings, see [Using Connection String Keywords with SQL Native Client](http://go.microsoft.com/fwlink/?LinkId=105504).  
  
## See Also  
[Connecting to the Server](../content/Connecting-to-the-Server.md)  
  
