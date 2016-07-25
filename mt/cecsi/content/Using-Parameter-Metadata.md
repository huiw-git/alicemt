---
title: "Using Parameter Metadata"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: db2c1957-91c6-4989-a07b-9f8be6d2033a
caps.latest.revision: 17
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
# Using Parameter Metadata
  To query a [SQLServerPreparedStatement](../content/SQLServerPreparedStatement-Class.md) or a [SQLServerCallableStatement](../content/SQLServerCallableStatement-Class.md) object about the parameters that they contain, the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] implements the [SQLServerParameterMetaData](../content/SQLServerParameterMetaData-Class.md) class. This class contains numerous fields and methods that return information in the form of a single value.  
  
 To create a SQLServerParameterMetaData object, you can use the [getParameterMetaData](../content/getParameterMetaData-Method--SQLServerPreparedStatement-.md) methods of the SQLServerPreparedStatement and SQLServerCallableStatement classes.  
  
 In the following example, an open connection to the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database is passed in to the function, the getParameterMetaData method of the SQLServerCallableStatement class is used to return a SQLServerParameterMetaData object, and then various methods of the SQLServerParameterMetaData object are used to display information about the type and mode of the parameters that are contained within the HumanResources.uspUpdateEmployeeHireInfo stored procedure.  
  
 [!CODE [JDBC#UsingParamMetaData1](../CodeSnippet/SQLDrivers/jdbc#usingparammetadata1)]  
    
> [!NOTE]  
There are some limitations when using the SQLServerParameterMetaData class with prepared statements. 
**With Microsoft JDBC Driver 6.0 (or higher) for SQL Server**: 
When using SQL Server 2008 or 2008 R2, the JDBC driver supports SELECT, DELETE, INSERT, and UPDATE statements as long as these statements does not contain subqueries and/or joins. MERGE queries are also not supported for  SQLServerParameterMetaData class when using SQL Server 2008 or 2008 R2. For SQL Server 2012 and higher versions parameter metadata with complex queries are supported. Retrieval of parameter metadata for encrypted columns are not supported. **With Microsoft JDBC Driver 4.0, 4.1 or 4.2 for SQL Server**: The JDBC driver supports SELECT, DELETE, INSERT, and UPDATE statements as long as these statements does not contain subqueries and/or joins. MERGE queries are also not supported for  SQLServerParameterMetaData class.  

## See Also  
 [Handling Metadata with the JDBC Driver](../content/Handling-Metadata-with-the-JDBC-Driver.md)  
  
  