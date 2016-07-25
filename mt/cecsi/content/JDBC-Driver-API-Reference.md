---
title: "JDBC Driver API Reference"
ms.custom: na
ms.date: 07/22/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e4e1ae9d-18a6-41db-8bd2-9cf0eee4cccb
caps.latest.revision: 46
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
# JDBC Driver API Reference
  The [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] provides an API that can be used within Java programming code to connect to and interact with a [!INCLUDE[msCoName](../content/includes/msCoName_md.md)][!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database.  
  
> [!NOTE]  
>  For conceptual information about using the JDBC driver, see [Overview of the JDBC Driver](../content/Overview-of-the-JDBC-Driver.md).  
  
> [!IMPORTANT]  
>  For JDBC 4.1 and 4.2 compliance support, use Microsoft JDBC Driver 4.2 (or higher) for SQL Server. The previous Microsoft JDBC Drivers 4.1 and 4.0 releases do not support new methods introduced with JDBC 4.1 or 4.2.  
>   
>  API details for JDBC 4.1 compliance are not in this section. See [JDBC 4.1 Compliance for the JDBC Driver](../content/JDBC-4.1-Compliance-for-the-JDBC-Driver.md).  
>   
>  API details for JDBC 4.2 compliance are not found in this section. See [JDBC 4.2 Compliance for the JDBC Driver](../content/JDBC-4.2-Compliance-for-the-JDBC-Driver.md).  
>   
>  API details for Bulk Copy, available starting with Microsoft JDBC Driver 4.2  for SQL Server, are not found in this section. See [Using Bulk Copy with the JDBC Driver](../content/Using-Bulk-Copy-with-the-JDBC-Driver.md).  
>   
>  API details for Always Encrypted, available starting with  Microsoft JDBC Driver 6.0 for SQL Server, are not found in this section. See [Always Encrypted API Reference for the JDBC Driver](../content/Always-Encrypted-API-Reference-for-the-JDBC-Driver.md)  
>   
>  API details for Using Table-Valued Parameters, available starting with  Microsoft JDBC Driver 6.0 for SQL Server, are not found in this section. See [Using Table-Valued Parameters](../content/Using-Table-Valued-Parameters.md)  
>   
>  Microsoft JDBC Drivers 6.0 and 4.2 support compilation with JDK 5.0, 6.0, 7.0, and 8.0.  
>   
>  Microsoft JDBC Driver 4.1 supports compilation with JDK 5.0, 6.0, and 7.0.  
>   
>  Microsoft JDBC Driver 4.0 supports compilation with JDK 5.0 and 6.0.  
  
## Interfaces  
  
|Interface Name|Description|  
|--------------------|-----------------|  
|[ISQLServerCallableStatement Interface](../content/ISQLServerCallableStatement-Interface.md)|Lets you specify the stored procedure name to call along with input and output parameters.|  
|[ISQLServerConnection Interface](../content/ISQLServerConnection-Interface.md)|Represents a JDBC connection to a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database.|  
|[SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)|Represents a list of properties specific to connecting to a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database by using a [ISQLServerConnection](../content/SQLServerConnection-Class.md) object.|  
|[ISQLServerPreparedStatement](../content/ISQLServerPreparedStatement-Interface.md)|Represents the basic implementation of JDBC prepared statement functionality.|  
|[ISQLServerResultSet](../content/ISQLServerResultSet-Interface.md)|Represents a JDBC result set.|  
|[ISQLServerStatement](../content/ISQLServerStatement-Interface.md)|Represents the basic implementation of JDBC statement functionality.|  
  
## Classes  
  
|Class Name|Description|  
|----------------|-----------------|  
|[DateTimeOffset](../content/DateTimeOffset-Class.md)|Represents an object of type microsoft.sql.DateTimeOffset.|  
|[SQLServerBlob](../content/SQLServerBlob-Class.md)|Represents a binary large object (BLOB).|  
|[SQLServerCallableStatement](../content/SQLServerCallableStatement-Class.md)|Implements ISQLServerCallableStatement.|  
|[SQLServerClob](../content/SQLServerClob-Class.md)|Represents a character large binary object (CLOB).|  
|[SQLServerConnection](../content/SQLServerConnection-Class.md)|Implements ISQLServerConnectopn.|  
|[SQLServerConnectionPoolDataSource](../content/SQLServerConnectionPoolDataSource-Class.md)|Represents physical database connections for connection pool managers.|  
|[SQLServerDatabaseMetaData](../content/SQLServerDatabaseMetaData-Class.md)|Represents the metadata for the database.|  
|[SQLServerDataSource](../content/ISQLServerDataSource-Interface.md)|Represents a list of properties specific to connecting to a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database by using a [SQLServerConnection](../content/SQLServerConnection-Class.md) object.|  
|[SQLServerDataSourceObjectFactory](../content/SQLServerDataSourceObjectFactory-Class.md)|Represents an object factory to materialize data sources from the Java Naming and Directory Interface (JNDI).|  
|[SQLServerDriver](../content/SQLServerDriver-Class.md)|Represents the JDBC driver. This class includes methods for connecting to a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database, and for obtaining information about the JDBC driver.|  
|[SQLServerException](../content/SQLServerException-Class.md)|Represents an unsuccessful or incomplete running of an SQL statement.|  
|[SQLServerNClob Class](../content/SQLServerNClob-Class.md)|Represents a character large binary object using the National Character Set.|  
|[SQLServerParameterMetaData](../content/SQLServerParameterMetaData-Class.md)|Represents the metadata for prepared statement parameters.|  
|[SQLServerPooledConnection](../content/SQLServerPooledConnection-Class.md)|Represents a physical database connection in a connection pool.|  
|[SQLServerPreparedStatement](../content/SQLServerPreparedStatement-Class.md)|Implements ISQLServerPreparedStatement.|  
|[SQLServerResource](../content/SQLServerResource-Class.md)|Represents a localized error string resource. This class is intended for internal use only.|  
|[SQLServerResultSet](../content/SQLServerResultSet-Class.md)|Implements ISQLServerResultSet.|  
|[SQLServerResultSetMetaData](../content/SQLServerResultSetMetaData-Class.md)|Represents the metadata of the columns that are contained within a result set.|  
|[SQLServerSavepoint](../content/SQLServerSavepoint-Class.md)|Represents the checkpoint to which a transaction can be rolled back.|  
|[SQLServerStatement](../content/SQLServerStatement-Class.md)|Implements ISQLServerStatement.|  
|[SQLServerXAConnection](../content/SQLServerXAConnection-Class.md)|Represents JDBC connections that can participate in distributed (XA) transactions.|  
|[SQLServerXADataSource](../content/SQLServerXADataSource-Class.md)|Represents a factory for [SQLServerXAConnection](../content/SQLServerXAConnection-Class.md) objects that is used internally.|  
|[SQLServerXAResource](../content/SQLServerXAResource-Class.md)|Represents an XAResource for XA distributed transaction management.|  
  
## See Also  
 [Overview of the JDBC Driver](../content/Overview-of-the-JDBC-Driver.md)  
  
  