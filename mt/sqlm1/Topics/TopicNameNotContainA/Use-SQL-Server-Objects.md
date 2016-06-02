---
title: Use SQL Server Objects
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bcd731b1-3c4e-4086-b58a-af7a3af904ad
---
# Use SQL Server Objects
  Microsoft [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provides objects and counters that can be used by System Monitor to monitor activity in computers running an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. An object is any [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] resource, such as a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] lock or Windows process. Each object contains one or more counters that determine various aspects of the objects to monitor. For example, the **SQL Server Locks** object contains counters called **Number of Deadlocks\/sec** and **Lock Timeouts\/sec**.  
  
 Some objects have several instances if multiple resources of a given type exist on the computer. For example, the **Processor** object type will have multiple instances if a system has multiple processors. The **Databases** object type has one instance for each database on [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Some object types \(for example, the **Memory Manager** object\) have only one instance. If an object type has multiple instances, you can add counters to track statistics for each instance, or in many cases, all instances at once. Counters for the default instance appear in the format **SQLServer:***\<object name\>*. Counters for named instances appear in the format **MSSQL$***\<instance name\>***:***\<counter name\>* or **SQLAgent$***\<instance name\>***:***\<counter name\>*.  
  
 By adding or removing counters to the chart and saving the chart settings, you can specify the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] objects and counters that are monitored when System Monitor is started.  
  
 You can configure System Monitor to display statistics from any [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] counter. In addition, you can set a threshold value for any [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] counter and then generate an alert when a counter exceeds a threshold. For more information about setting an alert, see [Create a SQL Server Database Alert](../../Topics\TopicNameContainA/Create-a-SQL-Server-Database-Alert.md).  
  
