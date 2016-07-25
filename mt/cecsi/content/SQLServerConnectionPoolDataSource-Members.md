---
title: "SQLServerConnectionPoolDataSource Members"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dac0337e-8088-488c-a25a-801a2190f6ca
caps.latest.revision: 25
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
# SQLServerConnectionPoolDataSource Members
  The following tables list the members that are exposed by the [SQLServerConnectionPoolDataSource](../content/SQLServerConnectionPoolDataSource-Class.md) class.  
  
## Constructors  
  
|Name|Description|  
|----------|-----------------|  
|[SQLServerConnectionPoolDataSource ()](../content/SQLServerConnectionPoolDataSource-Constructor---.md)|Initializes a new instance of the [SQLServerConnectionPoolDataSource](../content/SQLServerConnectionPoolDataSource-Class.md) class.|  
  
## Fields  
 None.  
  
## Inherited Fields  
 None.  
  
## Methods  
  
|Name|Description|  
|----------|-----------------|  
|[getApplicationIntent](../content/getApplicationIntent-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Returns the value of the **applicationIntent** connection property.|  
|[getApplicationName](../content/getApplicationName-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Returns the application name.|  
|[getConnection](../content/getConnection-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Tries to establish a connection with the data source that this DataSource object represents.|  
|[getDatabaseName](../content/getDatabaseName-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Returns the database name.|  
|[getDescription](../content/getDescription-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Returns a description of the data source.|  
|[getFailoverPartner](../content/getFailoverPartner-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Returns the name of the failover server that is used in a database mirroring configuration.|  
|[getInstanceName](../content/getInstanceName-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Returns the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] instance name.|  
|[getLastUpdateCount](../content/getLastUpdateCount-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Returns a **boolean** value that indicates if the lastUpdateCount property is enabled.|  
|[getLockTimeout](../content/getLockTimeout-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Returns an **int** value that indicates the number of milliseconds that the database will wait before reporting a lock time out.|  
|[getLoginTimeout](../content/getLoginTimeout-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Returns the number of seconds that this DataSource object will wait while trying to make a connection.|  
|[getLogWriter](../content/getLogWriter-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Returns a character output stream to be used for all logging and tracing messages.|  
|[getMultiSubnetFailover](../content/getMultiSubnetFailover-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Returns the value of the **multiSubnetFailover** connection property.|  
|[getPooledConnection](../content/getPooledConnection-Method--SQLServerConnectionPoolDataSource-.md)|Tries to establish a physical database connection that can be used as a pooled connection.|  
|[getPortNumber](../content/getPortNumber-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Returns the current port number that is used to communicate with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].|  
|[getReference](../content/getReference-Method--SQLServerConnectionPoolDataSource-.md)|Returns a reference to this DataSource object.|  
|[getSelectMethod](../content/getSelectMethod-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Returns the default cursor type that is used for all result sets that are created by using this DataSource object.|  
|[getSendStringParametersAsUnicode](../content/getSendStringParametersAsUnicode-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Returns a **Boolean** value that indicates if sending string parameters to the server in UNICODE format is enabled.|  
|[getServerName](../content/getServerName-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Returns the name of the computer that is running [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].|  
|[getURL](../content/getURL-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Returns the URL that is used to connect to the data source.|  
|[getUser](../content/getUser-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Returns the user name that is used to connect the data source.|  
|[getWorkstationID](../content/getWorkstationID-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Returns the name of the client computer name that is used to connect to the data source.|  
|[getXopenStates](../content/getXopenStates-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Returns a **Boolean** value that indicates if converting SQL states to XOPEN compliant states is enabled.|  
|[isWrapperFor](../content/isWrapperFor-Method--SQLServerConnectionPoolDataSource-.md)|Indicates whether this object is a wrapper for the specified interface.|  
|[setApplicationIntent](../content/setApplicationIntent-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Sets the value of the **applicationIntent** connection property.|  
|[setApplicationName](../content/setApplicationName-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Sets the application name.|  
|[setAuthenticationSceme](../content/setAuthenticationScheme--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Indicates the kind of integrated security you want your application to use.|  
|[setDatabaseName](../content/setDatabaseName-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Sets the database name to connect to.|  
|[setDescription](../content/setDescription-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Sets the description of the data source.|  
|[setFailoverPartner](../content/setFailoverPartner-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Sets the name of the failover server that is used in a database mirroring configuration.|  
|[setInstanceName](../content/setInstanceName-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Sets the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] instance name.|  
|[setIntegratedSecurity](../content/setIntegratedSecurity-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Sets a **Boolean** value that indicates if the integratedSecurity property is enabled.|  
|[setLastUpdateCount](../content/setLastUpdateCount-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Sets a **Boolean** value that indicates if the lastUpdateCount property is enabled.|  
|[setLockTimeout](../content/setLockTimeout-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Sets an **int** value that indicates the number of milliseconds to wait before the database reports a lock time out.|  
|[setLoginTimeout](../content/setLoginTimeout-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Sets the number of seconds that this DataSource object will wait while trying to make a connection.|  
|[setLogWriter](../content/setLogWriter-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Sets a character output stream to be used for all logging and tracing messages.|  
|[setMultiSubnetFailover](../content/setMultiSubnetFailover-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Sets the value of the **multiSubnetFailover** connection property.|  
|[setPassword](../content/setPassword-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Sets the password that will be used to connect to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].|  
|[setPortNumber](../content/setPortNumber-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Sets the port number to be used to communicate with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].|  
|[setSelectMethod](../content/setSelectMethod-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Sets the default cursor type that is used for all result sets that are created by using this DataSource object.|  
|[setSendStringParametersAsUnicode](../content/setSendStringParametersAsUnicode-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Sets a **Boolean** value that indicates if sending string parameters to the server in UNICODE format is enabled.|  
|[setServerName](../content/setServerName-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Sets the name of the computer that is running [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].|  
|[setURL](../content/setURL-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Sets the URL that is used to connect to the data source.|  
|[setUser](../content/setUser-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Sets the user name that is used to connect the data source.|  
|[setWorkstationID](../content/setWorkstationID-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Sets the client computer name that is used to connect to the data source.|  
|[setXopenStates](../content/setXopenStates-Method--SQLServerDataSource-.md)|(Inherited from [SQLServerDataSource](../content/SQLServerDataSource-Class.md)) Sets a **boolean** value that indicates if converting SQL states to XOPEN compliant states is enabled.|  
|[unwrap](../content/unwrap-Method--SQLServerConnectionPoolDataSource-.md)|Returns an object that implements the specified interface to allow access to the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)]-specific methods.|  
  
## Inherited Methods  
  
|Class inherited from:|Methods|  
|---------------------------|-------------|  
|com.microsoft.sqlserver.jdbc.SQLServerDataSource|getApplicationName, getConnection, getDatabaseName, getDescription, getFailoverPartner, getInstanceName, getLastUpdateCount, getLockTimeout, getLoginTimeout, getLogWriter, getPortNumber, getSelectMethod, getSendStringParametersAsUnicode, getServerName, getURL, getUser, getWorkstationID, getXopenStates, setApplicationName, setDatabaseName, setDescription, setFailoverPartner, setInstanceName, setIntegratedSecurity, setLastUpdateCount, setLockTimeout, setLoginTimeout, setLogWriter, setPassword, setPortNumber, setSelectMethod, setSendStringParametersAsUnicode, setServerName, setURL, setUser, setWorkstationID, setXopenStates|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
|javax.sql.ConnectionPoolDataSource|getLoginTimeout, getLogWriter, setLoginTimeout, setLogWriter, getPooledConnection|  
  
## See Also  
 [SQLServerConnectionPoolDataSource Class](../content/SQLServerConnectionPoolDataSource-Class.md)  
  
  