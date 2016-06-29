---
title: SQLServerResultSetMetaData Members
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 37587981-2979-49a3-a6ab-df4bfb9b8748
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
# SQLServerResultSetMetaData Members
  The following tables list the members that are exposed by the [SQLServerResultSetMetaData](../content/SQLServerResultSetMetaData-Class.md) class.  
  
## Constructors  
 None.  
  
## Fields  
 None.  
  
## Inherited Fields  
  
|Name|Description|  
|----------|-----------------|  
|java.sql.ResultSetMetaData|columnNoNulls, columnNullable, columnNullableUnknown|  
  
## Methods  
  
|Name|Description|  
|----------|-----------------|  
|[getCatalogName](../content/getCatalogName-Method--SQLServerResultSetMetaData-.md)|Gets the catalog name for the table that includes the designated column.|  
|[getColumnClassName](../content/getColumnClassName-Method--SQLServerResultSetMetaData-.md)|Returns the fully\-qualified name of the Java class whose instances are manufactured if the [getObject](../content/getObject-Method--SQLServerResultSet-.md) method of the [SQLServerResultSet](../content/SQLServerResultSet-Class.md) class is called to retrieve a value from the column.|  
|[getColumnCount](../content/getColumnCount-Method--SQLServerResultSetMetaData-.md)|Returns the number of columns in the result set.|  
|[getColumnDisplaySize](../content/getColumnDisplaySize-Method--SQLServerResultSetMetaData-.md)|Returns the normal maximum width, in characters, of the designated column.|  
|[getColumnLabel](../content/getColumnLabel-Method--SQLServerResultSetMetaData-.md)|Gets the title that is suggested for use in printouts and displays of the designated column.|  
|[getColumnName](../content/getColumnName-Method--SQLServerResultSetMetaData-.md)|Get the name of the designated column.|  
|[getColumnType](../content/getColumnType-Method--SQLServerResultSetMetaData-.md)|Retrieves the SQL type of the designated column.|  
|[getColumnTypeName](../content/getColumnTypeName-Method--SQLServerResultSetMetaData-.md)|Retrieves the database\-specific type name of the designated column.|  
|[getPrecision](../content/getPrecision-Method--SQLServerResultSetMetaData-.md)|Get the number of decimal digits for the designated column.|  
|[getScale](../content/getScale-Method--SQLServerResultSetMetaData-.md)|Gets the number of digits to the right of the decimal point for the designated column.|  
|[getSchemaName](../content/getSchemaName-Method--SQLServerResultSetMetaData-.md)|Gets the table schema name for the designated column.|  
|[getTableName](../content/getTableName-Method--SQLServerResultSetMetaData-.md)|Gets the table name of the designated column.|  
|[isAutoIncrement](../content/isAutoIncrement-Method--SQLServerResultSetMetaData-.md)|Indicates whether the designated column is automatically numbered, which makes it read\-only.|  
|[isCaseSensitive](../content/isCaseSensitive-Method--SQLServerResultSetMetaData-.md)|Indicates whether a column is case sensitive.|  
|[isCurrency](../content/isCurrency-Method--SQLServerResultSetMetaData-.md)|Indicates whether the designated column is a cash value.|  
|[isDefinitelyWritable](../content/isDefinitelyWritable-Method--SQLServerResultSetMetaData-.md)|Indicates whether a write on the designated column will definitely succeed.|  
|[isNullable](../content/isNullable-Method--SQLServerResultSetMetaData-.md)|Indicates the nullability of values in the designated column.|  
|[isReadOnly](../content/isReadOnly-Method--SQLServerResultSetMetaData-.md)|Indicates whether the designated column is definitely not writable.|  
|[isSearchable](../content/isSearchable-Method--SQLServerResultSetMetaData-.md)|Indicates whether the designated column can be used in an SQL WHERE clause.|  
|[isSigned](../content/isSigned-Method--SQLServerResultSetMetaData-.md)|Indicates whether values in the designated column are signed numbers.|  
|[isSparseColumnSet](../content/isSparseColumnSet-Method--SQLServerResultSetMetaData-.md)|Indicates if a column in a result set is a sparse column set.|  
|[isWritable](../content/isWritable-Method--SQLServerResultSetMetaData-.md)|Indicates whether it is possible for a write on the designated column to succeed.|  
  
## Inherited Methods  
  
|Class inherited from:|Methods|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## See Also  
 [SQLServerResultSetMetaData Class](../content/SQLServerResultSetMetaData-Class.md)  
  
  