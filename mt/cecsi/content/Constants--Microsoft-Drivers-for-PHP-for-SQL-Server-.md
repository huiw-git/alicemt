---
title: Constants (Microsoft Drivers for PHP for SQL Server)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9727c944-b645-48d6-9012-18dbde35ee3c
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
# Constants (Microsoft Drivers for PHP for SQL Server)
This topic discusses the constants that are defined by the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)].  
  
## PDO\_SQLSRV Driver Constants  
The constants listed on the [PDO website](http://go.microsoft.com/fwlink/?LinkID=187441) are valid in the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)].  
  
The following describe the Microsoft specific constants in the PDO\_SQLSRV driver.  
  
### Transaction Isolation Level Constants  
The **TransactionIsolation** key, which is used with [PDO::__construct](../Topic/PDO::__construct.md), accepts one of the following constants:  
  
-   PDO::SQLSRV\_TXN\_READ\_UNCOMMITTED  
  
-   PDO::SQLSRV\_TXN\_READ\_COMMITTED  
  
-   PDO::SQLSRV\_TXN\_REPEATABLE\_READ  
  
-   PDO::SQLSRV\_TXN\_SNAPSHOT  
  
-   PDO::SQLSRV\_TXN\_SERIALIZABLE  
  
For more information about the **TransactionIsolation** key, see [Connection Options](../content/Connection-Options.md).  
  
### Encoding Constants  
The PDO::SQLSRV\_ATTR\_ENCODING attribute can be passed to [PDOStatement::setAttribute](../Topic/PDOStatement::setAttribute.md), [PDO::setAttribute](../Topic/PDO::setAttribute.md), [PDO::prepare](../Topic/PDO::prepare.md), [PDOStatement::bindColumn](../Topic/PDOStatement::bindColumn.md), and [PDOStatement::bindParam](../Topic/PDOStatement::bindParam.md).  
  
The available values to pass to PDO::SQLSRV\_ATTR\_ENCODING are  
  
|PDO\_SQLSRV driver constant|Description|  
|-------------------------------|---------------|  
|PDO::SQLSRV\_ENCODING\_BINARY|Data is a raw byte stream from the server without performing encoding or translation.<br /><br />Not valid for PDO::setAttribute.|  
|PDO::SQLSRV\_ENCODING\_SYSTEM|Data is 8\-bit characters as specified in the code page of the Windows locale that is set on the system. Any multi\-byte characters or characters that do not map into this code page are substituted with a single byte question mark \(?\) character.|  
|PDO::SQLSRV\_ENCODING\_UTF8|Data is in the UTF\-8 encoding. This is the default encoding.|  
|PDO::SQLSRV\_ENCODING\_DEFAULT|Uses PDO::SQLSRV\_ENCODING\_SYSTEM if specified during connection.<br /><br />Use the connection’s encoding if specified in a prepare statement.|  
  
### Query Timeout  
The PDO::SQLSRV\_ATTR\_QUERY\_TIMEOUT attribute is any non\-negative integer representing the timeout period, in seconds. Zero \(0\) is the default and means no timeout.  
  
You can specify the PDO::SQLSRV\_ATTR\_QUERY\_TIMEOUT attribute with [PDOStatement::setAttribute](../Topic/PDOStatement::setAttribute.md), [PDO::setAttribute](../Topic/PDO::setAttribute.md), and [PDO::prepare](../Topic/PDO::prepare.md).  
  
### Direct or Prepared Execution  
You can select direct query execution or prepared statement execution with the PDO::SQLSRV\_ATTR\_DIRECT\_QUERY attribute. PDO::SQLSRV\_ATTR\_DIRECT\_QUERY can be set with [PDO::prepare](../Topic/PDO::prepare.md) or [PDO::setAttribute](../Topic/PDO::setAttribute.md). For more information about PDO::SQLSRV\_ATTR\_DIRECT\_QUERY, see [Direct Statement Execution and Prepared Statement Execution in the PDO_SQLSRV Driver](../content/Direct-Statement-Execution-and-Prepared-Statement-Execution-in-the-PDO_SQLSRV-Driver.md).  
  
## SQLSRV Driver Constants  
The following sections list the constants used by the SQLSRV driver.  
  
### ERR Constants  
The following table lists the constants that are used to specify if [sqlsrv\_errors](../content/sqlsrv_errors.md) returns errors, warnings, or both.  
  
|Value|Description|  
|---------|---------------|  
|SQLSRV\_ERR\_ALL|Errors and warnings generated on the last **sqlsrv** function call are returned. This is the default value.|  
|SQLSRV\_ERR\_ERRORS|Errors generated on the last **sqlsrv** function call are returned.|  
|SQLSRV\_ERR\_WARNINGS|Warnings generated on the last **sqlsrv** function call are returned.|  
  
### FETCH Constants  
The following table lists the constants that are used to specify the type of array returned by [sqlsrv_fetch_array](../content/sqlsrv_fetch_array.md).  
  
|SQLSRV constant|Description|  
|-------------------|---------------|  
|SQLSRV\_FETCH\_ASSOC|**sqlsrv\_fetch\_array** returns the next row of data as an associative array.|  
|SQLSRV\_FETCH\_BOTH|**sqlsrv\_fetch\_array** returns the next row of data as an array with both numeric and associative keys. This is the default value.|  
|SQLSRV\_FETCH\_NUMERIC|**sqlsrv\_fetch\_array** returns the next row of data as a numerically indexed array.|  
  
### Logging Constants  
This section lists the constants that are used to change the logging settings with [sqlsrv_configure](../content/sqlsrv_configure.md). For more information about logging activity, see [Logging Activity](../content/Logging-Activity.md).  
  
The following table lists the constants that can be used as the value for the **LogSubsystems** setting:  
  
|SQLSRV constant \(integer equivalent in paraentheses\)|Description|  
|----------------------------------------------------------|---------------|  
|SQLSRV\_LOG\_SYSTEM\_ALL \(\-1\)|Turns on logging of all subsystems.|  
|SQLSRV\_LOG\_SYSTEM\_CONN \(2\)|Turns on logging of connection activity.|  
|SQLSRV\_LOG\_SYSTEM\_INIT \(1\)|Turns on logging of initialization activity.|  
|SQLSRV\_LOG\_SYSTEM\_OFF \(0\)|Turns logging off.|  
|SQLSRV\_LOG\_SYSTEM\_STMT \(4\)|Turns on logging of statement activity.|  
|SQLSRV\_LOG\_SYSTEM\_UTIL \(8\)|Turns on logging of error functions activity \(such as **handle\_error** and **handle\_warning**\).|  
  
The following table lists the constants that can be used as the value for the **LogSeverity** setting:  
  
|SQLSRV constant \(integer equivalent in paraentheses\)|Description|  
|----------------------------------------------------------|---------------|  
|SQLSRV\_LOG\_SEVERITY\_ALL \(\-1\)|Specifies that errors, warnings, and notices will be logged.|  
|SQLSRV\_LOG\_SEVERITY\_ERROR \(1\)|Specifies that errors will be logged.|  
|SQLSRV\_LOG\_SEVERITY\_NOTICE \(4\)|Specifies that notices will be logged.|  
|SQLSRV\_LOG\_SEVERITY\_WARNING \(2\)|Specifies that warnings will be logged.|  
  
### Nullable Constants  
The following table lists the constants that you can use to determine whether or not a column is nullable or if this information is not available. You can compare the value of the **Nullable** key that is returned by [sqlsrv_field_metadata](../content/sqlsrv_field_metadata.md) to determine the column's nullable status.  
  
|SQLSRV constant \(integer equivalent in paraentheses\)|Description|  
|----------------------------------------------------------|---------------|  
|SQLSRV\_NULLABLE\_YES \(0\)|The column is nullable.|  
|SQLSRV\_NULLABLE\_NO \(1\)|The column is not nullable.|  
|SQLSRV\_NULLABLE\_UNKNOWN \(2\)|It is not known if the column is nullable.|  
  
### PARAM Constants  
The following list contains the constants for specifying parameter direction when you call [sqlsrv_query](../content/sqlsrv_query.md) or [sqlsrv_prepare](../content/sqlsrv_prepare.md).  
  
|SQLSRV constant|Description|  
|-------------------|---------------|  
|SQLSRV\_PARAM\_IN|Indicates an input parameter.|  
|SQLSRV\_PARAM\_INOUT|Indicates a bidirectional parameter.|  
|SQLSRV\_PARAM\_OUT|Indicates an output parameter.|  
  
### PHPTYPE Constants  
The following table lists the constants that are used to describe PHP data types. For information about PHP data types, see [PHP Types](http://go.microsoft.com/fwlink/?LinkId=104881).  
  
|SQLSRV constant|PHP data type|  
|-------------------|-----------------|  
|SQLSRV\_PHPTYPE\_INT|Integer|  
|SQLSRV\_PHPTYPE\_DATETIME|Datetime|  
|SQLSRV\_PHPTYPE\_FLOAT|Float|  
|SQLSRV\_PHPTYPE\_STREAM\(<encoding><sup>1</sup>\)|Stream|  
|SQLSRV\_PHPTYPE\_STRING\(<encoding><sup>1</sup>\)|String|  
  
1. **SQLSRV\_PHPTYPE\_STREAM** and **SQLSRV\_PHPTYPE\_STRING** accept a parameter that specifies the stream encoding. The following table contains the SQLSRV constants that are acceptable parameters, and a description of the corresponding encoding.  
  
|SQLSRV constant|Description|  
|-------------------|---------------|  
|SQLSRV\_ENC\_BINARY|Data is returned as a raw byte stream from the server without performing encoding or translation.|  
|SQLSRV\_ENC\_CHAR|Data is returned in 8\-bit characters as specified in the code page of the Windows locale that is set on the system. Any multi\-byte characters or characters that do not map into this code page are substituted with a single byte question mark \(?\) character.<br /><br />This is the default encoding.|  
|"UTF\-8"|Data is returned in the UTF\-8 encoding. This constant was added in version 1.1 of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)]. For more information about UTF\-8 support, see [How to: Send and Retrieve UTF-8 Data Using Built-In UTF-8 Support](../Topic/How%20to:%20Send%20and%20Retrieve%20UTF-8%20Data%20Using%20Built-In%20UTF-8%20Support.md).|  
  
