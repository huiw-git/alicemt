---
title: DMVs for SQL Server R Services
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b3643ea0-d9f3-463f-8ece-572127f32a24
---
# DMVs for SQL Server R Services

The topic lists the system catalog views and DMVs that are related to [!INCLUDE[rsql_productname_md](../../Token\Other/rsql_productname_md.md)]. 


For information about extended events, see [Extended Events for SQL Server R Services](../../Topics\TopicNameNotContainA/Extended-Events-for-SQL-Server-R-Services.md).

> [!NOTE]
> 
> System views related to [!INCLUDE[rsql_productname_md](../../Token\Other/rsql_productname_md.md)] are not present unless you have enabled the feature.

## System Configuration and System Resources

You can monitor and analyze the resources used by R scripts by using [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)] system catalog views and DMVs.

**General**
+ [ sys.dm_exec_sessions](sys.dm_exec_sessions%20\(Transact-SQL\).md)

  Returns information for both user connections and system sessions. You can identify the system sessions by looking at the _session_id_ column; values greater than or equal to 51 are user connections and values lower than 51 are system processes. 



+ [sys.dm_os_performance_counters (Transact-SQL)](sys.dm_os_performance_counters%20\(Transact-SQL\).md)

  Returns a row for each system performance counter being used by the server.  You can use this information to see how many scripts ran, which scripts were run using which authentication mode, or how many R calls were issued on the instance overall.

  For example, to get just the counters related to R script:

  ~~~~

  SELECT * from sys.dm_os_performance_counters WHERE object_name LIKE '%Extended Script%'

  ~~~~

  The following counters are reported by this DMV for external scripts per instance:

  + **Total Executions**: Number of R processes started by local or remote calls
  + **Parallel Executions**: Number of times that a script included the @parallel specification and that SQL Server was able to generate and use a parallel query plan
  + **Streaming Executions**: 
  + **SQL CC Executions**: Number of R scripts run where the call was instantiated remotely and SQL Server used as the compute context 
  + **Implied Auth. Logins**: Number of times that an ODBC loopback call was made using implied authentication; that is, the SQL Server executed the call on behalf of the user sending the script request
  + **Total Execution Time (ms)**: Time elapsed between the call 
  + **Execution Errors**: Number of times scripts reported errors. This count does not include R errors.


+ sys.dm_external_script_requests

  The following counters are reported by this DMV for individual requests:
  + **external_script_request_id**: The process ID as received by SQL Server	
  + **language**: The keyword of a supported script language. Currently `R` is supported.
  + **degree_of_parallelism**: 	An integer indicating the number of parallel processes that were created. This might be different from the number of parallel processe that were requested. 
  + **external_user_name**: The SQL login or Windows user account under which the script was issued. If the
  

+ sys.dm_external_script_execution_stats (Transact-SQL)

  This DMV is provided for internal monitoring (telemetry) to track how many R calls are made on an instance. The telemetry service starts when SQL Server does and increments a disk-based counter each time a specific R function is called.

  The counter is incremented per call to a function. For example, if `rxLinMod` is called and run in parallel, the counter is incremented by 1.
  
  Generally speaking, performance counters are valid only as long as the process that generated them is active. Therefore, a query on a DMV cannot show detailed data for  services that have stopped running. For example, if the Launchpad creates multiple parallel R jobs and yet they are very quickly executed and then cleaned up by the Windows job object, a DMV might not show any data.
 
  However, the counters tracked by this DMV are kept running, and state for dm_external_script _execution counter is preserved by using writes to disk, even if the instance is shut down.
 
 For more information about system performance counters used by [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)], see [Use SQL Server Objects](../../Topics\TopicNameNotContainA/Use-SQL-Server-Objects.md).

**Resource Governor views**

+ [sys.resource_governor_resource_pools](sys.resource_governor_resource_pools%20\(Transact-SQL\).md)

  Returns information about the current resource pool state, the current configuration of resource pools, and resource pool statistics.

  > [!IMPORTANT]
  > 
  > You must modify resource pools that apply to other server services before you can allocate additional resources to R Services.


+ [sys.resource_governor_external_resource_pools](sys.resource_governor_external_resource_pools%20\(Transact-SQL\).md)

  A new catalog view that shows the current configuration values for external resource pools.
  In Enterprise Edition, you can configure additional external resource pools: for example, you might decide to handle resources for R jobs running in SQL Server separately from those that originate from a remote client. 

  > [!NOTE]
  > 
  > In Standard Edition all R jobs are run in the same external default resource pool.

+ [sys.resource_governor_workload_groups](sys.resource_governor_workload_groups%20\(Transact-SQL\).md)

  Returns workload group statistics and the current configuration of the workload group. This view can be joined with sys.dm_resource_governor_resource_pools to get the resource pool name.
  For external scripts, a new column has been added that shows the id of the external pool associated with the workload group. 


+ [sys.dm_resource_governor_external_resource_pool_affinity](sys.dm_resource_governor_external_resource_pool_affinity%20\(Transact-SQL\).md)

  A new system catalog view that lets you see the processors and resources that are affinitized to a particular resource pool.

  Returns one row per scheduler in SQL Server where each scheduler is mapped to an individual processor. Use this view to monitor the condition of a scheduler or to identify runaway tasks.

  Under the default configuration, workload pools are automatically assigned to processors and therefore there are no affinity values to return.

  The affinity schedule maps the resource pool to the SQL Server schedules identified by the given IDs. These IDs map to the values in the scheduler_id column in sys.dm_os_schedulers (Transact-SQL).


> [!NOTE] 
> 
> Although the ability to configure and customize resource pools is available only in Enterprise and Developer editions, the default pools, as well as the DMVs, are available in all editions. Therefore, you can use these DMVs in Standard Edition to determine resource caps for your R jobs. 

For general information about monitoring SQL Server instances, see [Catalog Views](Catalog%20Views%20\(Transact-SQL\).md) and [Resource Governor Related Dynamic Management Views](Resource%20Governor%20Related%20Dynamic%20Management%20Views%20\(Transact-SQL\).md).

## R Script Execution and Monitoring

R scripts that run in [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)] are started by the [!INCLUDE[rsql_launchpad_md](../../Token\Other/rsql_launchpad_md.md)] interface. However, the Launchpad is not resource governed or monitored separately, as it is assumed to be a secure service provided by Microsoft that manages resources appropriately.

Individual R scripts that run under the Launchpad service are managed using the 
[Windows job object](https://msdn.microsoft.com/library/windows/desktop/ms684161.aspx).

A job object allows groups of processes to be managed as a unit. Each job object is hierarchical and control the attributes of all processes associated with it. Operations performed on a job object affect all processes associated with the job object. 

Thus, if you need to terminate one job associated with an object, all related processes will also be terminated. If you are running an R script that is assigned to a Windows job object and that script requires a related ODBC job that must be terminated, the parent process will be terminated as well. 

If you start an R script that uses parallel processing, a single Windows job object is created that manages the parallel child processes.

To determine if a process is running in a job, use the IsProcessInJob function.

## See Also
[Managing and Monitoring](../../Topics\TopicNameNotContainA/Managing-and-Monitoring-R-Solutions.md)

