---
title: JDBC Driver Support for High Availability, Disaster Recovery
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 62de4be6-b027-427d-a7e5-352960e42877
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
# JDBC Driver Support for High Availability, Disaster Recovery
  This topic discusses [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] support for high\-availability, disaster recovery \-\- [!INCLUDE[ssHADR](../content/includes/ssHADR_md.md)]. For more information about [!INCLUDE[ssHADR](../content/includes/ssHADR_md.md)], see [!INCLUDE[ssSQL11](../content/includes/ssSQL11_md.md)] Books Online.  
  
 Beginning in version 4.0 of the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)], you can specify the availability group listener of a \(high\-availability, disaster\-recovery\) availability group \(AG\) in the connection property. If a [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] application is connected to an AlwaysOn database that fails over, the original connection is broken and the application must open a new connection to continue work after the failover.  
  
 If you are not connecting to an availability group listener, and if multiple IP addresses are associated with a server, the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] attempts to connect to the first IP address. If the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] cannot establish a connection with first IP address, the connection fails. The [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] will not attempt to connect to any subsequent IP address associated with the server. When connecting to an availability group listener, the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] attempts to establish connections to all IP addresses in parallel and if a connection attempt succeeds, the driver will discard any pending connection attempts.  
  
> [!NOTE]  
>  Increasing connection timeout and implementing connection retry logic will increase the probability that an application will connect to an availability group. Also, because a connection can fail because of an availability group failover, you should implement connection retry logic, retrying a failed connection until it reconnects.  
  
 The following [connection properties](../content/Setting-the-Connection-Properties.md) were added in [!INCLUDE[jdbc_40](../content/includes/jdbc_40_md.md)]:  
  
-   **multiSubnetFailover**  
  
-   **applicationIntent**  
  
## Connecting With MultiSubnetFailover  
 Always specify **multiSubnetFailover\=true** when connecting to the availability group listener of a [!INCLUDE[ssSQL11](../content/includes/ssSQL11_md.md)] availability group or a [!INCLUDE[ssSQL11](../content/includes/ssSQL11_md.md)] Failover Cluster Instance. **multiSubnetFailover** enables faster failover for all Availability Groups and failover cluster instances in [!INCLUDE[ssSQL11](../content/includes/ssSQL11_md.md)] and will significantly reduce failover time for single and multi\-subnet AlwaysOn topologies. During a multi\-subnet failover, the client will attempt connections in parallel. During a subnet failover, the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] will aggressively retry the TCP connection.  
  
 The **multiSubnetFailover** connection property indicates that the application is being deployed in an availability group or Failover Cluster Instance and that the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] will try to connect to the database on the primary [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] instance by trying to connect to all the IP addresses. When **MultiSubnetFailover\=true** is specified for a connection, the client retries TCP connection attempts faster than the operating system’s default TCP retransmit intervals. This enables faster reconnection after failover of either an AlwaysOn Availability Group or an AlwaysOn Failover Cluster Instance, and is applicable to both single\- and multi\-subnet Availability Groups and Failover Cluster Instances.  
  
 For more information about connection string keywords in the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)], see [Setting the Connection Properties](../content/Setting-the-Connection-Properties.md).  
  
 Specifying **multiSubnetFailover\=true** when connecting to something other than an availability group listener or Failover Cluster Instance may result in a negative performance impact, and is not supported.  
  
 If the security manager is not installed, the Java Virtual Machine caches virtual IP addresses \(VIPs\) for a finite period of time, by default, defined by your JDK implementation and the Java properties networkaddress.cache.ttl and networkaddress.cache.negative.ttl. If the JDK security manager is installed, the Java Virtual Machine will cache VIPs, and will not refresh the cache by default. You should set "time\-to\-live" \(networkaddress.cache.ttl\) to one day for the Java Virtual Machine cache. If you don’t change the default value to one day \(or so\), the old value will not be purged from the Java Virtual Machine cache when a VIP is added or updated. For more information about networkaddress.cache.ttl and networkaddress.cache.negative.ttl, see [http:\/\/download.oracle.com\/javase\/6\/docs\/technotes\/guides\/net\/properties.html](http://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html).  
  
 Use the following guidelines to connect to a server in an availability group or Failover Cluster Instance:  
  
-   The driver will generate an error if the **instanceName** connection property is used in the same connection string as the **multiSubnetFailover** connection property. This reflects the fact that SQL Browser is not used in an availability group. However, if the **portNumber** connection property is also specified, the driver will ignore **instanceName** and use **portNumber**.  
  
-   Use the **multiSubnetFailover** connection property when connecting to a single subnet or multi\-subnet, it will improve performance for both.  
  
-   To connect to an availability group, specify the availability group listener of the availability group as the server in your connection string. For example, jdbc:sqlserver:\/\/VNN1.  
  
-   Connecting to a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] instance configured with more than 64 IP addresses will cause a connection failure.  
  
