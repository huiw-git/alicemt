---
title: "Diagnostic Connection for Database Administrators"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 2015-10-16
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 993e0820-17f2-4c43-880c-d38290bf7abc
caps.latest.revision: 65
caps.handback.revision: 0
manager: jhubbard
---
# Diagnostic Connection for Database Administrators
[!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] provides a special diagnostic connection for administrators when standard connections to the server are not possible. This diagnostic connection allows an administrator to access [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] to execute diagnostic queries and troubleshoot problems even when [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is not responding to standard connection requests.  
  
 This dedicated administrator connection (DAC) supports encryption and other security features of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. The DAC only allows changing the user context to another admin user.  
  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] makes every attempt to make DAC connect successfully, but under extreme situations it may not be successful.  
  
||  
|-|  
|**Applies to**: [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] ([!INCLUDE[ssKatmai](../../Topics/TopicNameContainA/tokens/ssKatmai_md.md)] through [current version](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[sqldbesa](../../Topics/TopicNameNotContainA/tokens/sqldbesa_md.md)].|  
  
## Connecting with DAC  
 By default, the connection is only allowed from a client running on the server. Network connections are not permitted unless they are configured by using the sp_configure stored procedure with the [remote admin connections option](../../Topics/TopicNameNotContainA/remote-admin-connections-Server-Configuration-Option.md).  
  
 Only members of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] sysadmin role can connect using the DAC.  
  
 The DAC is available and supported through the **sqlcmd** command-prompt utility using a special administrator switch (**-A**). For more information about using **sqlcmd**, see [Use sqlcmd with Scripting Variables](../../Topics/TopicNameNotContainA/Use-sqlcmd-with-Scripting-Variables.md). You can also connect prefixing **admin:**to the instance name in the format **sqlcmd -Sadmin:***<instance_name>.* You can also initiate a DAC from a [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] Query Editor by connecting to **admin:**<*instance_name*>.  
  
## Restrictions  
 Because the DAC exists solely for diagnosing server problems in rare circumstances, there are some restrictions on the connection:  
  
-   To guarantee that there are resources available for the connection, only one DAC is allowed per instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. If a DAC connection is already active, any new request to connect through the DAC is denied with error 17810.  
  
-   To conserve resources, [!INCLUDE[ssExpress](../../Topics/TopicNameContainA/tokens/ssExpress_md.md)] does not listen on the DAC port unless started with a trace flag 7806.  
  
-   The DAC initially attempts to connect to the default database associated with the login. After it is successfully connected, you can connect to the master database. If the default database is offline or otherwise not available, the connection will return error 4060. However, it will succeed if you override the default database to connect to the master database instead using the following command:  
  
     **sqlcmd –A –d**   
     **master**  
  
     We recommend that you connect to the master database with the DAC because master is guaranteed to be available if the instance of the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] is started.  
  
-   [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] prohibits running parallel queries or commands with the DAC. For example, error 3637 is generated if you execute either of the following statements with the DAC:  
  
    -   RESTORE  
  
    -   BACKUP  
  
