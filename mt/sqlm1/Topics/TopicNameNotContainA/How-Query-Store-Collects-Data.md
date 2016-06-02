---
title: How Query Store Collects Data
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8d5eec36-0013-480a-9c11-183e162e4c8e
---
# How Query Store Collects Data
  Query Store works as a **flight data recorder** constantly collecting compile and runtime information related to the queries and plans. Query related data is persisted in the internal tables and presented to users through a set of views.  
  
## Views  
 The following diagram shows Query Store views and their logical relationships, with compile time information presented as blue entities:  
  
 ![query-store-process-1views](../../Images\Image\ImageNotContaina/query-store-process-1views.png "query-store-process-1views")  
  
 **View Descriptions**  
  
|View|Description|  
|----------|-----------------|  
|**sys.query\_store\_query\_text**|Presents unique query texts executed against the database. Comments and spaces before and after the query text are ignored. Comments and spaces inside text are not ignored. Every statement in the batch generates a separate query text entry.|  
|**sys.query\_context\_settings**|Presents unique combinations of plan affecting settings under which queries are executed. The same query text executed with different plan affecting settings produces separate query entry in the Query Store because `context_settings_id` is part of the query key.|  
|**sys.query\_store\_query**|Query entries that are tracked and forced separately in the Query Store. A single query text can produce multiple query entries if it is executed under different context settings or if it is executed outside vs. inside of different [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] modules \(stored procedures, triggers, etc.\).|  
|**sys.query\_store\_plan**|Presents estimated plan for the query with the compile time statistics. Stored plan is equivalent to one that you would get by using `SET SHOWPLAN_XML ON`.|  
|**sys.query\_store\_runtime\_stats\_interval**|Query Store divides time into automatically generated time windows \(intervals\) and stores aggregated statistics on that interval for every executed plan. The size of the interval is controlled by the configuration option Statistics Collection Interval \(in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)]\) or `INTERVAL_LENGTH_MINUTES` using [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md).|  
|**sys.query\_store\_runtime\_stats**|Aggregated runtime statistics for executed plans. All captured metrics are expressed in form of 4 statistic functions: Average, Minimum, Maximum, and Standard Deviation.|  
  
 For additional details on Query Store views, see the **Related Views, Functions, and Procedures** section of [Monitoring Performance By Using the Query Store](https://msdn.microsoft.com/library/dn817826.aspx).  
  
## Query Processing  
 Query store interacts with the query processing pipeline at the following key points:  
  
1.  When query gets compiled for the first time, query text and initial plan are sent to Query Store  
  
2.  When query gets recompiled, the plan is being updated in the Query Store. If a new plan is created, Query Store adds the new plan entry for the query, keeping the previous ones along with their execution statistics.  
  
3.  Upon the query execution, runtime statistics are sent to the Query Store. Query Store keeps aggregated statistics accurate for every plan that was executed within the currently active interval.  
  
4.  During the compile and check for recompile phases, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] determines if there is a plan in the Query Store that should be applied for the currently running query. If there is a forced plan and the plan in the procedure cache is different than the forced plan, the query gets recompiled, effectively the same way as if PLAN HINT was applied to that query. This process happens transparently to the user application.  
  
 The following diagram depicts points of integration explained above:  
  
 ![query-store-process-2processor](../../Images\Image\ImageNotContaina/query-store-process-2processor.png "query-store-process-2processor")  
  
 To minimize I\/O overhead, new data is captured in\-memory. Writes operations are queued and flushed to disk afterwards. Query and plan information \(Plan Store on diagram below\) are flushed with minimal latency while runtime statistics \(Runtime Stats\) are kept in memory for a period of time defined with Data Flush Interval \(Minutes\) in SSMS UI or `DATA_FLUSH_INTERVAL_SECONDS` \(Transact\-SQL\).  
  
 ![query-store-process-3plan](../../Images\Image\ImageNotContaina/query-store-process-3.png "query-store-process-3")  
  
 In case of a system crash, Query Store can lose runtime data up to amount defined with `DATA_FLUSH_INTERVAL_SECONDS`. The default value of 900 seconds \(15 minutes\) is an optimal balance between query capture performance and data availability.  
In case of memory pressure, runtime statistics can be flushed to disk earlier than defined with `DATA_FLUSH_INTERVAL_SECONDS`.  
During the read of the Query Store data in\-memory and on\-disk data are unified transparently.  
  
 ![query-store-process-4planinfo](../../Images\Image\ImageNotContaina/query-store-process-4planinfo.png "query-store-process-4planinfo")  
  
 Although in\-memory structures eliminate latency during the data capture, configuring large value for `DATA_FLUSH_INTERVAL_SECONDS` will significantly reduce performance of querying the Query Store views.  
  
## See Also  
 [Monitoring Performance By Using the Query Store](../../Topics\TopicNameNotContainA/Monitoring-Performance-By-Using-the-Query-Store.md)   
 [Best Practice with the Query Store](../../Topics\TopicNameNotContainA/Best-Practice-with-the-Query-Store.md)   
 [Query Store Catalog Views &#40;Transact-SQL&#41;](../Topic/Query%20Store%20Catalog%20Views%20\(Transact-SQL\).md)  
  
  