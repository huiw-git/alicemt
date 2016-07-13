---
title: Using Basic Data Types
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d7044936-5b8c-4def-858c-28a11ef70a97
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
  - sv-se
  - zh-cn
  - zh-tw
---
# Using Basic Data Types
  The [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] uses the JDBC basic data types to convert the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data types to a format that can be understood by the Java programming language, and vice versa. The JDBC driver provides support for the JDBC 4.0 API, which includes the **SQLXML** data type, and National \(Unicode\) data types, such as **NCHAR**, **NVARCHAR**, **LONGNVARCHAR**, and **NCLOB**.  
  
## Data Type Mappings  
 The following table lists the default mappings between the basic [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)], JDBC, and Java programming language data types:  
  
|SQL Server Types|JDBC Types \(java.sql.Types\)|Java Language Types|  
|----------------------|-----------------------------------|-------------------------|  
|bigint|BIGINT|long|  
|binary|BINARY|byte\[\]|  
|bit|BIT|boolean|  
|char|CHAR|String|  
|date|DATE|java.sql.Date|  
|datetime|TIMESTAMP|java.sql.Timestamp|  
|datetime2|TIMESTAMP|java.sql.Timestamp|  
|datetimeoffset \(2\)|microsoft.sql.Types.DATETIMEOFFSET|microsoft.sql.DateTimeOffset|  
|decimal|DECIMAL|java.math.BigDecimal|  
|float|DOUBLE|double|  
|image|LONGVARBINARY|byte\[\]|  
|int|INTEGER|int|  
|money|DECIMAL|java.math.BigDecimal|  
|nchar|CHAR<br /><br /> NCHAR \(Java SE 6.0\)|String|  
|ntext|LONGVARCHAR<br /><br /> LONGNVARCHAR \(Java SE 6.0\)|String|  
|numeric|NUMERIC|java.math.BigDecimal|  
|nvarchar|VARCHAR<br /><br /> NVARCHAR \(Java SE 6.0\)|String|  
|nvarchar\(max\)|VARCHAR<br /><br /> NVARCHAR \(Java SE 6.0\)|String|  
|real|REAL|float|  
|smalldatetime|TIMESTAMP|java.sql.Timestamp|  
|smallint|SMALLINT|short|  
|smallmoney|DECIMAL|java.math.BigDecimal|  
|text|LONGVARCHAR|String|  
|time|TIME \(1\)|java.sql.Time \(1\)|  
|timestamp|BINARY|byte\[\]|  
|tinyint|TINYINT|short|  
|udt|VARBINARY|byte\[\]|  
|uniqueidentifier|CHAR|String|  
|varbinary|VARBINARY|byte\[\]|  
|varbinary\(max\)|VARBINARY|byte\[\]|  
||||  
|varchar|VARCHAR|String|  
|varchar\(max\)|VARCHAR|String|  
|xml|LONGVARCHAR<br /><br /> LONGNVARCHAR \(Java SE 6.0\)|String<br /><br /> SQLXML|  
  
 \(1\) To use java.sql.Time with the time [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] type, you must set the **sendTimeAsDatetime** connection property to false.  
  
 \(2\) You can programmatically access values of **datetimeoffset** with [DateTimeOffset Class](../content/DateTimeOffset-Class.md).  
  
 The [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] sqlvariant data type is not currently supported by the JDBC driver. If a query is used to retrieve data from a table that contains a column of the sqlvariant data type, an exception will occur.  
  
 The following sections provide examples of how you can use the JDBC Driver and the basic data types. For a more detailed example of how to use the basic data types in a Java application, see [Basic Data Types Sample](../content/Basic-Data-Types-Sample.md).  
  
