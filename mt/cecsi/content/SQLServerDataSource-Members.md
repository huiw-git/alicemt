---
title: "SQLServerDataSource Members"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7e749bc5-d765-4864-be2b-7822d4c20c09
caps.latest.revision: 43
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
# SQLServerDataSource Members
  The following tables list the members exposed by the [SQLServerDataSource](../content/SQLServerDataSource-Class.md) class.  
  
## Constructors  
  
|Name|Description|  
|----------|-----------------|  
|[SQLServerDataSource ()](../content/SQLServerDataSource-Constructor---.md)|Initializes a new instance of the [SQLServerDataSource](../content/SQLServerDataSource-Class.md) class.|  
  
## Fields  
 None.  
  
## Inherited Fields  
 None.  
  
## Methods  
  
|Name|Description|  
|----------|-----------------|  
|[getApplicationIntent](../content/getApplicationIntent-Method--SQLServerDataSource-.md)|Returns the value of the **applicationIntent** connection property.|  
|[getApplicationName](../content/getApplicationName-Method--SQLServerDataSource-.md)|Returns the application name.|  
|[getConnection](../content/getConnection-Method--SQLServerDataSource-.md)|Tries to establish a connection with the data source that this [SQLServerDataSource](../content/SQLServerDataSource-Class.md) object represents.|  
|[getDatabaseName](../content/getDatabaseName-Method--SQLServerDataSource-.md)|Returns the database name.|  
|[getEncrypt](../content/getEncrypt-Method--SQLServerDataSource-.md)|Returns a **Boolean** value indicating whether the encrypt property is enabled.|  
|[getDescription](../content/getDescription-Method--SQLServerDataSource-.md)|Returns a description of the data source.|  
|[getFailoverPartner](../content/getFailoverPartner-Method--SQLServerDataSource-.md)|Returns the name of the failover server used in a database mirroring configuration.|  
|[getHostNameInCertificate](../content/getHostNameInCertificate-Method--SQLServerDataSource-.md)|Returns the host name used in validating the SQL Server Secure Sockets Layer (SSL) certificate.|  
|[getInstanceName](../content/getInstanceName-Method--SQLServerDataSource-.md)|Returns the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] instance name.|  
|[getLastUpdateCount](../content/getLastUpdateCount-Method--SQLServerDataSource-.md)|Returns a **boolean** value indicating whether the lastUpdateCount property is enabled.|  
|[getLockTimeout](../content/getLockTimeout-Method--SQLServerDataSource-.md)|Returns an **int** value indicating the number of milliseconds the database waits before reporting a lock time out.|  
|[getLoginTimeout](../content/getLoginTimeout-Method--SQLServerDataSource-.md)|Returns the number of seconds this [SQLServerDataSource](../content/SQLServerDataSource-Class.md) object waits while trying to make a connection.|  
|[getLogWriter](../content/getLogWriter-Method--SQLServerDataSource-.md)|Returns a character output stream to be used for all logging and tracing messages.|  
|[getMultiSubnetFailover](../content/getMultiSubnetFailover-Method--SQLServerDataSource-.md)|Returns the value of the **multiSubnetFailover** connection property.|  
|[getPacketSize](../content/getPacketSize-Method--SQLServerDataSource-.md)|Returns the current network packet size used to communicate with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)], specified in bytes.|  
|[getPortNumber](../content/getPortNumber-Method--SQLServerDataSource-.md)|Returns the current port number used to communicate with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].|  
|[getReference](../content/getReference-Method--SQLServerDataSource-.md)|Returns a reference to this [SQLServerDataSource](../content/SQLServerDataSource-Class.md) object.|  
|[getResponseBuffering](../content/getResponseBuffering-Method--SQLServerDataSource-.md)|Returns the response buffering mode for this [SQLServerDataSource](../content/SQLServerDataSource-Class.md) object.|  
|[getSelectMethod](../content/getSelectMethod-Method--SQLServerDataSource-.md)|Returns the default cursor type used for all result sets created by using this [SQLServerDataSource](../content/SQLServerDataSource-Class.md) object.|  
|[getSendStringParametersAsUnicode](../content/getSendStringParametersAsUnicode-Method--SQLServerDataSource-.md)|Returns a **Boolean** value indicating whether sending string parameters to the server in UNICODE format is enabled.|  
|[getSendTimeAsDatetime](../content/getSendTimeAsDatetime-Method--SQLServerDataSource-.md)|Returns the setting of the **SendTimeAsDatetime** connection property.|  
|[getServerName](../content/getServerName-Method--SQLServerDataSource-.md)|Returns the name of the computer running [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].|  
|[getTrustServerCertificate](../content/getTrustServerCertificate-Method--SQLServerDataSource-.md)|Returns a **Boolean** value indicating whether the trustServerCertificate property is enabled.|  
|[getTrustStore](../content/getTrustStore-Method--SQLServerDataSource-.md)|Returns the path (including file name) to the certificate trustStore file.|  
|[getURL](../content/getURL-Method--SQLServerDataSource-.md)|Returns the URL used to connect to the data source.|  
|[getUser](../content/getUser-Method--SQLServerDataSource-.md)|Returns the user name used to connect the data source.|  
|[getUseSQLServerBaseDate](../content/getSendTimeAsDatetime-Method--SQLServerDataSource-.md)|Returns the setting of the useSQLServerBaseDate connection property.|  
|[getWorkstationID](../content/getWorkstationID-Method--SQLServerDataSource-.md)|Returns the name of the client computer name used to connect to the data source.|  
|[getXopenStates](../content/getXopenStates-Method--SQLServerDataSource-.md)|Returns a **Boolean** value indicating whether converting SQL states to XOPEN compliant states is enabled.|  
|[isWrapperFor](../content/isWrapperFor-Method--SQLServerDataSource-.md)|Indicates whether this data source object is a wrapper for the specified interface.|  
|[setApplicationIntent](../content/setApplicationIntent-Method--SQLServerDataSource-.md)|Sets the value of the **applicationIntent** connection property.|  
|[setApplicationName](../content/setApplicationName-Method--SQLServerDataSource-.md)|Sets the application name.|  
|[setAuthenticationScheme](../content/setAuthenticationScheme--SQLServerDataSource-.md)|Indicates the kind of integrated security you want your application to use.|  
|[setDatabaseName](../content/setDatabaseName-Method--SQLServerDataSource-.md)|Sets the database name to connect to.|  
|[setDescription](../content/setDescription-Method--SQLServerDataSource-.md)|Sets the description of the data source.|  
|[setEncrypt](../content/setEncrypt-Method--SQLServerDataSource-.md)|Sets a **Boolean** value indicating whether the encrypt property is enabled.|  
|[setFailoverPartner](../content/setFailoverPartner-Method--SQLServerDataSource-.md)|Sets the name of the failover server used in a database mirroring configuration.|  
|[setHostNameInCertificate](../content/setHostNameInCertificate-Method--SQLServerDataSource-.md)|Sets the host name to be used in validating the SQL Server Secure Sockets Layer (SSL) certificate.|  
|[setInstanceName](../content/setInstanceName-Method--SQLServerDataSource-.md)|Sets the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] instance name.|  
|[setIntegratedSecurity](../content/setIntegratedSecurity-Method--SQLServerDataSource-.md)|Sets a **Boolean** value indicating whether the integratedSecurity property is enabled.|  
|[setLastUpdateCount](../content/setLastUpdateCount-Method--SQLServerDataSource-.md)|Sets a **Boolean** value indicating whether the lastUpdateCount property is enabled.|  
|[setLockTimeout](../content/setLockTimeout-Method--SQLServerDataSource-.md)|Sets an **int** value indicating the number of milliseconds to wait before the database reports a lock time out.|  
|[setLoginTimeout](../content/setLoginTimeout-Method--SQLServerDataSource-.md)|Sets the number of seconds that this [SQLServerDataSource](../content/SQLServerDataSource-Class.md) object waits while trying to make a connection.|  
|[setLogWriter](../content/setLogWriter-Method--SQLServerDataSource-.md)|Sets a character output stream to be used for all logging and tracing messages.|  
|[setMultiSubnetFailover](../content/setMultiSubnetFailover-Method--SQLServerDataSource-.md)|Sets the value of the **multiSubnetFailover** connection property.|  
|[setPacketSize](../content/setPacketSize-Method--SQLServerDataSource-.md)|Sets the current network packet size used to communicate with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)], specified in bytes.|  
|[setPassword](../content/setPassword-Method--SQLServerDataSource-.md)|Sets the password used to connect to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].|  
|[setPortNumber](../content/setPortNumber-Method--SQLServerDataSource-.md)|Sets the port number used to communicate with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].|  
|[setResponseBuffering](../content/setResponseBuffering-Method--SQLServerDataSource-.md)|Sets the response buffering mode for connections created by using this [SQLServerDataSource](../content/SQLServerDataSource-Class.md) object.|  
|[setSelectMethod](../content/setSelectMethod-Method--SQLServerDataSource-.md)|Sets the default cursor type used for all result sets created by using this [SQLServerDataSource](../content/SQLServerDataSource-Class.md) object.|  
|[setSendStringParametersAsUnicode](../content/setSendStringParametersAsUnicode-Method--SQLServerDataSource-.md)|Sets a **Boolean** value indicating whether sending string parameters to the server in UNICODE format is enabled.|  
|[setSendTimeAsDatetime](../content/setSendTimeAsDatetime-Method--SQLServerDataSource-.md)|Specifies how to send java.sql.Time values to the server.|  
|[setServerName](../content/setServerName-Method--SQLServerDataSource-.md)|Sets the name of the computer running [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].|  
|[setTrustServerCertificate](../content/setTrustServerCertificate-Method--SQLServerDataSource-.md)|Sets a **Boolean** value indicating whether the trustServerCertificate property is enabled.|  
|[setTrustStore](../content/setTrustStore-Method--SQLServerDataSource-.md)|Sets the path (including file name) to the certificate trustStore file.|  
|[setTrustStorePassword](../content/setTrustStorePassword-Method--SQLServerDataSource-.md)|Sets the password that is used to check the integrity of the trustStore data.|  
|[setURL](../content/setURL-Method--SQLServerDataSource-.md)|Sets the URL used to connect to the data source.|  
|[setUser](../content/setUser-Method--SQLServerDataSource-.md)|Sets the user name used to connect the data source.|  
|[setWorkstationID](../content/setWorkstationID-Method--SQLServerDataSource-.md)|Sets the name of the client computer used to connect to the data source.|  
|[setXopenStates](../content/setXopenStates-Method--SQLServerDataSource-.md)|Sets a **Boolean** value indicating whether converting SQL states to XOPEN compliant states is enabled.|  
|[unwrap](../content/unwrap-Method--SQLServerDataSource-.md)|Returns an object that implements the specified interface to allow access to the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)]-specific methods.|  
  
## Inherited Methods  
  
|Class inherited from:|Methods|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## See Also  
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  