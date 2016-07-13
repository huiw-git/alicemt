---
title: Programming Guidelines
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0cc8686c-e27b-4963-b674-dc420fcbd3d2
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
# Programming Guidelines
The programming features of the [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] on Linux are based on ODBC in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Native Client \([SQL Server Native Client \(ODBC\)](http://go.microsoft.com/fwlink/?LinkID=134151)\). [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Native Client is based on ODBC in Windows Data Access Components \([ODBC Programmer's Reference](http://go.microsoft.com/fwlink/?LinkID=45250)\).  
  
> [!IMPORTANT]  
> These instructions refer to msodbcsql\-11.0.2270.0.tar.gz, which is the installation file for Red Hat Linux. If you are installing the CTP for SUSE Linux, the file name is msodbcsql\-11.0.2260.0.tar.gz.  
  
An ODBC application can use Multiple Active Result Sets \(MARS\) and other [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] specific features by including \/opt\/microsoft\/msodbcsql\/11.0.2270.0\/msodbcsql.h after including the unixODBC headers \(sql.h, sqlext.h, sqltypes.h, and sqlucode.h\). Then use the same symbolic names for [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] specific items that you would in your Windows ODBC applications.  
  
## Available Features  
The following sections in from the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Native Client documentation for ODBC \([SQL Server Native Client \(ODBC\)](http://go.microsoft.com/fwlink/?LinkID=134151)\) are valid when using the ODBC driver on Linux:  
  
-   [Communicating with SQL Server \(ODBC\)](http://msdn.microsoft.com/library/ms131692.aspx)  
-   [Connection and query timeout support](http://msdn.microsoft.com/library/ms130822.aspx)  
-   [cursors](http://msdn.microsoft.com/library/ms130794(SQL.110).aspx)  
-   [Date\/Time Improvements \(ODBC\)](http://msdn.microsoft.com/library/bb677319.aspx)  
-   [Executing Queries \(ODBC\)](http://msdn.microsoft.com/library/ms131677.aspx)  
-   [Handling Errors and Messages](http://msdn.microsoft.com/library/ms131289.aspx)  
-   [Kerberos authentication](http://msdn.microsoft.com/library/cc280459.aspx)  
-   [Large CLR User\-Defined Types \(ODBC\)](http://msdn.microsoft.com/library/bb677316.aspx)  
-   [Performing Transactions \(ODBC\) \(except distributed transactions\)](http://msdn.microsoft.com/library/ms131706.aspx)  
-   [Processing Results \(ODBC\)](http://msdn.microsoft.com/library/ms130812.aspx)  
-   [Running Stored Procedures](http://msdn.microsoft.com/library/ms131440.aspx)  
-   [Sparse Columns Support \(ODBC\)](http://msdn.microsoft.com/library/cc280357.aspx)  
-   [SSL encryption](http://msdn.microsoft.com/library/ms131691.aspx)  
-   [UTF\-8 and UTF\-16 for command and data API](http://msdn.microsoft.com/library/ff878241.aspx)  
-   [Using Catalog Functions](http://msdn.microsoft.com/library/ms131490.aspx)  
  
## Features That Are Not Available  
The following features are not available in this release of the ODBC driver on Linux:  
  
-   bulk copy functions \(bcp\_batch, for example\)  
-   distributed transactions \(SQL\_ATTR\_ENLIST\_IN\_DTC attribute is not supported\)  
-   database mirroring  
-   FILESTREAM  
-   profiling ODBC driver performance, discussed in [SQLSetConnectAttr](http://go.microsoft.com/fwlink/?LinkId=234099), the following performance\-related connection attributes:  
    -   SQL\_COPT\_SS\_PERF\_DATA  
    -   SQL\_COPT\_SS\_PERF\_DATA\_LOG  
    -   SQL\_COPT\_SS\_PERF\_DATA\_LOG\_NOW  
    -   SQL\_COPT\_SS\_PERF\_QUERY  
    -   SQL\_COPT\_SS\_PERF\_QUERY\_INTERVAL  
    -   SQL\_COPT\_SS\_PERF\_QUERY\_LOG  
-   SQLBrowseConnect  
-   table\-valued parameters \(TVPs\)  
-   C interval types such as SQL\_C\_INTERVAL\_YEAR\_TO\_MONTH \(documented in [Data Type Identifiers and Descriptors](http://msdn.microsoft.com/library/ms716351(VS.85).aspx)\) are not currently supported.  
-   Not supported: the SQL\_CUR\_USE\_ODBC value of the SQL\_ATTR\_ODBC\_CURSORS attribute of the SQLSetConnectAttr function.  
  
## Character Support  
SQLCHAR data must be UTF\-8. SQLWCHAR data must be UTF\-16LE \(Little Endian\).  
  
If SQLDescribeParameter does not specify a SQL type on the server, the driver uses the SQL type specified in the *ParameterType* parameter of SQLBindParameter. If a narrow character SQL type, such as SQL\_VARCHAR, is specified in SQLBindParameter, the driver converts the supplied UTF\-8 data to the default [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] code page. \(The default [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] code page is typically 1252.\) However, data loss is possible. If code page 1252 cannot represent a character, the driver converts the character to a question mark \('?'\). To avoid this data loss, specify a Unicode SQL character type, such as SQL\_NVARCHAR, in SQLBindParameter. In this case, the driver converts the supplied Unicode data in UTF\-8 encoding to UTF\-16 without loss of precision.  
  
There is a text\-encoding conversion difference between Windows and the iconv library on Linux. Text data that is encoded in codepage 1255 \(Hebrew\) has one code point \(0xCA\) that behaves differently on the two platforms. Converting to Unicode on Windows produces a UTF\-16 code point of 0x05BA. Converting to Unicode on Linux produces a UTF\-16 code point of 0x00CA. Code point 0xCA in codepage 1255 is not defined to be a character. An application should not include logic that uses the \(undefined\) code point 0xCA.  
  
When UTF\-8 multibyte characters or UTF\-16 surrogates are split across SQLPutData buffers, it results in data corruption. Use buffers for streaming SQLPutData that do not end in partial character encodings.  
  
## Other Issues  
  
1.  You can make a dedicated administrator connection \(DAC\) using [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] authentication and **host,port**. A member of the Sysadmin role first needs to discover the DAC port. For example, if the DAC port were 33000 you could connect to it with sqlcmd as follows:  
  
    ```  
    sqlcmd –U <user> -P <pwd> -S <host>,33000  
    ```  
  
2.  The UnixODBC driver manager returns "invalid attribute\/option identifier" for all statement attributes when they are passed through SQLSetConnectAttr. On Windows, when SQLSetConnectAttr receives a statement attribute value, it causes the driver to set that value on all active statements that are children of the connection handle.  
  
    > [!NOTE]  
    > DAC connections must use [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Authentication.  
  
## See Also  
[Microsoft ODBC Driver for SQL Server on Linux](../content/Microsoft-ODBC-Driver-for-SQL-Server-on-Linux.md)  
  
