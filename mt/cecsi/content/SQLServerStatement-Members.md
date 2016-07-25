---
title: "SQLServerStatement Members"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 828cbaa9-ea7a-4986-95c3-5ba0d7d01d83
caps.latest.revision: 28
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
# SQLServerStatement Members
  The following tables list the members that are exposed by the [SQLServerStatement](../content/SQLServerStatement-Class.md) class.  
  
## Constructors  
 None.  
  
## Fields  
 None.  
  
## Inherited Fields  
  
|Name|Description|  
|----------|-----------------|  
|java.sql.Statement|CLOSE_ALL_RESULTS, CLOSE_CURRENT_RESULT, EXECUTE_FAILED, KEEP_CURRENT_RESULT, NO_GENERATED_KEYS, RETURN_GENERATED_KEYS, SUCCESS_NO_INFO|  
  
## Methods  
  
|Name|Description|  
|----------|-----------------|  
|[addBatch](../content/addBatch-Method--SQLServerStatement-.md)|Adds the given SQL command to the current list of commands for this [SQLServerStatement](../content/SQLServerStatement-Class.md) object.|  
|[cancel](../content/cancel-Method--SQLServerStatement-.md)|Cancels the SQL statement that is currently being run by this [SQLServerStatement](../content/SQLServerStatement-Class.md) object.|  
|[clearBatch](../content/clearBatch-Method--SQLServerStatement-.md)|Empties the current list of SQL commands for this [SQLServerStatement](../content/SQLServerStatement-Class.md) object.|  
|[clearWarnings](../content/clearWarnings-Method--SQLServerStatement-.md)|Clears all the warnings that are reported on this [SQLServerStatement](../content/SQLServerStatement-Class.md) object.|  
|[close](../content/close-Method--SQLServerStatement-.md)|Releases this [SQLServerStatement](../content/SQLServerStatement-Class.md) object's database and JDBC resources immediately instead of waiting for them to be automatically released.|  
|[execute](../content/execute-Method--SQLServerStatement-.md)|Runs the given SQL statement, which can return multiple results.|  
|[executeBatch](../content/executeBatch-Method--SQLServerStatement-.md)|Submits a batch of commands to the database to be run. If all commands run successfully, returns an array of update counts.|  
|[executeQuery](../content/executeQuery-Method--SQLServerStatement-.md)|Runs the given SQL statement and returns a single [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[executeUpdate](../content/executeUpdate-Method--SQLServerStatement-.md)|Runs the given SQL statement, which can be an INSERT, UPDATE, MERGE, or DELETE statement; or an SQL statement that returns nothing, such as an SQL DDL statement.|  
|[getConnection](../content/getConnection-Method--SQLServerStatement-.md)|Retrieves the [SQLServerConnection](../content/SQLServerConnection-Class.md) object that produced this [SQLServerStatement](../content/SQLServerStatement-Class.md) object.|  
|[getFetchDirection](../content/getFetchDirection-Method--SQLServerStatement-.md)|Retrieves the direction for fetching rows from database tables that is the default for result sets generated from this [SQLServerStatement](../content/SQLServerStatement-Class.md) object.|  
|[getFetchSize](../content/getFetchSize-Method--SQLServerStatement-.md)|Retrieves the number of result set rows that is the default fetch size for result set objects generated from this [SQLServerStatement](../content/SQLServerStatement-Class.md) object.|  
|[getGeneratedKeys](../content/getGeneratedKeys-Method--SQLServerStatement-.md)|Retrieves any auto-generated keys that are created as a result of running this [SQLServerStatement](../content/SQLServerStatement-Class.md) object.|  
|[getMaxFieldSize](../content/getMaxFieldSize-Method--SQLServerStatement-.md)|Retrieves the maximum number of bytes that can be returned for character and binary column values in a [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object that is produced by this [SQLServerStatement](../content/SQLServerStatement-Class.md) object.|  
|[getMaxRows](../content/getMaxRows-Method--SQLServerStatement-.md)|Retrieves the maximum number of rows that a [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object that is produced by this [SQLServerStatement](../content/SQLServerStatement-Class.md) object can contain.|  
|[getMoreResults](../content/getMoreResults-Method--SQLServerStatement-.md)|Moves to the next result of this [SQLServerStatement](../content/SQLServerStatement-Class.md) object.|  
|[getQueryTimeout](../content/getQueryTimeout-Method--SQLServerStatement-.md)|Retrieves the number of seconds the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] will wait for this [SQLServerStatement](../content/SQLServerStatement-Class.md) object to run.|  
|[getResponseBuffering](../content/getResponseBuffering-Method--SQLServerStatement-.md)|Retrieves the response buffering mode for this [SQLServerStatement](../content/SQLServerStatement-Class.md) object.|  
|[getResultSet](../content/getResultSet-Method--SQLServerStatement-.md)|Retrieves the current result as a [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.|  
|[getResultSetConcurrency](../content/getResultSetConcurrency-Method--SQLServerStatement-.md)|Retrieves the result set concurrency for [SQLServerResultSet](../content/SQLServerResultSet-Class.md) objects that are generated by this [SQLServerStatement](../content/SQLServerStatement-Class.md) object.|  
|[getResultSetHoldability](../content/getResultSetHoldability-Method--SQLServerStatement-.md)|Retrieves the result set holdability for [SQLServerResultSet](../content/SQLServerResultSet-Class.md) objects that are generated by this [SQLServerStatement](../content/SQLServerStatement-Class.md) object.|  
|[getResultSetType](../content/getResultSetType-Method--SQLServerStatement-.md)|Retrieves the result set type for [SQLServerResultSet](../content/SQLServerResultSet-Class.md) objects that are generated by this [SQLServerStatement](../content/SQLServerStatement-Class.md) object.|  
|[getUpdateCount](../content/getUpdateCount-Method--SQLServerStatement-.md)|Retrieves the current result as an update count.|  
|[getWarnings](../content/getWarnings-Method--SQLServerStatement-.md)|Retrieves the first warning that is reported by calls on this [SQLServerStatement](../content/SQLServerStatement-Class.md) object.|  
|[isClosed](../content/isClosed-Method--SQLServerStatement-.md)|Indicates whether this [SQLServerStatement](../content/SQLServerStatement-Class.md) object has been closed.|  
|[isPoolable](../content/isPoolable-Method--SQLServerStatement-.md)|Returns a value indicating if a statement can be added to the user-provided statement pool.|  
|[isWrapperFor](../content/isWrapperFor-Method--SQLServerStatement-.md)|Indicates whether this statement object is a wrapper for the specified interface.|  
|[setCursorName](../content/setCursorName-Method--SQLServerStatement-.md)|Sets the SQL cursor name to the given String, which will be used by subsequent execute methods.|  
|[setEscapeProcessing](../content/setEscapeProcessing-Method--SQLServerStatement-.md)|Sets the escape processing mode.|  
|[setFetchDirection](../content/setFetchDirection-Method--SQLServerStatement-.md)|Gives the JDBC driver a hint as to the direction in which result set rows should be processed.|  
|[setFetchSize](../content/setFetchSize-Method--SQLServerStatement-.md)|Gives the JDBC driver a hint as to the number of rows that should be fetched from the database when more rows are needed.|  
|[setMaxFieldSize](../content/setMaxFieldSize-Method--SQLServerStatement-.md)|Sets the limit for the maximum number of bytes in a [SQLServerResultSet](../content/SQLServerResultSet-Class.md) column storing character or binary values to the given number of bytes.|  
|[setMaxRows](../content/setMaxRows-Method--SQLServerStatement-.md)|Sets the limit for the maximum number of rows that any [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object can contain to the given number.|  
|[setPoolable](../content/setPoolable-Method--SQLServerStatement-.md)|Requests that a statement be pooled or not pooled.|  
|[setQueryTimeout](../content/setQueryTimeout-Method--SQLServerStatement-.md)|Sets the number of seconds the driver will wait for a [SQLServerStatement](../content/SQLServerStatement-Class.md) object to run to the given number of seconds.|  
|[setResponseBuffering](../content/setResponseBuffering-Method--SQLServerStatement-.md)|Sets the response buffering mode for this [SQLServerStatement](../content/SQLServerStatement-Class.md) object to case-insensitive **String full** or **adaptive**.|  
|[unwrap](../content/unwrap-Method--SQLServerStatement-.md)|Returns an object that implements the specified interface to allow access to the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)]-specific methods.|  
  
## Inherited Methods  
  
|Class inherited from:|Methods|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## See Also  
 [SQLServerStatement Class](../content/SQLServerStatement-Class.md)  
  
  