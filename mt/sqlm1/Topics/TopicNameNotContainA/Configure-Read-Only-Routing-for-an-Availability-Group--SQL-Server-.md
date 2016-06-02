---
title: Configure Read-Only Routing for an Availability Group (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7bd89ddd-0403-4930-a5eb-3c78718533d4
---
# Configure Read-Only Routing for an Availability Group (SQL Server)
  To configure an Always On availability group to support read\-only routing in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], you can use either [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] or PowerShell. *Read\-only routing* refers to the ability of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to route qualifying read\-only connection requests to an available Always On [readable secondary replica](../Topic/Active%20Secondaries:%20Readable%20Secondary%20Replicas%20\(Always%20On%20Availability%20Groups\).md) \(that is, a replica that is configured to allow read\-only workloads when running under the secondary role\). To support read\-only routing, the availability group must possess an [availability group listener](../Topic/Availability%20Group%20Listeners,%20Client%20Connectivity,%20and%20Application%20Failover%20\(SQL%20Server\).md). Read\-only clients must direct their connection requests to this listener, and the client's connection strings must specify the application intent as "read\-only." That is, they must be *read\-intent connection requests*.  
  
> [!NOTE]  
>  For information about how to configure a readable secondary replica, see [Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;](../Topic/Configure%20Read-Only%20Access%20on%20an%20Availability%20Replica%20\(SQL%20Server\).md).  
  
