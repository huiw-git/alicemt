---
title: "Constants (Microsoft Drivers for PHP for SQL Server)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9727c944-b645-48d6-9012-18dbde35ee3c
caps.latest.revision: 70
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
  
## PDO_SQLSRV Driver Constants  
The constants listed on the [PDO website](http://go.microsoft.com/fwlink/?LinkID=187441) are valid in the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)].  
  
The following describe the Microsoft specific constants in the PDO_SQLSRV driver.  
  
### Transaction Isolation Level Constants  
The **TransactionIsolation** key, which is used with [PDO::__construct](../Topic/PDO::__construct.md), accepts one of the following constants:  
  
-   PDO::SQLSRV_TXN_READ_UNCOMMITTED  
  
-   PDO::SQLSRV_TXN_READ_COMMITTED  
  
-   PDO::SQLSRV_TXN_REPEATABLE_READ  
  
-   PDO::SQLSRV_TXN_SNAPSHOT  
  
-   PDO::SQLSRV_TXN_SERIALIZABLE  
  
For more information about the **TransactionIsolation** key, see [Connection Options](../content/Connection-Options.md).  
  
### Encoding Constants  
The PDO::SQLSRV_ATTR_ENCODING attribute can be passed to [PDOStatement::setAttribute](../Topic/PDOStatement::setAttribute.md), [PDO::setAttribute](../Topic/PDO::setAttribute.md), [PDO::prepare](../Topic/PDO::prepare.md), [PDOStatement::bindColumn](../Topic/PDOStatement::bindColumn.md), and [PDOStatement::bindParam](../Topic/PDOStatement::bindParam.md).  
  
The available values to pass to PDO::SQLSRV_ATTR_ENCODING are  
  
|PDO_SQLSRV driver constant|Description|  
|-------------------------------|---------------|  
|PDO::SQLSRV_ENCODING_BINARY|Data is a raw byte stream from the server without performing encoding or translation.<br /><br />Not valid for PDO::setAttribute.|  
|PDO::SQLSRV_ENCODING_SYSTEM|Data is 8-bit characters as specified in the code page of the Windows locale that is set on the system. Any multi-byte characters or characters that do not map into this code page are substituted with a single byte question mark (?) character.|  
|PDO::SQLSRV_ENCODING_UTF8|Data is in the UTF-8 encoding. This is the default encoding.|  
|PDO::SQLSRV_ENCODING_DEFAULT|Uses PDO::SQLSRV_ENCODING_SYSTEM if specified during connection.<br /><br />Use the connection’s encoding if specified in a prepare statement.|  
  
### Query Timeout  
The PDO::SQLSRV_ATTR_QUERY_TIMEOUT attribute is any non-negative integer representing the timeout period, in seconds. Zero (0) is the default and means no timeout.  
  
You can specify the PDO::SQLSRV_ATTR_QUERY_TIMEOUT attribute with [PDOStatement::setAttribute](../Topic/PDOStatement::setAttribute.md), [PDO::setAttribute](../Topic/PDO::setAttribute.md), and [PDO::prepare](../Topic/PDO::prepare.md).  
  
### Direct or Prepared Execution  
You can select direct query execution or prepared statement execution with the PDO::SQLSRV_ATTR_DIRECT_QUERY attribute. PDO::SQLSRV_ATTR_DIRECT_QUERY can be set with [PDO::prepare](../Topic/PDO::prepare.md) or [PDO::setAttribute](../Topic/PDO::setAttribute.md). For more information about PDO::SQLSRV_ATTR_DIRECT_QUERY, see [Direct Statement Execution and Prepared Statement Execution in the PDO_SQLSRV Driver](../content/Direct-Statement-Execution-and-Prepared-Statement-Execution-in-the-PDO_SQLSRV-Driver.md).  
  
## SQLSRV Driver Constants  
The following sections list the constants used by the SQLSRV driver.  
  
### ERR Constants  
The following table lists the constants that are used to specify if [sqlsrv_errors](../content/sqlsrv_errors.md) returns errors, warnings, or both.  
  
|Value|Description|  
|---------|---------------|  
|SQLSRV_ERR_ALL|Errors and warnings generated on the last **sqlsrv** function call are returned. This is the default value.|  
|SQLSRV_ERR_ERRORS|Errors generated on the last **sqlsrv** function call are returned.|  
|SQLSRV_ERR_WARNINGS|Warnings generated on the last **sqlsrv** function call are returned.|  
  
### FETCH Constants  
The following table lists the constants that are used to specify the type of array returned by [sqlsrv_fetch_array](../content/sqlsrv_fetch_array.md).  
  
|SQLSRV constant|Description|  
|-------------------|---------------|  
|SQLSRV_FETCH_ASSOC|**sqlsrv_fetch_array** returns the next row of data as an associative array.|  
|SQLSRV_FETCH_BOTH|**sqlsrv_fetch_array** returns the next row of data as an array with both numeric and associative keys. This is the default value.|  
|SQLSRV_FETCH_NUMERIC|**sqlsrv_fetch_array** returns the next row of data as a numerically indexed array.|  
  
### Logging Constants  
This section lists the constants that are used to change the logging settings with [sqlsrv_configure](../content/sqlsrv_configure.md). For more information about logging activity, see [Logging Activity](../content/Logging-Activity.md).  
  
The following table lists the constants that can be used as the value for the **LogSubsystems** setting:  
  
|SQLSRV constant (integer equivalent in paraentheses)|Description|  
|----------------------------------------------------------|---------------|  
|SQLSRV_LOG_SYSTEM_ALL (-1)|Turns on logging of all subsystems.|  
|SQLSRV_LOG_SYSTEM_CONN (2)|Turns on logging of connection activity.|  
|SQLSRV_LOG_SYSTEM_INIT (1)|Turns on logging of initialization activity.|  
|SQLSRV_LOG_SYSTEM_OFF (0)|Turns logging off.|  
|SQLSRV_LOG_SYSTEM_STMT (4)|Turns on logging of statement activity.|  
|SQLSRV_LOG_SYSTEM_UTIL (8)|Turns on logging of error functions activity (such as **handle_error** and **handle_warning**).|  
  
The following table lists the constants that can be used as the value for the **LogSeverity** setting:  
  
|SQLSRV constant (integer equivalent in paraentheses)|Description|  
|----------------------------------------------------------|---------------|  
|SQLSRV_LOG_SEVERITY_ALL (-1)|Specifies that errors, warnings, and notices will be logged.|  
|SQLSRV_LOG_SEVERITY_ERROR (1)|Specifies that errors will be logged.|  
|SQLSRV_LOG_SEVERITY_NOTICE (4)|Specifies that notices will be logged.|  
|SQLSRV_LOG_SEVERITY_WARNING (2)|Specifies that warnings will be logged.|  
  
### Nullable Constants  
The following table lists the constants that you can use to determine whether or not a column is nullable or if this information is not available. You can compare the value of the **Nullable** key that is returned by [sqlsrv_field_metadata](../content/sqlsrv_field_metadata.md) to determine the column's nullable status.  
  
|SQLSRV constant (integer equivalent in paraentheses)|Description|  
|----------------------------------------------------------|---------------|  
|SQLSRV_NULLABLE_YES (0)|The column is nullable.|  
|SQLSRV_NULLABLE_NO (1)|The column is not nullable.|  
|SQLSRV_NULLABLE_UNKNOWN (2)|It is not known if the column is nullable.|  
  
### PARAM Constants  
The following list contains the constants for specifying parameter direction when you call [sqlsrv_query](../content/sqlsrv_query.md) or [sqlsrv_prepare](../content/sqlsrv_prepare.md).  
  
|SQLSRV constant|Description|  
|-------------------|---------------|  
|SQLSRV_PARAM_IN|Indicates an input parameter.|  
|SQLSRV_PARAM_INOUT|Indicates a bidirectional parameter.|  
|SQLSRV_PARAM_OUT|Indicates an output parameter.|  
  
### PHPTYPE Constants  
The following table lists the constants that are used to describe PHP data types. For information about PHP data types, see [PHP Types](http://go.microsoft.com/fwlink/?LinkId=104881).  
  
|SQLSRV constant|PHP data type|  
|-------------------|-----------------|  
|SQLSRV_PHPTYPE_INT|Integer|  
|SQLSRV_PHPTYPE_DATETIME|Datetime|  
|SQLSRV_PHPTYPE_FLOAT|Float|  
|SQLSRV_PHPTYPE_STREAM(<encoding><sup>1</sup>)|Stream|  
|SQLSRV_PHPTYPE_STRING(<encoding><sup>1</sup>)|String|  
  
1. **SQLSRV_PHPTYPE_STREAM** and **SQLSRV_PHPTYPE_STRING** accept a parameter that specifies the stream encoding. The following table contains the SQLSRV constants that are acceptable parameters, and a description of the corresponding encoding.  
  
|SQLSRV constant|Description|  
|-------------------|---------------|  
|SQLSRV_ENC_BINARY|Data is returned as a raw byte stream from the server without performing encoding or translation.|  
|SQLSRV_ENC_CHAR|Data is returned in 8-bit characters as specified in the code page of the Windows locale that is set on the system. Any multi-byte characters or characters that do not map into this code page are substituted with a single byte question mark (?) character.<br /><br />This is the default encoding.|  
|"UTF-8"|Data is returned in the UTF-8 encoding. This constant was added in version 1.1 of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)]. For more information about UTF-8 support, see [How to: Send and Retrieve UTF-8 Data Using Built-In UTF-8 Support](../Topic/How%20to:%20Send%20and%20Retrieve%20UTF-8%20Data%20Using%20Built-In%20UTF-8%20Support.md).|  
  
