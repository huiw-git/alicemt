---
title: Driver-Aware Connection Pooling in the ODBC Driver for SQL Server
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 455ab165-8e4d-4df9-a1d7-2b532bfd55d6
manager:jhubbard
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
  The ODBC Driver for [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] supports [Driver\-Aware Connection Pooling](http://msdn.microsoft.com/library/hh405031(VS.85).aspx). This topic describes the enhancements made to driver\-aware connection pooling in the Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] on Windows:  
  
-   Regardless of the connection properties, connections that use SQLDriverConnect go into a separate pool from connections that use SQLConnect.  
  
-   When using [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Authentication and driver\-aware connection pooling, the driver does not use the Windows user’s security context for the current thread to separate connections in the pool. That is, if connections are equivalent in their parameters for Windows impersonation scenarios with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Authentication, and they are using the same [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Authentication credentials to connect to the backend, different Windows users can potentially use the same pool of connections. When using Windows Authentication and driver\-aware connection pooling, the driver uses the current Windows user’s security context to separate connections in the pool. That is, for Windows impersonation scenarios, different Windows users do not share connections even if the connections use the same parameters.  
  
-   Driver\-aware connection pooling prevents a bad connection from being returned from the pool.  
  
-   Driver\-aware connection pooling recognizes driver\-specific connection attributes. So, if a connection uses SQL\_COPT\_SS\_APPLICATION\_INTENT set to read only, that connection gets its own connection pool.  
  
-   If one of the following connection\-attribute IDs or connection string keywords is different between your connection string and the pooled connection string, the driver uses a pooled connection. However, performance is better if all connection attribute IDs or connection string keywords match. \(In order to match a connection in the pool, the driver resets the attribute. Performance degrades because resetting the following parameters requires an extra network call.  
  
     If two or more of the following connection attributes or connection keywords differ, a pooled connection is not used.  
  
    -   Language  
  
    -   QuoteId  
  
    -   SQL\_ATTR\_TXN\_ISOLATION  
  
    -   SQL\_COPT\_SS\_QUOTED\_IDENT  
  
-   If there is a difference in any of the following connection keywords between your connection string and a pooled connection string, a pooled connection is not used.  
  
    ||||  
    |-|-|-|  
    |Address|AnsiNPW|App|  
    |ApplicationIntent|Database|Encrypt|  
    |Failover\_Partner|FailoverPartnerSPN|MARS\_Connection|  
    |Network|PWD|Server|  
    |ServerSPN|Trusted\_Connection|TrustServerCertificate|  
    |UID|WSID||  
  
     If there is a difference in any of the following connection attributes between your connection string and a pooled connection string, a pooled connection is not used.  
  
    ||||  
    |-|-|-|  
    |SQL\_ATTR\_CURRENT\_CATALOG|SQL\_ATTR\_PACKET\_SIZE|SQL\_COPT\_SS\_ANSI\_NPW|  
    |SQL\_COPT\_SS\_ATTACHDBFILENAME|SQL\_COPT\_SS\_BCP|SQL\_COPT\_SS\_CONCAT\_NULL|  
    |SQL\_COPT\_SS\_ENCRYPT|SQL\_COPT\_SS\_FAILOVER\_PARTNER|SQL\_COPT\_SS\_FAILOVER\_PARTNER\_SPN|  
    |SQL\_COPT\_SS\_INTEGRATED\_SECURITY|SQL\_COPT\_SS\_MARS\_ENABLED|SQL\_COPT\_SS\_OLDPWD|  
    |SQL\_COPT\_SS\_SERVER\_SPN|SQL\_COPT\_SS\_TRUST\_SERVER\_CERTIFICATE|SSPROP\_AUTH\_REPL\_SERVER\_NAME|  
  
-   The driver can reset and adjust the following connection keywords and attributes without making an extra network call. The driver resets these parameters to ensure that the connection does not contain incorrect information.  
  
     These connection keywords are not considered when the Driver Manager tries to match your connection with a connection in the pool. \(Even if you change one of these parameters, an existing connection can be reused. The driver will reset the options, as needed.\) This attributes can be reset in the client side without making an extra network call.  
  
    ||||  
    |-|-|-|  
    |AutoTranslate|Description|MultisubnetFailover|  
    |QueryLog\_On|QueryLogFile|QueryLogTime|  
    |Regional|StatsLog\_On|StatsLogFile|  
  
     If you change one of the following connection attributes, an existing connection can be reused.  The driver will reset the value, as needed. The driver can reset these attributes in the client without making an extra network call.  
  
    ||||  
    |-|-|-|  
    |All statement attributes|SQL\_ATTR\_AUTOCOMMIT|SQL\_ATTR\_CONNECTION\_TIMEOUT|  
    |SQL\_ATTR\_DISCONNECT\_BEHAVIOR SQL\_ATTR\_CONNECTION\_TIMEOUT|SQL\_ATTR\_LOGIN\_TIMEOUT|SQL\_ATTR\_ODBC\_CURSORS|  
    |SQL\_COPT\_SS\_PERF\_DATA|SQL\_COPT\_SS\_PERF\_DATA\_LOG|SQL\_COPT\_SS\_PERF\_DATA\_LOG\_NOW|  
    |SQL\_COPT\_SS\_PERF\_QUERY|SQL\_COPT\_SS\_PERF\_QUERY\_INTERVAL|SQL\_COPT\_SS\_PERF\_QUERY\_LOG|  
    |SQL\_COPT\_SS\_PRESERVE\_CURSORS|SQL\_COPT\_SS\_TRANSLATE|SQL\_COPT\_SS\_USER\_DATA|  
    |SQL\_COPT\_SS\_WARN\_ON\_CP\_ERROR|||  
  
## See Also  
 [Microsoft ODBC Driver for SQL Server on Windows](../content/Microsoft-ODBC-Driver-for-SQL-Server-on-Windows.md)  
  
  