-   Only limited resources are guaranteed to be available with the DAC. Do not use the DAC to run resource-intensive queries (for example. a complex join on large table) or queries that may block. This helps prevent the DAC from compounding any existing server problems. To avoid potential blocking scenarios, if you have to run queries that may block, run the query under snapshot-based isolation levels if possible; otherwise, set the transaction isolation level to READ UNCOMMITTED and set the LOCK_TIMEOUT value to a short value such as 2000 milliseconds, or both. This will prevent the DAC session from getting blocked. However, depending on the state that the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is in, the DAC session might get blocked on a latch. You might be able to terminate the DAC session using CNTRL-C but it is not guaranteed. In that case, your only option may be to restart [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
-   To guarantee connectivity and troubleshooting with the DAC, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] reserves limited resources to process commands run on the DAC. These resources are typically only enough for simple diagnostic and troubleshooting functions, such as those listed below.  
  
 Although you can theoretically run any [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statement that does not have to execute in parallel on the DAC, we strongly recommend that you restrict usage to the following diagnostic and troubleshooting commands:  
  
-   Querying dynamic management views for basic diagnostics such as sys.dm_tran_locks for the locking status, sys.dm_os_memory_cache_counters to check the health of caches, and sys.dm_exec_requests and sys.dm_exec_sessions for active sessions and requests. Avoid dynamic management views that are resource intensive (for example, sys.dm_tran_version_store scans the full version store and can cause extensive I/O) or that use complex joins. For information about performance implications, see the documentation for the specific [dynamic management view](assetId:///cf893ecb-0bf6-4cbf-ac00-8a1099e405b1).  
  
-   Querying catalog views.  
  
-   Basic DBCC commands such as DBCC FREEPROCCACHE, DBCC FREESYSTEMCACHE, DBCC DROPCLEANBUFFERS**,** and DBCC SQLPERF. Do not run resource-intensive commands such as **DBCC** CHECKDB, DBCC DBREINDEX, or DBCC SHRINKDATABASE.  
  
-   [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] KILL*<spid\>* command. Depending on the state of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], the KILL command might not always succeed; then the only option may be to restart [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. The following are some general guidelines:  
  
    -   Verify that the SPID was actually killed by querying `SELECT * FROM sys.dm_exec_sessions WHERE session_id = <spid>`. If it returns no rows, it means the session was killed.  
  
    -   If the session is still there, verify whether there are tasks assigned to this session by running the query `SELECT * FROM sys.dm_os_tasks WHERE session_id = <spid>`. If you see the task there, most likely your session is currently being killed. Note that this may take considerable amount of time and may not succeed at all.  
  
    -   If there are no tasks in the sys.dm_os_tasks associated with this session, but the session remains in sys.dm_exec_sessions after executing the KILL command, it means that you do not have a worker available. Select one of the currently running tasks (a task listed in the sys.dm_os_tasks view with a `sessions_id <> NULL`), and kill the session associated with it to free up the worker. Note that it may not be enough to kill a single session: you may have to kill multiple ones.  
  
## DAC Port  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] listens for the DAC on TCP port 1434 if available or a TCP port dynamically assigned upon [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] startup. The error log contains the port number the DAC is listening on. By default the DAC listener accepts connection on only the local port. For a code sample that activates remote administration connections, see [remote admin connections Server Configuration Option](../../Topics/TopicNameNotContainA/remote-admin-connections-Server-Configuration-Option.md).  
  
 After the remote administration connection is configured, the DAC listener is enabled without requiring a restart of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] and a client can now connect to the DAC remotely. You can enable the DAC listener to accept connections remotely even if [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is unresponsive by first connecting to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] using the DAC locally, and then executing the sp_configure stored procedure to accept connection from remote connections.  
  
 On cluster configurations, the DAC will be off by default. Users can execute the remote admin connection option of sp_configure to enable the DAC listener to access a remote connection. If [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is unresponsive and the DAC listener is not enabled, you might have to restart [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] to connect with the DAC. Therefore, we recommend that you enable the remote admin connections configuration option on clustered systems.  
  
 The DAC port is assigned dynamically by [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] during startup. When connecting to the default instance, the DAC avoids using a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Resolution Protocol (SSRP) request to the SQL Server Browser Service when connecting. It first connects over TCP port 1434. If that fails, it makes an SSRP call to get the port. If [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Browser is not listening for SSRP requests, the connection request returns an error. Refer to the error log to find the port number DAC is listening on. If [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is configured to accept remote administration connections, the DAC must be initiated with an explicit port number:  
  
 **sqlcmd**  
 **–S**  
 **tcp:** *<server\>,<port\>*  
  
 The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] error log lists the port number for the DAC, which is 1434 by default. If [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is configured to accept local DAC connections only, connect using the loopback adapter using the following command:  
  
 **sqlcmd**  
 **–S**  
 **127.0.0.1**,**1434**  
  
> [!TIP]  
>  When connecting to the [!INCLUDE[ssSDSfull](../../Topics/TopicNameContainA/tokens/ssSDSfull_md.md)] with the DAC, you must also specify the database name in the connection string by using the -d option.  
  
## Example  
 In this example, an administrator notices that server `URAN123` is not responding and wants to diagnose the problem. To do this, the user activates the `sqlcmd` command prompt utility and connects to server `URAN123` using `-A` to indicate the DAC.  
  
 `sqlcmd -S URAN123 -U sa -P <xxx> –A`  
  
 The administrator can now execute queries to diagnose the problem and possibly terminate the unresponsive sessions.  
  
 A similar example connecting to [!INCLUDE[ssSDS](../../Topics/TopicNameContainA/tokens/ssSDS_md.md)] would use the following command including the -d parameter to specify the database:  
  
 `sqlcmd -S serverName.database.windows.net,1434 -U sa -P <xxx> -d AdventureWorks`  
  
## Related Tasks  
  
## Related Content  
 [Use sqlcmd with Scripting Variables](../../Topics/TopicNameNotContainA/Use-sqlcmd-with-Scripting-Variables.md)  
  
 [sqlcmd Utility](../../Topics/TopicNameNotContainA/sqlcmd-Utility.md)  
  
 [SELECT (Transact-SQL)](assetId:///dc85caea-54d1-49af-b166-f3aa2f3a93d0)  
  
 [sp_who (Transact-SQL)](assetId:///132dfb08-fa79-422e-97d4-b2c4579c6ac5)  
  
 [sp_lock (Transact-SQL)](assetId:///9eaa0ec2-2ad9-457c-ae48-8da92a03dcb0)  
  
 [KILL (Transact-SQL)](assetId:///071cf260-c794-4b45-adc0-0e64097938c0)  
  
 [DBCC CHECKALLOC (Transact-SQL)](assetId:///bc1218eb-ffff-44ce-8122-6e4fa7d68a79)  
  
 [DBCC CHECKDB (Transact-SQL)](assetId:///2c506167-0b69-49f7-9282-241e411910df)  
  
 [DBCC OPENTRAN (Transact-SQL)](assetId:///63163843-226f-42d3-9e2c-b634fbf06943)  
  
 [DBCC INPUTBUFFER (Transact-SQL)](assetId:///a44d702b-b3fb-4950-8c8f-1adcf3f514ba)  
  
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)  
  
 [Transaction Related Dynamic Management Objects](assetId:///4db9f715-995e-4e71-9544-26eb59e9fae0)  
  
 [Trace Flags (Transact-SQL)](assetId:///b971b540-1ac2-435b-b191-24399eb88265)