-   **Before you begin:**  
  
     [Prerequisites](#Prerequisites)  
  
     [What Replica Properties Do you Need to Configure to Support Read-Only Routing?](#RORReplicaProperties)  
  
     [Security](#Security)  
  
-   **To Configure read\-only routing, using:**  
  
     [Transact\-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
    > [!NOTE]  
    >  Configuring read\-only routing is not supported by [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
-   **Follow Up:**  [After Configuring Read\-Only Routing](#FollowUp)  
  
-   [Related Tasks](#RelatedTasks)  
  
-   [Related Content](#RelatedContent)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Prerequisites"></a> Prerequisites  
  
-   The availability group must possess an availability group listener. For more information, see [Create or Configure an Availability Group Listener &#40;SQL Server&#41;](../Topic/Create%20or%20Configure%20an%20Availability%20Group%20Listener%20\(SQL%20Server\).md).  
  
-   One or more availability replicas must be configured to accept read\-only in the secondary role \(that is, to be [readable secondary replicas](../Topic/Active%20Secondaries:%20Readable%20Secondary%20Replicas%20\(Always%20On%20Availability%20Groups\).md)\). For more information, see [Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;](../Topic/Configure%20Read-Only%20Access%20on%20an%20Availability%20Replica%20\(SQL%20Server\).md).  
  
-   You must be connected to the server instance that hosts the current primary replica.  
  
###  <a name="RORReplicaProperties"></a> What Replica Properties Do you Need to Configure to Support Read\-Only Routing?  
  
-   For each readable secondary replica that is to support read\-only routing, you need to specify a *read\-only routing URL*. This URL takes effect only when the local replica is running under the secondary role. The read\-only routing URL must be specified on a replica\-by\-replica basis, as needed. Each read\-only routing URL is used for routing read\-intent connection requests to a specific readable secondary replica. Typically, every readable secondary replica is assigned a read\-only routing URL.  
  
     For information about calculating the read\-only routing URL for an availability replica, see [Calculating read\_only\_routing\_url for Always On](http://blogs.msdn.com/b/mattn/archive/2012/04/25/calculating-read-only-routing-url-for-Always%20On.aspx).  
  
-   For each availability replica that you want to support read\-only routing when it is the primary replica, you need to specify a *read\-only routing list*. A given read\-only routing list takes effect only when the local replica is running under the primary role. This list must be specified on a replica\-by\-replica basis, as needed. Typically, each read\-only routing list would contain every read\-only routing URL, with the URL of the local replica at the end of the list.  
  
    > [!NOTE]  
    >  Read\-intent connection requests are routed to the first available entry on the read\-only routing list of the current primary replica. However, load\-balancing across read\-only replicas is supported. For more information, see [Configure load-balancing across read-only replicas](../Topic/Configure%20Read-Only%20Routing%20for%20an%20Availability%20Group%20\(SQL%20Server\).md#loadbalancing).  
  
> [!NOTE]  
>  For information about availability group listeners and more information about read\-only routing, see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../Topic/Availability%20Group%20Listeners,%20Client%20Connectivity,%20and%20Application%20Failover%20\(SQL%20Server\).md).  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
  
|Task|Permissions|  
|----------|-----------------|  
|To configure replicas when creating an availability group|Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.|  
|To modify an availability replica|Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.|  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
### Configure a read\-only routing list  
 Use the following steps to configure read\-only routing using Transact\-SQL. For a code example, see [Example \(Transact\-SQL\)](#TsqlExample), later in this section.  
  
1.  Connect to the server instance that hosts the primary replica.  
  
2.  If you are specifying a replica for a new availability group, use the [CREATE AVAILABILITY GROUP](../Topic/CREATE%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md)[!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement. If you are adding or modifying a replica for an existing availability group, use the [ALTER AVAILABILITY GROUP](../Topic/ALTER%20AVAILABILITY%20GROUP%20\(Transact-SQL\).md)[!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement.  
  
    -   To configure read\-only routing for the secondary role, in the ADD REPLICA or MODIFY REPLICA WITH clause, specify the SECONDARY\_ROLE option, as follows:  
  
         SECONDARY\_ROLE **\(** READ\_ONLY\_ROUTING\_URL **\='**TCP**:\/\/***system\-address***:***port***'\)**  
  
         The parameters of the read\-only routing URL are as follows:  
  
         *system\-address*  
         Is a string, such as a system name, a fully qualified domain name, or an IP address, that unambiguously identifies the destination computer system.  
  
         *port*  
         Is a port number that is used by the Database Engine of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance.  
  
         For example:   `SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER01.contoso.com:1433')`  
  
         In a MODIFY REPLICA clause the ALLOW\_CONNECTIONS is optional if the replica is already configured to allow read\-only connections.  
  
         For more information, see [Calculating read\_only\_routing\_url for Always On](http://blogs.msdn.com/b/mattn/archive/2012/04/25/calculating-read-only-routing-url-for-Always%20On.aspx).  
  
    -   To configure read\-only routing for the primary role, in the ADD REPLICA or MODIFY REPLICA WITH clause, specify the PRIMARY\_ROLE option, as follows:  
  
         PRIMARY\_ROLE **\(** READ\_ONLY\_ROUTING\_LIST **\=\(‘***server***’** \[ **,**...*n* \] **\)\)**  
  
         where, *server* identifies a server instance that hosts a read\-only secondary replica in the availability group.  
  
         For example:   `PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('Server1','Server2'))`  
  
        > [!NOTE]  
        >  You must set the read\-only routing URL before configuring the read\-only routing list.  
  
###  <a name="loadbalancing"></a> Configure load\-balancing across read\-only replicas  
 Beginning with [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)], you can configure load\-balancing across a set of read\-only replicas. Previously, read\-only routing always directed traffic to the first available replica in the routing list. To take advantage of this feature, use one level of nested parentheses around the **READ\_ONLY\_ROUTING\_LIST** server instances in the **CREATE AVAILABILITY GROUP** or **ALTER AVAILABILITY GROUP** commands.  
  
 For example, the following routing list load balances read\-intent connection request across two read\-only replicas, `Server1` and `Server2`. The nested parentheses that surround these servers identify the load\-balanced set. If neither replica is available in that set, it will proceed to attempt to sequentially connect to the other replicas, `Server3` and `Server4`, in the read\-only routing list.  
  
```tsql  
READ_ONLY_ROUTING_LIST = (('Server1','Server2'), 'Server3', 'Server4')  
```  
  
 Note that each entry in the routing list can itself be a set of load\-balanced read\-only replicas. The following example demonstrates this.  
  
```tsql  
READ_ONLY_ROUTING_LIST = (('Server1','Server2'), ('Server3', 'Server4', 'Server5'), 'Server6')  
```  
  
 Only one level of nested parentheses is supported.  
  
###  <a name="TsqlExample"></a> Example \(Transact\-SQL\)  
 The following example modifies two availability replicas of an existing availability group, `AG1` to support read\-only routing if one of these replicas currently owns the primary role. To identify the server instances that host the availability replica, this example specifies the instance names—`COMPUTER01` and `COMPUTER02`.  
  
```  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER01' WITH   
(SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY));  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER01' WITH   
(SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER01.contoso.com:1433'));  
  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER02' WITH   
(SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY));  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER02' WITH   
(SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER02.contoso.com:1433'));  
  
ALTER AVAILABILITY GROUP [AG1]   
MODIFY REPLICA ON  
N'COMPUTER01' WITH   
(PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('COMPUTER02','COMPUTER01')));  
  
ALTER AVAILABILITY GROUP [AG1]   
MODIFY REPLICA ON  
N'COMPUTER02' WITH   
(PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('COMPUTER01','COMPUTER02')));  
GO  
  
```  
  
##  <a name="PowerShellProcedure"></a> Using PowerShell  
  
### Configure a read\-only routing list  
 Use the following steps to configure read\-only routing using PowerShell. For a code example, see [Example \(PowerShell\)](#PSExample), later in this section.  
  
1.  Set default \(**cd**\) to the server instance that hosts the primary replica.  
  
2.  When adding an availability replica to an availability group, use the **New\-SqlAvailabilityReplica** cmdlet. When modifying an existing availability replica, use the **Set\-SqlAvailabilityReplica** cmdlet. The relevant parameters are as follows:  
  
    -   To configure read\-only routing for the secondary role, specify the **ReadonlyRoutingConnectionUrl"***url***"** parameter.  
  
         where, *url* is the connectivity fully\-qualified domain name \(FQDN\) and port to use when routing to the replica for read\-only connections. For example:  `-ReadonlyRoutingConnectionUrl "TCP://DBSERVER8.manufacturing.Adventure-Works.com:7024"`  
  
         For more information, see [Calculating read\_only\_routing\_url for Always On](http://blogs.msdn.com/b/mattn/archive/2012/04/25/calculating-read-only-routing-url-for-Always%20On.aspx).  
  
    -   To configure connection access for the primary role, specify **ReadonlyRoutingList"***server***"** \[ **,**...*n* \], where *server* identifies a server instance that hosts a read\-only secondary replica in the availability group. For example:  `-ReadOnlyRoutingList "SecondaryServer","PrimaryServer"`  
  
        > [!NOTE]  
        >  You must set the read\-only routing URL of a replica before configuring its read\-only routing list.  
  
    > [!NOTE]  
    >  To view the syntax of a cmdlet, use the **Get\-Help** cmdlet in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell environment. For more information, see [Get Help SQL Server PowerShell](../../Topics\TopicNameNotContainA/Get-Help-SQL-Server-PowerShell.md).  
  
### Set up and use the SQL Server PowerShell provider  
  
-   [SQL Server PowerShell Provider](../../Topics\TopicNameNotContainA/SQL-Server-PowerShell-Provider.md)  
  
-   [Get Help SQL Server PowerShell](../../Topics\TopicNameNotContainA/Get-Help-SQL-Server-PowerShell.md)  
  
###  <a name="PSExample"></a> Example \(PowerShell\)  
 The following example configures the primary replica and one secondary replica in an availability group for read\-only routing. First, the example assigns a read\-only routing URL to each replica. Then it sets the read\-only routing list on the primary replica. Connections with the "ReadOnly" property set in the connection string will be redirected to the secondary replica. If this secondary replica is not readable \(as determined by the **ConnectionModeInSecondaryRole** setting\), the connection will be directed back to the primary replica.  
  
```  
Set-Location SQLSERVER:\SQL\PrimaryServer\default\AvailabilityGroups\MyAg  
$primaryReplica = Get-Item "AvailabilityReplicas\PrimaryServer"  
$secondaryReplica = Get-Item "AvailabilityReplicas\SecondaryServer"  
  
Set-SqlAvailabilityReplica -ReadOnlyRoutingConnectionUrl "TCP://PrimaryServer.domain.com:1433" -InputObject $primaryReplica  
Set-SqlAvailabilityReplica -ReadOnlyRoutingConnectionUrl "TCP://SecondaryServer.domain.com:1433" -InputObject $secondaryReplica  
Set-SqlAvailabilityReplica -ReadOnlyRoutingList "SecondaryServer","PrimaryServer" -InputObject $primaryReplica  
```  
  
##  <a name="FollowUp"></a> Follow Up: After Configuring Read\-Only Routing  
 Once the current primary replica and the readable secondary replicas are configured to support read\-only routing in both roles, the readable secondary replicas can receive read read\-intent connection requests from clients that connect via the availability group listener.  
  
> [!TIP]  
>  When using the [bcp Utility](../../Topics\TopicNameNotContainA/bcp-Utility.md) or [sqlcmd Utility](../../Topics\TopicNameNotContainA/sqlcmd-Utility.md), you can specify read\-only access to any secondary replica that is enabled for read\-only access by specifying the **\-K ReadOnly** switch.  
  
###  <a name="ConnStringReqsRecs"></a> Requirements and Recommendations for Client Connection\-Strings  
 For a client application to use read\-only routing, its connection string must satisfy the following requirements:  
  
-   Use the TCP protocol.  
  
-   Set the application intent attribute\/property to readonly.  
  
-   Reference the listener of an availability group that is configured to support read\-only routing.  
  
-   Reference a database in that availability group.  
  
 In addition, we recommend that connection strings enable multi\-subnet failover, which supports a parallel client thread for each replica on each subnet. This minimizes client reconnection time after a failover.  
  
 The syntax for a connection string depends on the SQL Server provider an application is using. The following example connection string for the .NET Framework Data Provider 4.0.2 for SQL Server illustrates the parts of a connection string that are required and recommended to work for read\-only routing.  
  
```  
Server=tcp:MyAgListener,1433;Database=Db1;IntegratedSecurity=SSPI;ApplicationIntent=ReadOnly;MultiSubnetFailover=True  
```  
  
 For more information about read\-only application intent and read\-only routing, see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../Topic/Availability%20Group%20Listeners,%20Client%20Connectivity,%20and%20Application%20Failover%20\(SQL%20Server\).md).  
  
### If Read\-Only Routing is Not Working Correctly  
 For information about troubleshooting a read\-only routing configuration, see [Read-Only Routing is Not Working Correctly](../Topic/Troubleshoot%20Always%20On%20Availability%20Groups%20Configuration%20\(SQL%20Server\).md#ROR).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To view read\-only routing configurations**  
  
-   [sys.availability_read_only_routing_lists &#40;Transact-SQL&#41;](../Topic/sys.availability_read_only_routing_lists%20\(Transact-SQL\).md)  
  
-   [sys.availability_replicas &#40;Transact-SQL&#41;](../Topic/sys.availability_replicas%20\(Transact-SQL\).md) \(**read\_only\_routing\_url** column\)  
  
 **To configure client connection access**  
  
-   [Create or Configure an Availability Group Listener &#40;SQL Server&#41;](../Topic/Create%20or%20Configure%20an%20Availability%20Group%20Listener%20\(SQL%20Server\).md)  
  
-   [Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;](../Topic/Configure%20Read-Only%20Access%20on%20an%20Availability%20Replica%20\(SQL%20Server\).md)  
  
 **To use connection strings in applications**  
  
-   [SQL Server Native Client Support for High Availability, Disaster Recovery](../Topic/SQL%20Server%20Native%20Client%20Support%20for%20High%20Availability,%20Disaster%20Recovery.md)  
  
-   [Using Connection String Keywords with SQL Server Native Client](../Topic/Using%20Connection%20String%20Keywords%20with%20SQL%20Server%20Native%20Client.md)  
  
##  <a name="RelatedContent"></a> Related Content  
  
-   **Blogs:**  
  
     [Calculating read\_only\_routing\_url for Always On](http://blogs.msdn.com/b/mattn/archive/2012/04/25/calculating-read-only-routing-url-for-Always%20On.aspx)  
  
     [SQL Server Always On Team Blogs: The official SQL Server Always On Team Blog](http://blogs.msdn.com/b/sqlAlways%20On/)  
  
     [CSS SQL Server Engineers Blogs](http://blogs.msdn.com/b/psssql/)  
  
-   **White papers:**  
  
     [Microsoft White Papers for SQL Server 2012](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [SQL Server Customer Advisory Team Whitepapers](http://sqlcat.com/)  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Active Secondaries: Readable Secondary Replicas &#40;Always On Availability Groups&#41;](../Topic/Active%20Secondaries:%20Readable%20Secondary%20Replicas%20\(Always%20On%20Availability%20Groups\).md)   
 [About Client Connection Access to Availability Replicas &#40;SQL Server&#41;](../Topic/About%20Client%20Connection%20Access%20to%20Availability%20Replicas%20\(SQL%20Server\).md)   
 [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../Topic/Availability%20Group%20Listeners,%20Client%20Connectivity,%20and%20Application%20Failover%20\(SQL%20Server\).md)  
  
  