> [!NOTE]  
> When you use **SQLSRV\_PHPTYPE\_STREAM** or **SQLSRV\_PHPTYPE\_STRING**, the encoding must be specified. If no parameter is supplied, an error will be returned.  
  
For more information about these constants, see [How to: Specify PHP Data Types](../Topic/How%20to:%20Specify%20PHP%20Data%20Types.md), [How to: Retrieve Character Data as a Stream Using the SQLSRV Driver](../Topic/How%20to:%20Retrieve%20Character%20Data%20as%20a%20Stream%20Using%20the%20SQLSRV%20Driver.md).  
  
### SQLTYPE Constants  
The following table lists the constants that are used to describe SQL Server data types. Some constants require parameters that correspond to precision, scale, and\/or length. For information about SQL Server data types, see [Data Types \(Transact\-SQL\).](http://go.microsoft.com/fwlink/?LinkId=104883) For information about precision, scale, and length, see [Precision, Scale, and Length \(Transact\-SQL\).](http://go.microsoft.com/fwlink/?LinkId=104885)  
  
|SQLSRV constant|SQL Server data type|  
|-------------------|------------------------|  
|SQLSRV\_SQLTYPE\_BIGINT|bigint|  
|SQLSRV\_SQLTYPE\_BINARY|binary|  
|SQLSRV\_SQLTYPE\_BIT|bit|  
|SQLSRV\_SQLTYPE\_CHAR\($charCount\)|char|  
|SQLSRV\_SQLTYPE\_DATE|date<sup>4</sup>|  
|SQLSRV\_SQLTYPE\_DATETIME|datetime|  
|SQLSRV\_SQLTYPE\_DATETIME2|datetime2<sup>4</sup>|  
|SQLSRV\_SQLTYPE\_DATETIMEOFFSET|datetimeoffset<sup>4</sup>|  
|SQLSRV\_SQLTYPE\_DECIMAL\($precision, $scale\)|decimal|  
|SQLSRV\_SQLTYPE\_FLOAT|float|  
|SQLSRV\_SQLTYPE\_IMAGE|image<sup>1</sup>|  
|SQLSRV\_SQLTYPE\_INT|int|  
|SQLSRV\_SQLTYPE\_MONEY|money|  
|SQLSRV\_SQLTYPE\_NCHAR\($charCount\)|nchar|  
|SQLSRV\_SQLTYPE\_NUMERIC\($precision, $scale\)|numeric|  
|SQLSRV\_SQLTYPE\_NVARCHAR\($charCount\)|nvarchar|  
|SQLSRV\_SQLTYPE\_NVARCHAR\('max'\)|nvarchar\(MAX\)|  
|SQLSRV\_SQLTYPE\_NTEXT|ntext<sup>2</sup>|  
|SQLSRV\_SQLTYPE\_REAL|real|  
|SQLSRV\_SQLTYPE\_SMALLDATETIME|smalldatetime|  
|SQLSRV\_SQLTYPE\_SMALLINT|smallint|  
|SQLSRV\_SQLTYPE\_SMALLMONEY|smallmoney|  
|SQLSRV\_SQLTYPE\_TEXT|text<sup>3</sup>|  
|SQLSRV\_SQLTYPE\_TIME|time<sup>4</sup>|  
|SQLSRV\_SQLTYPE\_TIMESTAMP|timestamp|  
|SQLSRV\_SQLTYPE\_TINYINT|tinyint|  
|SQLSRV\_SQLTYPE\_UNIQUEIDENTIFIER|uniqueidentifier|  
|SQLSRV\_SQLTYPE\_UDT|UDT|  
|SQLSRV\_SQLTYPE\_VARBINARY\($byteCount\)|varbinary|  
|SQLSRV\_SQLTYPE\_VARBINARY\('max'\)|varbinary\(MAX\)|  
|SQLSRV\_SQLTYPE\_VARCHAR\($charCount\)|varchar|  
|SQLSRV\_SQLTYPE\_VARCHAR\('max'\)|varchar\(MAX\)|  
|SQLSRV\_SQLTYPE\_XML|xml|  
  
1.  This is a legacy type that maps to the varbinary\(max\) type.  
  
2.  This is a legacy type that maps to the newer nvarchar type.  
  
3.  This is a legacy type that maps to the newer varchar type.  
  
4.  Support for this type was added in version 1.1 of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)].  
  