-   Behavior of an application that uses the **multiSubnetFailover** connection property is not affected based on the type of authentication: [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Authentication, Kerberos Authentication, or Windows Authentication.  
  
-   Increase the value of **loginTimeout** to accommodate for failover time and reduce application connection retry attempts.  
  
-   Distributed transactions are not supported.  
  
 If read\-only routing is not in effect, connecting to a secondary replica location in an availability group will fail in the following situations:  
  
1.  If the secondary replica location is not configured to accept connections.  
  
2.  If an application uses **applicationIntent\=ReadWrite** \(discussed below\) and the secondary replica location is configured for read\-only access.  
  
 A connection will fail if a primary replica is configured to reject read\-only workloads and the connection string contains **ApplicationIntent\=ReadOnly**.  
  
## Upgrading to Use Multi\-Subnet Clusters from Database Mirroring  
 If you upgrade a [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] application that currently uses database mirroring to a multi\-subnet scenario, you should remove the **failoverPartner** connection property and replace it with **multiSubnetFailover** set to **true** and replace the server name in the connection string with a availability group listener. If a connection string uses **failoverPartner** and **multiSubnetFailover\=true**, the driver will generate an error. However, if a connection string uses **failoverPartner** and **multiSubnetFailover\=false** \(or **ApplicationIntent\=ReadWrite**\), the application will use database mirroring.  
  
 The driver will return an error if database mirroring is used on the primary database in the AG, and if **multiSubnetFailover\=true** is used in the connection string that connects to a primary database instead of to an availability group listener.  
  
## Specifying Application Intent  
 When **applicationIntent\=ReadOnly**, the client requests a read\-only workload when connecting to an AlwaysOn enabled database. The server will enforce the intent at connection time and during a USE database statement but only to an AlwaysOn enabled database.  
  
 The **applicationIntent** keyword does not work with legacy, read\-only databases.  
  
 A database can allow or disallow read workloads on the targeted AlwaysOn database. \(This is done with the **ALLOW\_CONNECTIONS** clause of the **PRIMARY\_ROLE** and **SECONDARY\_ROLE**[!INCLUDE[tsql](../content/includes/tsql_md.md)] statements.\)  
  
 The **applicationIntent** keyword is used to enable read\-only routing.  
  
## Read\-Only Routing  
 Read\-only routing is a feature that can ensure the availability of a read\-only replica of a database. To enable read\-only routing:  
  
1.  You must connect to an AlwaysOn Availability Group availability group listener.  
  
2.  The **applicationIntent** connection string keyword must be set to **ReadOnly**.  
  
3.  The Availability Group must be configured by the database administrator to enable read\-only routing.  
  
 It is possible that multiple connections using read\-only routing will not all connect to the same read\-only replica. Changes in database synchronization or changes in the server's routing configuration can result in client connections to different read\-only replicas. To ensure that all read\-only requests connect to the same read\-only replica, do not pass an availability group listener or virtual IP address to the **serverName** connection string keyword. Instead, specify the name of the read\-only instance.  
  
 Read\-only routing may take longer than connecting to the primary because read\-only routing first connects to the primary and then looks for the best available readable secondary. Because of this, you should increase your login timeout.  
  
## New Methods Supporting multiSubnetFailover and applicationIntent  
 The following methods give you programmatic access to the **multiSubnetFailover** and **applicationIntent** connection string keywords:  
  
-   [SQLServerDataSource.getApplicationIntent](../content/getApplicationIntent-Method--SQLServerDataSource-.md)  
  
-   [SQLServerDataSource.setApplicationIntent](../content/setApplicationIntent-Method--SQLServerDataSource-.md)  
  
-   [SQLServerDataSource.getMultiSubnetFailover](../content/getMultiSubnetFailover-Method--SQLServerDataSource-.md)  
  
-   [SQLServerDataSource.setMultiSubnetFailover](../content/setMultiSubnetFailover-Method--SQLServerDataSource-.md)  
  
-   [SQLServerDriver.getPropertyInfo](../content/getPropertyInfo-Method--SQLServerDriver-.md)  
  
 The **getMultiSubnetFailover**, **setMultiSubnetFailover**, **getApplicationIntent**, and **setApplicationIntent** methods are also added to [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md), [SQLServerConnectionPoolDataSource Class](../content/SQLServerConnectionPoolDataSource-Class.md), and [SQLServerXADataSource Class](../content/SQLServerXADataSource-Class.md).  
  
## SSL Certificate Validation  
 An availability group consists of multiple physical servers. [!INCLUDE[jdbc_40](../content/includes/jdbc_40_md.md)] added support for **Subject Alternate Name** in SSL certificates so multiple hosts can be associated with the same certificate. For more information on SSL, see [Understanding SSL Support](../content/Understanding-SSL-Support.md).  
  
## See Also  
 [Connecting to SQL Server with the JDBC Driver](../content/Connecting-to-SQL-Server-with-the-JDBC-Driver.md)   
 [Setting the Connection Properties](../content/Setting-the-Connection-Properties.md)  
  
  