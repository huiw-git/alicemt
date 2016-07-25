---
title: "Driver-Aware Connection Pooling in the ODBC Driver for SQL Server"
ms.custom: na
ms.date: 07/21/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 455ab165-8e4d-4df9-a1d7-2b532bfd55d6
caps.latest.revision: 13
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
# Driver-Aware Connection Pooling in the ODBC Driver for SQL Server
  The ODBC Driver for [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] supports [Driver-Aware Connection Pooling](http://msdn.microsoft.com/library/hh405031(VS.85).aspx). This topic describes the enhancements made to driver-aware connection pooling in the Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] on Windows:  
  
-   Regardless of the connection properties, connections that use SQLDriverConnect go into a separate pool from connections that use SQLConnect.  
  
-   When using [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Authentication and driver-aware connection pooling, the driver does not use the Windows user’s security context for the current thread to separate connections in the pool. That is, if connections are equivalent in their parameters for Windows impersonation scenarios with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Authentication, and they are using the same [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Authentication credentials to connect to the backend, different Windows users can potentially use the same pool of connections. When using Windows Authentication and driver-aware connection pooling, the driver uses the current Windows user’s security context to separate connections in the pool. That is, for Windows impersonation scenarios, different Windows users do not share connections even if the connections use the same parameters.
    - When using Azure Active Directory and driver-aware connection pooling, the driver also uses the Authentication value to determine the membership in the connection pool.
  
-   Driver-aware connection pooling prevents a bad connection from being returned from the pool.  
  
-   Driver-aware connection pooling recognizes driver-specific connection attributes. So, if a connection uses SQL_COPT_SS_APPLICATION_INTENT set to read only, that connection gets its own connection pool.
    - Setting the SQL_COPT_SS_ACCESS_TOKEN attribute causes a connection to be pooled separately 
  
-   If one of the following connection-attribute IDs or connection string keywords is different between your connection string and the pooled connection string, the driver uses a pooled connection. However, performance is better if all connection attribute IDs or connection string keywords match. (In order to match a connection in the pool, the driver resets the attribute. Performance degrades because resetting the following parameters requires an extra network call.  
  
     If two or more of the following connection attributes or connection keywords differ, a pooled connection is not used.  
  
    -   Language  
  
    -   QuoteId  
  
    -   SQL_ATTR_TXN_ISOLATION  
  
    -   SQL_COPT_SS_QUOTED_IDENT  
  
-   If there is a difference in any of the following connection keywords between your connection string and a pooled connection string, a pooled connection is not used.  
  
    |||||
    |-|-|-|-|
    |Address|AnsiNPW|App|ApplicationIntent|  
    |Authentication*|ColumnEncryption*|Database|Encrypt|  
    |Failover_Partner|FailoverPartnerSPN|MARS_Connection|Network|  
    |PWD|Server|ServerSPN|TransparentNetworkIPResolution|
    |Trusted_Connection|TrustServerCertificate|UID|WSID|  
    *ODBC Driver 13.1 Only
    
     If there is a difference in any of the following connection attributes between your connection string and a pooled connection string, a pooled connection is not used.  
  
    ||||  
    |-|-|-|  
    |SQL_ATTR_CURRENT_CATALOG|SQL_ATTR_PACKET_SIZE|SQL_COPT_SS_ANSI_NPW|  
    |SQL_COPT_SS_ACCESS_TOKEN*|SQL_COPT_SS_AUTHENTICATION*|SQL_COPT_SS_ATTACHDBFILENAME|
    |SQL_COPT_SS_BCP|SQL_COPT_SS_COLUMN_ENCRYPTION*|SQL_COPT_SS_CONCAT_NULL|
    |SQL_COPT_SS_ENCRYPT|SQL_COPT_SS_FAILOVER_PARTNER|SQL_COPT_SS_FAILOVER_PARTNER_SPN|
    |SQL_COPT_SS_INTEGRATED_SECURITY|SQL_COPT_SS_MARS_ENABLED|SQL_COPT_SS_OLDPWD|
    |SQL_COPT_SS_SERVER_SPN|SQL_COPT_SS_TRUST_SERVER_CERTIFICATE|SSPROP_AUTH_REPL_SERVER_NAME|
    |SQL_COPT_SS_TNIR*|||
    *ODBC Driver 13.1 Only
     
  
-   The driver can reset and adjust the following connection keywords and attributes without making an extra network call. The driver resets these parameters to ensure that the connection does not contain incorrect information.  
  
     These connection keywords are not considered when the Driver Manager tries to match your connection with a connection in the pool. (Even if you change one of these parameters, an existing connection can be reused. The driver will reset the options, as needed.) This attributes can be reset in the client side without making an extra network call.  
  
    ||||  
    |-|-|-|  
    |AutoTranslate|Description|MultisubnetFailover|  
    |QueryLog_On|QueryLogFile|QueryLogTime|  
    |Regional|StatsLog_On|StatsLogFile|  
  
     If you change one of the following connection attributes, an existing connection can be reused.  The driver will reset the value, as needed. The driver can reset these attributes in the client without making an extra network call.  
  
    ||||  
    |-|-|-|  
    |All statement attributes|SQL_ATTR_AUTOCOMMIT|SQL_ATTR_CONNECTION_TIMEOUT|  
    |SQL_ATTR_DISCONNECT_BEHAVIOR SQL_ATTR_CONNECTION_TIMEOUT|SQL_ATTR_LOGIN_TIMEOUT|SQL_ATTR_ODBC_CURSORS|  
    |SQL_COPT_SS_PERF_DATA|SQL_COPT_SS_PERF_DATA_LOG|SQL_COPT_SS_PERF_DATA_LOG_NOW|  
    |SQL_COPT_SS_PERF_QUERY|SQL_COPT_SS_PERF_QUERY_INTERVAL|SQL_COPT_SS_PERF_QUERY_LOG|  
    |SQL_COPT_SS_PRESERVE_CURSORS|SQL_COPT_SS_TRANSLATE|SQL_COPT_SS_USER_DATA|  
    |SQL_COPT_SS_WARN_ON_CP_ERROR|||  
  
## See Also  
 [Microsoft ODBC Driver for SQL Server on Windows](../content/Microsoft-ODBC-Driver-for-SQL-Server-on-Windows.md)  
  
  