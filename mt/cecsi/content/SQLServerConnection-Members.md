---
title: SQLServerConnection Members
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3115a533-756b-4c78-aee9-4ba7253c85e0
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
# SQLServerConnection Members
  The following tables list the members that are exposed by the [SQLServerConnection](../content/SQLServerConnection-Class.md) class.  
  
## Constructors  
 None.  
  
## Fields  
  
|Name|Description|  
|----------|-----------------|  
|[TRANSACTION\_SNAPSHOT](../content/TRANSACTION_SNAPSHOT-Field--SQLServerConnection-.md)|Used to specify the snapshot transaction isolation level.|  
  
## Inherited Fields  
  
|Class inherited from:|Description|  
|---------------------------|-----------------|  
|java.sql.Connection|TRANSACTION\_NONE, TRANSACTION\_READ\_COMMITTED, TRANSACTION\_READ\_UNCOMMITTED, TRANSACTION\_REPEATABLE\_READ, TRANSACTION\_SERIALIZABLE|  
  
## Methods  
  
|Name|Description|  
|----------|-----------------|  
|[clearWarnings](../content/clearWarnings-Method--SQLServerConnection-.md)|Clears all warnings reported for this [SQLServerConnection](../content/SQLServerConnection-Class.md) object.|  
|[close](../content/close-Method--SQLServerConnection-.md)|Releases the database for this [SQLServerConnection](../content/SQLServerConnection-Class.md) object and JDBC resources immediately instead of waiting for them to be automatically released.|  
|[commit](../content/commit-Method--SQLServerConnection-.md)|Makes all changes made since the previous commit or rollback permanent, and releases any database locks that are currently held by this [SQLServerConnection](../content/SQLServerConnection-Class.md) object.|  
|[createBlob](../content/createBlob-Method--SQLServerConnection-.md)|Creates a **java.sql.Blob** object without any data.|  
|[createClob](../content/createClob-Method--SQLServerConnection-.md)|Creates a **java.sql.Clob** object without any data.|  
|[createNClob](../content/createNClob-Method--SQLServerConnection-.md)|Creates a **java.sql.NClob** object without any data.|  
|[createStatement](../content/createStatement-Method--SQLServerConnection-.md)|Creates a [SQLServerStatement](../content/SQLServerStatement-Class.md) object for sending SQL statements to the database.|  
|[createSQLXML](../content/createSQLXML-Method--SQLServerConnection-.md)|Creates a **java.sql.SQLXML** object without any data.|  
|[getAutoCommit](../content/getAutoCommit-Method--SQLServerConnection-.md)|Retrieves the current auto\-commit mode for this [SQLServerConnection](../content/SQLServerConnection-Class.md) object.|  
|[getCatalog](../content/getCatalog-Method--SQLServerConnection-.md)|Retrieves the current catalog name for this [SQLServerConnection](../content/SQLServerConnection-Class.md) object.|  
|[getClientConnectionID Method &#40;SQLServerConnection&#41;](../content/getClientConnectionID-Method--SQLServerConnection-.md)|Gets the connection ID of the most recent connection attempt, regardless of whether the attempt succeeded or failed.|  
|[getClientInfo](../content/getClientInfo-Method--SQLServerConnection-.md)|Retrieves information regarding the client information properties supported by the JDBC driver.|  
|[getHoldability](../content/getHoldability-Method--SQLServerConnection-.md)|Retrieves the current holdability of [SQLServerResultSet](../content/SQLServerResultSet-Class.md) objects that are created by using this [SQLServerConnection](../content/SQLServerConnection-Class.md) object.|  
|[getMetaData](../content/getMetaData-Method--SQLServerConnection-.md)|Retrieves a [SQLServerDatabaseMetaData](../content/SQLServerDatabaseMetaData-Class.md) object that contains metadata about the database to which this [SQLServerConnection](../content/SQLServerConnection-Class.md) object represents a connection.|  
|[getTransactionIsolation](../content/getTransactionIsolation-Method--SQLServerConnection-.md)|Retrieves the current transaction isolation level for this [SQLServerConnection](../content/SQLServerConnection-Class.md) object.|  
|[getTypeMap](../content/getTypeMap-Method--SQLServerConnection-.md)|Retrieves the Map object that is associated with this [SQLServerConnection](../content/SQLServerConnection-Class.md) object.|  
|[getWarnings](../content/getWarnings-Method--SQLServerConnection-.md)|Retrieves the first warning reported by calls on this [SQLServerConnection](../content/SQLServerConnection-Class.md) object.|  
|[isClosed](../content/isClosed-Method--SQLServerConnection-.md)|Indicates whether this [SQLServerConnection](../content/SQLServerConnection-Class.md) object has been closed.|  
|[isReadOnly](../content/isReadOnly-Method--SQLServerConnection-.md)|Indicates whether this [SQLServerConnection](../content/SQLServerConnection-Class.md) object is in read\-only mode.|  
|[isValid](../content/isValid-Method--SQLServerConnection-.md)|Indicates whether this [SQLServerConnection](../content/SQLServerConnection-Class.md) object has not been closed and is still valid.|  
|[nativeSQL](../content/nativeSQL-Method--SQLServerConnection-.md)|Converts the given SQL statement into the native SQL grammar of the database server.|  
|[prepareCall](../content/prepareCall-Method--SQLServerConnection-.md)|Creates a [SQLServerCallableStatement](../content/SQLServerCallableStatement-Class.md) object for calling database stored procedures.|  
|[prepareStatement](../content/prepareStatement-Method--SQLServerConnection-.md)|Creates a [SQLServerPreparedStatement](../content/SQLServerPreparedStatement-Class.md) object for sending parameterized SQL statements to the database.|  
|[releaseSavepoint](../content/releaseSavepoint-Method--SQLServerConnection-.md)|Removes the specified [SQLServerSavepoint](../content/SQLServerSavepoint-Class.md) object from the current transaction.|  
|[rollback](../content/rollback-Method--SQLServerConnection-.md)|Undoes all changes made in the current transaction and releases any database locks currently held by this [SQLServerConnection](../content/SQLServerConnection-Class.md) object.|  
|[setAutoCommit](../content/setAutoCommit-Method--SQLServerConnection-.md)|Sets the auto\-commit mode for this [SQLServerConnection](../content/SQLServerConnection-Class.md) object to the given state.|  
|[setCatalog](../content/setCatalog-Method--SQLServerConnection-.md)|Sets the specified catalog name to select a subspace of this [SQLServerConnection](../content/SQLServerConnection-Class.md) object's database in which to work.|  
|[setClientInfo](../content/setClientInfo-Method--SQLServerConnection-.md)|Sets the value of the client information properties.|  
|[setHoldability](../content/setHoldability-Method--SQLServerConnection-.md)|Changes the holdability of [SQLServerResultSet](../content/SQLServerResultSet-Class.md) objects that are created by using this [SQLServerSavepoint](../content/SQLServerSavepoint-Class.md) object to the given holdability.|  
|[setReadOnly](../content/setReadOnly-Method--SQLServerConnection-.md)|Puts this [SQLServerConnection](../content/SQLServerConnection-Class.md) object in read\-only mode as a hint to the JDBC driver to enable database optimizations.|  
|[setSavepoint](../content/setSavepoint-Method--SQLServerConnection-.md)|Creates an unnamed savepoint in the current transaction and returns the new [SQLServerSavepoint](../content/SQLServerSavepoint-Class.md) object that represents it.|  
|[setTransactionIsolation](../content/setTransactionIsolation-Method--SQLServerConnection-.md)|Tries to change the transaction isolation level for this [SQLServerConnection](../content/SQLServerConnection-Class.md) object to the one given.|  
|[setTypeMap](../content/setTypeMap-Method--SQLServerConnection-.md)|Installs the given TypeMap object as the type map for this [SQLServerConnection](../content/SQLServerConnection-Class.md) object.|  
  
## Inherited Methods  
  
|Class inherited from:|Methods|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.lang.Wrapper|isWrapperFor, unwrap|  
  
## See Also  
 [SQLServerConnection Class](../content/SQLServerConnection-Class.md)  
  
  