The following table lists the SQLTYPE constants that accept parameters and the range of values allowed for the parameter.  
  
|SQLTYPE|Parameter|Allowable range for parameter|  
|-----------|-------------|---------------------------------|  
|SQLSRV\_SQLTYPE\_CHAR,<br /><br />SQLSRV\_SQLTYPE\_VARCHAR|charCount|1 \- 8000|  
|SQLSRV\_SQLTYPE\_NCHAR,<br /><br />SQLSRV\_SQLTYPE\_NVARCHAR|charCount|1 \- 4000|  
|SQLSRV\_SQLTYPE\_BINARY,<br /><br />SQLSRV\_SQLTYPE\_VARBINARY|byteCount|1 \- 8000|  
|SQLSRV\_SQLTYPE\_DECIMAL,<br /><br />SQLSRV\_SQLTYPE\_NUMERIC|precision|1 \- 38|  
|SQLSRV\_SQLTYPE\_DECIMAL,<br /><br />SQLSRV\_SQLTYPE\_NUMERIC|scale|1 \- precision|  
  
### Transaction Isolation Level Constants  
The **TransactionIsolation** key, which is used with [sqlsrv_connect](../content/sqlsrv_connect.md), accepts one of the following constants:  
  
-   SQLSRV\_TXN\_READ\_UNCOMMITTED  
  