> [!NOTE]  
> When you use **SQLSRV_PHPTYPE_STREAM** or **SQLSRV_PHPTYPE_STRING**, the encoding must be specified. If no parameter is supplied, an error will be returned.  
  
For more information about these constants, see [How to: Specify PHP Data Types](../Topic/How%20to:%20Specify%20PHP%20Data%20Types.md), [How to: Retrieve Character Data as a Stream Using the SQLSRV Driver](../Topic/How%20to:%20Retrieve%20Character%20Data%20as%20a%20Stream%20Using%20the%20SQLSRV%20Driver.md).  
  
### SQLTYPE Constants  
The following table lists the constants that are used to describe SQL Server data types. Some constants require parameters that correspond to precision, scale, and/or length. For information about SQL Server data types, see [Data Types (Transact-SQL).](http://go.microsoft.com/fwlink/?LinkId=104883) For information about precision, scale, and length, see [Precision, Scale, and Length (Transact-SQL).](http://go.microsoft.com/fwlink/?LinkId=104885)  
  
|SQLSRV constant|SQL Server data type|  
|-------------------|------------------------|  
|SQLSRV_SQLTYPE_BIGINT|bigint|  
|SQLSRV_SQLTYPE_BINARY|binary|  
|SQLSRV_SQLTYPE_BIT|bit|  
|SQLSRV_SQLTYPE_CHAR($charCount)|char|  
|SQLSRV_SQLTYPE_DATE|date<sup>4</sup>|  
|SQLSRV_SQLTYPE_DATETIME|datetime|  
|SQLSRV_SQLTYPE_DATETIME2|datetime2<sup>4</sup>|  
|SQLSRV_SQLTYPE_DATETIMEOFFSET|datetimeoffset<sup>4</sup>|  
|SQLSRV_SQLTYPE_DECIMAL($precision, $scale)|decimal|  
|SQLSRV_SQLTYPE_FLOAT|float|  
|SQLSRV_SQLTYPE_IMAGE|image<sup>1</sup>|  
|SQLSRV_SQLTYPE_INT|int|  
|SQLSRV_SQLTYPE_MONEY|money|  
|SQLSRV_SQLTYPE_NCHAR($charCount)|nchar|  
|SQLSRV_SQLTYPE_NUMERIC($precision, $scale)|numeric|  
|SQLSRV_SQLTYPE_NVARCHAR($charCount)|nvarchar|  
|SQLSRV_SQLTYPE_NVARCHAR('max')|nvarchar(MAX)|  
|SQLSRV_SQLTYPE_NTEXT|ntext<sup>2</sup>|  
|SQLSRV_SQLTYPE_REAL|real|  
|SQLSRV_SQLTYPE_SMALLDATETIME|smalldatetime|  
|SQLSRV_SQLTYPE_SMALLINT|smallint|  
|SQLSRV_SQLTYPE_SMALLMONEY|smallmoney|  
|SQLSRV_SQLTYPE_TEXT|text<sup>3</sup>|  
|SQLSRV_SQLTYPE_TIME|time<sup>4</sup>|  
|SQLSRV_SQLTYPE_TIMESTAMP|timestamp|  
|SQLSRV_SQLTYPE_TINYINT|tinyint|  
|SQLSRV_SQLTYPE_UNIQUEIDENTIFIER|uniqueidentifier|  
|SQLSRV_SQLTYPE_UDT|UDT|  
|SQLSRV_SQLTYPE_VARBINARY($byteCount)|varbinary|  
|SQLSRV_SQLTYPE_VARBINARY('max')|varbinary(MAX)|  
|SQLSRV_SQLTYPE_VARCHAR($charCount)|varchar|  
|SQLSRV_SQLTYPE_VARCHAR('max')|varchar(MAX)|  
|SQLSRV_SQLTYPE_XML|xml|  
  
1.  This is a legacy type that maps to the varbinary(max) type.  
  
2.  This is a legacy type that maps to the newer nvarchar type.  
  
3.  This is a legacy type that maps to the newer varchar type.  
  
4.  Support for this type was added in version 1.1 of the [!INCLUDE[ssDriverPHP](../content/includes/ssDriverPHP_md.md)].  
  
The following table lists the SQLTYPE constants that accept parameters and the range of values allowed for the parameter.  
  
|SQLTYPE|Parameter|Allowable range for parameter|  
|-----------|-------------|---------------------------------|  
|SQLSRV_SQLTYPE_CHAR,<br /><br />SQLSRV_SQLTYPE_VARCHAR|charCount|1 - 8000|  
|SQLSRV_SQLTYPE_NCHAR,<br /><br />SQLSRV_SQLTYPE_NVARCHAR|charCount|1 - 4000|  
|SQLSRV_SQLTYPE_BINARY,<br /><br />SQLSRV_SQLTYPE_VARBINARY|byteCount|1 - 8000|  
|SQLSRV_SQLTYPE_DECIMAL,<br /><br />SQLSRV_SQLTYPE_NUMERIC|precision|1 - 38|  
|SQLSRV_SQLTYPE_DECIMAL,<br /><br />SQLSRV_SQLTYPE_NUMERIC|scale|1 - precision|  
  
### Transaction Isolation Level Constants  
The **TransactionIsolation** key, which is used with [sqlsrv_connect](../content/sqlsrv_connect.md), accepts one of the following constants:  
  
-   SQLSRV_TXN_READ_UNCOMMITTED  
  
-   SQLSRV_TXN_READ_COMMITTED  
  
-   SQLSRV_TXN_REPEATABLE_READ  
  
-   SQLSRV_TXN_SNAPSHOT  
  
-   SQLSRV_TXN_SERIALIZABLE  
  
### Cursor and Scrolling Constants  
The following constants specify the kind of cursor that you can use in a result set:  
  
-   SQLSRV_CURSOR_FORWARD  
  
-   SQLSRV_CURSOR_STATIC  
  
-   SQLSRV_CURSOR_DYNAMIC  
  
-   SQLSRV_CURSOR_KEYSET  
  
-   SQLSRV_CURSOR_CLIENT_BUFFERED  
  
The following constants specify which row to select in the result set:  
  
-   SQLSRV_SCROLL_NEXT  
  
-   SQLSRV_SCROLL_PRIOR  
  
-   SQLSRV_SCROLL_FIRST  
  
-   SQLSRV_SCROLL_LAST  
  
-   SQLSRV_SCROLL_ABSOLUTE  
  
-   SQLSRV_SCROLL_RELATIVE  
  
For information on using these constants, see [Specifying a Cursor Type and Selecting Rows](../content/Specifying-a-Cursor-Type-and-Selecting-Rows.md).  
  
## See Also  
[SQLSRV Driver API Reference](../content/SQLSRV-Driver-API-Reference.md)  
  