## Retrieving Data as a String  
 If you have to retrieve data from a data source that maps to any of the JDBC basic data types for viewing as a string, or if strongly typed data is not required, you can use the [getString](../content/getString-Method--SQLServerResultSet-.md) method of the [SQLServerResultSet](../content/SQLServerResultSet-Class.md) class, as in the following:  
  
 [!CODE [JDBC#UsingBasicDataTypes1](../CodeSnippet/SQLDrivers/jdbc#usingbasicdatatypes1)]  
  
## Retrieving Data by Data Type  
 If you have to retrieve data from a data source, and you know the type of data that is being retrieved, use one of the get\<Type\> methods of the SQLServerResultSet class, also known as the *getter methods*. You can use either a column name or a column index with the get\<Type\> methods, as in the following:  
  
 [!CODE [JDBC#UsingBasicDataTypes2](../CodeSnippet/SQLDrivers/jdbc#usingbasicdatatypes2)]  
  
> [!NOTE]  
>  The getUnicodeStream and getBigDecimal with scale methods are deprecated and are not supported by the JDBC driver.  
  
## Updating Data by Data Type  
 If you have to update the value of a field in a data source, use one of the update\<Type\> methods of the SQLServerResultSet class. In the following example, the [updateInt](../content/updateInt-Method--SQLServerResultSet-.md) method is used in conjunction with the [updateRow](../content/updateRow-Method--SQLServerResultSet-.md) method to update the data in the data source:  
  
 [!CODE [JDBC#UsingBasicDataTypes3](../CodeSnippet/SQLDrivers/jdbc#usingbasicdatatypes3)]  
  
> [!NOTE]  
>  The JDBC driver cannot update a SQL Server column with a column name that is more than 127 characters long. If an update to a column whose name is more than 127 characters is attempted, an exception is thrown.  
  
## Updating Data by Parameterized Query  
 If you have to update data in a data source by using a parameterized query, you can set the data type of the parameters by using one of the set\<Type\> methods of the [SQLServerPreparedStatement](../content/SQLServerPreparedStatement-Class.md) class, also known as the *setter methods*. In the following example, the [prepareStatement](../content/prepareStatement-Method--SQLServerConnection-.md) method is used to pre\-compile the parameterized query, and then the [setString](../content/setString-Method--SQLServerPreparedStatement-.md) method is used to set the string value of the parameter before the [executeUpdate](../content/executeUpdate-Method---.md) method is called.  
  
 [!CODE [JDBC#UsingBasicDataTypes4](../CodeSnippet/SQLDrivers/jdbc#usingbasicdatatypes4)]  
  
 For more information about parameterized queries, see [Using an SQL Statement with Parameters](../content/Using-an-SQL-Statement-with-Parameters.md).  
  
## Passing Parameters to a Stored Procedure  
 If you have to pass typed parameters into a stored procedure, you can set the parameters by index or name by using one of the set\<Type\> methods of the [SQLServerCallableStatement](../content/SQLServerCallableStatement-Class.md) class. In the following example, the [prepareCall](../content/prepareCall-Method--SQLServerConnection-.md) method is used to set up the call to the stored procedure, and then the [setString](../content/setString-Method--SQLServerCallableStatement-.md) method is used to set the parameter for the call before the [executeQuery](../content/executeQuery-Method--SQLServerStatement-.md) method is called.  
  
 [!CODE [JDBC#UsingBasicDataTypes5](../CodeSnippet/SQLDrivers/jdbc#usingbasicdatatypes5)]  
  
> [!NOTE]  
>  In this example, a result set is returned with the results of running the stored procedure.  
  
 For more information about using the JDBC driver with stored procedures and input parameters, see [Using a Stored Procedure with Input Parameters](../content/Using-a-Stored-Procedure-with-Input-Parameters.md).  
  
## Retrieving Parameters from a Stored Procedure  
 If you have to retrieve parameters back from a stored procedure, you must first register an out parameter by name or index by using the [registerOutParameter](../content/registerOutParameter-Method--SQLServerCallableStatement-.md) method of the SQLServerCallableStatement class, and then assign the returned out parameter to an appropriate variable after you run the call to the stored procedure. In the following example, the prepareCall method is used to set up the call to the stored procedure, the registerOutParameter method is used to set up the out parameter, and then the [setString](../content/setString-Method--SQLServerCallableStatement-.md) method is used to set the parameter for the call before executeQuery method is called. The value that is returned by the out parameter of the stored procedure is retrieved by using the [getShort](../content/getShort-Method--SQLServerCallableStatement-.md) method.  
  
 [!CODE [JDBC#UsingBasicDataTypes6](../CodeSnippet/SQLDrivers/jdbc#usingbasicdatatypes6)]  
  
> [!NOTE]  
>  In addition to the returned out parameter, a result set might also be returned with the results of running the stored procedure.  
  
 For more information about how to use the JDBC driver with stored procedures and output parameters, see [Using a Stored Procedure with Output Parameters](../content/Using-a-Stored-Procedure-with-Output-Parameters.md).  
  
## See Also  
 [Understanding the JDBC Driver Data Types](../content/Understanding-the-JDBC-Driver-Data-Types.md)  
  
  