-   SQLSRV\_TXN\_READ\_COMMITTED  
  
-   SQLSRV\_TXN\_REPEATABLE\_READ  
  
-   SQLSRV\_TXN\_SNAPSHOT  
  
-   SQLSRV\_TXN\_SERIALIZABLE  
  
### Cursor and Scrolling Constants  
The following constants specify the kind of cursor that you can use in a result set:  
  
-   SQLSRV\_CURSOR\_FORWARD  
  
-   SQLSRV\_CURSOR\_STATIC  
  
-   SQLSRV\_CURSOR\_DYNAMIC  
  
-   SQLSRV\_CURSOR\_KEYSET  
  
-   SQLSRV\_CURSOR\_CLIENT\_BUFFERED  
  
The following constants specify which row to select in the result set:  
  
-   SQLSRV\_SCROLL\_NEXT  
  
-   SQLSRV\_SCROLL\_PRIOR  
  
-   SQLSRV\_SCROLL\_FIRST  
  
-   SQLSRV\_SCROLL\_LAST  
  
-   SQLSRV\_SCROLL\_ABSOLUTE  
  
-   SQLSRV\_SCROLL\_RELATIVE  
  
For information on using these constants, see [Specifying a Cursor Type and Selecting Rows](../content/Specifying-a-Cursor-Type-and-Selecting-Rows.md).  
  
## See Also  
[SQLSRV Driver API Reference](../content/SQLSRV-Driver-API-Reference.md)  
  