> [!TIP]  
>  You can also return the performance counter values by querying the [sys.dm_os_performance_counters &#40;Transact-SQL&#41;](../Topic/sys.dm_os_performance_counters%20\(Transact-SQL\).md) dynamic management view.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] statistics are displayed only when an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is installed. If you stop and restart an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], the display of statistics is interrupted and resumes automatically. Also note that you will see [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] counters in the System Monitor snap\-in even if [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is not running. On a clustered instance, performance counters only function on the node where [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is running.  
  
 This topic contains the following sections:  
  
-   [SQL Server Agent Performance Objects](#SQLServerAgentPOs)  
  
-   [Service Broker Performance Objects](#ServiceBrokerPOs)  
  
-   [SQL Server Performance Objects](#SQLServerPOs)  
  
-   [SQL Server Replication Performance Objects](#SQLServerReplicationPOs)  
  
-   [SSIS Pipeline Counters](#SsisPipelineCounters)  
  
-   [Required Permissions](#RequiredPermissions)  
  
##  <a name="SQLServerAgentPOs"></a> SQL Server Agent Performance Objects  
 The following table lists the performance objects provided for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent:  
  
|Performance object|Description|  
|------------------------|-----------------|  
|[SQLAgent:Alerts](../../Topics\TopicNameNotContainA/SQL-Server-Agent,-Alerts-Object.md)|Provides information about [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent alerts.|  
|[SQLAgent:Jobs](../../Topics\TopicNameNotContainA/SQL-Server-Agent,-Jobs-Object.md)|Provides information about [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent jobs.|  
|[SQLAgent:JobSteps](../../Topics\TopicNameNotContainA/SQL-Server-Agent,-JobSteps-Object.md)|Provides information about [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent job steps.|  
|[SQLAgent:Statistics](../../Topics\TopicNameNotContainA/SQL-Server-Agent,-Statistics-Object.md)|Provides general information about [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent.|  
  
##  <a name="ServiceBrokerPOs"></a> Service Broker Performance Objects  
 The following table lists the performance objects provided for [!INCLUDE[ssSB](../../Token\Other/ssSB_md.md)].  
  
|Performance object|Description|  
|------------------------|-----------------|  
|[SQLServer:Broker Activation](../../Topics\TopicNameNotContainA/SQL-Server,-Broker-Activation-Object.md)|Provides information about [!INCLUDE[ssSB](../../Token\Other/ssSB_md.md)]\-activated tasks.|  
|[SQLServer:Broker Statistics](../../Topics\TopicNameNotContainA/SQL-Server,-Broker-Statistics-Object.md)|Provides general [!INCLUDE[ssSB](../../Token\Other/ssSB_md.md)] information.|  
|[SQLServer:Broker Transport](../../Topics\TopicNameNotContainA/SQL-Server,-Broker---DBM-Transport-Object.md)|Provides information on [!INCLUDE[ssSB](../../Token\Other/ssSB_md.md)] networking.|  
  
##  <a name="SQLServerPOs"></a> SQL Server Performance Objects  
 The following table describes [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] objects.  
  
|Performance object|Description|  
|------------------------|-----------------|  
|[SQLServer:Access Methods](../../Topics\TopicNameNotContainA/SQL-Server,-Access-Methods-Object.md)|Searches through and measures allocation of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database objects \(for example, the number of index searches or number of pages that are allocated to indexes and data\).|  
|[SQLServer:Backup Device](../../Topics\TopicNameNotContainA/SQL-Server,-Backup-Device-Object.md)|Provides information about backup devices used by backup and restore operations, such as the throughput of the backup device.|  
|[SQLServer:Buffer Manager](../../Topics\TopicNameNotContainA/SQL-Server,-Buffer-Manager-Object.md)|Provides information about the memory buffers used by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], such as **freememory** and **buffer cache hit ratio**.|  
|[SQL Server:Buffer Node](../Topic/SQL%20Server:Buffer%20Node.md)|Provides information about how frequently [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] requests and accesses free pages.|  
|[SQLServer:CLR](../../Topics\TopicNameNotContainA/SQL-Server,-CLR-Object.md)|Provides information about the common language runtime \(CLR\).|  
|[SQLServer:Columnstore](../../Topics\TopicNameNotContainA/SQL-Server,-Columnstore-Object.md)|**Applies to**: [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] \([!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] through [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]\).<br /><br /> Provides information about rowgroups and segments for columnstore indexes.|  
|[SQLServer:Cursor Manager by Type](../../Topics\TopicNameNotContainA/SQL-Server,-Cursor-Manager-by-Type-Object.md)|Provides information about cursors.|  
|[SQLServer:Cursor Manager Total](../../Topics\TopicNameNotContainA/SQL-Server,-Cursor-Manager-Total-Object.md)|Provides information about cursors.|  
|[SQLServer:Database Mirroring](../../Topics\TopicNameNotContainA/SQL-Server,-Database-Mirroring-Object.md)|Provides information about database mirroring.|  
|[SQLServer:Databases](../../Topics\TopicNameNotContainA/SQL-Server,-Databases-Object.md)|Provides information about a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database, such as the amount of free log space available or the number of active transactions in the database. There can be multiple instances of this object.|  
|[SQL Server:Deprecated Features](../../Topics\TopicNameNotContainA/SQL-Server,-Deprecated-Features-Object.md)|Counts the number of times that deprecated features are used.|  
|[SQLServer:Exec Statistics](../../Topics\TopicNameNotContainA/SQL-Server,-ExecStatistics-Object.md)|Provides information about execution statistics.|  
|[SQL Server:External Scripts](../../Topics\TopicNameNotContainA/SQL-Server,-External-Scripts-Object.md)|**Applies to**: [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] \([!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] through [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]\).<br /><br /> Provides information about external script execution.|  
|[SQLServer:General Statistics](../../Topics\TopicNameNotContainA/SQL-Server,-General-Statistics-Object.md)|Provides information about general server\-wide activity, such as the number of users who are connected to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].|  
|[SQL Server:HADR Availability Replica](../../Topics\TopicNameNotContainA/SQL-Server,-Availability-Replica.md)|Provides information about [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)][!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] availability replicas.|  
|[SQL Server:HADR Database Replica](../../Topics\TopicNameNotContainA/SQL-Server,-Database-Replica.md)|Provides information about [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)][!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] database replicas.|  
|[SQLServer:Latches](../../Topics\TopicNameNotContainA/SQL-Server,-Latches-Object.md)|Provides information about the latches on internal resources, such as database pages, that are used by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].|  
|[SQLServer:Locks](../../Topics\TopicNameNotContainA/SQL-Server,-Locks-Object.md)|Provides information about the individual lock requests made by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], such as lock time\-outs and deadlocks. There can be multiple instances of this object.|  
|[SQLServer:Memory Manager](../../Topics\TopicNameNotContainA/SQL-Server,-Memory-Manager-Object.md)|Provides information about [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] memory usage, such as the total number of lock structures currently allocated.|  
|[SQLServer:Plan Cache](../../Topics\TopicNameNotContainA/SQL-Server,-Plan-Cache-Object.md)|Provides information about the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] cache used to store objects such as stored procedures, triggers, and query plans.|  
|[SQLServer: Query Store](../../Topics\TopicNameNotContainA/SQL-Server,-Query-Store-Object.md)|Provides information about the Query Store.|  
|[SQLServer: Resource Pool Stats](../../Topics\TopicNameNotContainA/SQL-Server,-Resource-Pool-Stats-Object.md)|Provides information about Resource Governor resource pool statistics.|  
|[SQLServer:SQL Errors](../../Topics\TopicNameNotContainA/SQL-Server,-SQL-Errors-Object.md)|Provides information about [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] errors.|  
|[SQLServer:SQL Statistics](../../Topics\TopicNameNotContainA/SQL-Server,-SQL-Statistics-Object.md)|Provides information about aspects of [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] queries, such as the number of batches of [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements received by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].|  
|[SQLServer:Transactions](../../Topics\TopicNameNotContainA/SQL-Server,-Transactions-Object.md)|Provides information about the active transactions in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], such as the overall number of transactions and the number of snapshot transactions.|  
|[SQLServer:User Settable](../../Topics\TopicNameNotContainA/SQL-Server,-User-Settable-Object.md)|Performs custom monitoring. Each counter can be a custom stored procedure or any [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement that returns a value to be monitored.|  
|[SQLServer: Wait Statistics](../../Topics\TopicNameNotContainA/SQL-Server,-Wait-Statistics-Object.md)|Provides information about waits.|  
|[SQLServer: Workload Group Stats](../../Topics\TopicNameNotContainA/SQL-Server,-Workload-Group-Stats-Object.md)|Provides information about Resource Governor workload group statistics.|  
  
##  <a name="SQLServerReplicationPOs"></a> SQL Server Replication Performance Objects  
 The following table lists the performance objects provided for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] replication:  
  
|Performance object|Description|  
|------------------------|-----------------|  
|**SQLServer:Replication Agents**<br /><br /> **SQLServer:Replication Snapshot**<br /><br /> **SQLServer:Replication Logreader**<br /><br /> **SQLServer:Replication Dist.**<br /><br /> **SQLServer:Replication Merge**<br /><br /> For more information, see [Monitoring Replication with System Monitor](../../Topics\TopicNameNotContainA/Monitoring-Replication-with-System-Monitor.md).|Provides information about replication agent activity.|  
  
##  <a name="SsisPipelineCounters"></a> SSIS Pipeline Counters  
 For the **SSIS Pipeline** counter, see [Performance Counters](../../Topics\TopicNameNotContainA/Performance-Counters.md).  
  
##  <a name="RequiredPermissions"></a> Required Permissions  
 Use of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] objects depends on Windows permissions, except **SQLAgent:Alerts**. Users must be a member of the **sysadmin** fixed server role to use **SQLAgent:Alerts**.  
  
## See Also  
 [Use Performance Objects](../Topic/Use%20Performance%20Objects.md)   
 [sys.dm_os_performance_counters &#40;Transact-SQL&#41;](../Topic/sys.dm_os_performance_counters%20\(Transact-SQL\).md)  
  
  