---
title: "Database Properties (Query Store Page)"
ms.custom: na
ms.date: 2015-11-09
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: da47d75e-291a-4305-acef-4b0aaf5215da
caps.latest.revision: 11
caps.handback.revision: 0
manager: jhubbard
---
# Database Properties (Query Store Page)
Access this page from the principal database, and use it to configure and to modify the properties of the database query store. These options can also be configure by using the [ALTER DATABASE SET options](assetId:///f76fbd84-df59-4404-806b-8ecb4497c9cc). For information about the query store, see [Monitoring Performance By Using the Query Store](../../Topics/TopicNameNotContainA/Monitoring-Performance-By-Using-the-Query-Store.md).  
  
||  
|-|  
|**Applies to**: [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] ([!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)] through [current version](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[sqldbesa](../../Topics/TopicNameNotContainA/tokens/sqldbesa_md.md)].|  
  
## Options  
 Operation Mode  
 Valid values are OFF, READ_ONLY, and READ_WRITE. OFF disables the Query Store. In READ_WRITE mode, the query store collects and persists query plan and runtime execution statistics information. In READ_ONLY mode, information can be read from the query store, but new information is not added. If the maximum allocated space of the query store has been exhausted, the query store will change its operation mode to READ_ONLY.  
  
 Operation Mode (Actual)  
 Gets the actual operation mode of the query store.  
  
 Operation Mode (Requested)  
 Gets and sets the desired operation mode of the query store.  
  
 Data Flush Interval (Minutes)  
 Determines the frequency at which data written to the query store is persisted to disk. To optimize for performance, data collected by the query store is asynchronously written to the disk. The frequency at which this asynchronous transfer occurs is configured.  
  
 Statistics Collection Interval  
 Gets and sets the statistics collection interval value.  
  
 Max Size (MB)  
 Gets and sets the total space allocated to the query store.  
  
 Query Store Capture Mode  
 -   None does not capture new queries.  
  
-   All captures all queries.  
  
-   Auto captures queries based on resource consumption.  
  
 Stale Query Threshold (Days)  
 Gets and sets the stale query threshold. Configure the STALE_QUERY_THRESHOLD_DAYS argument to specify the number of days to retain data in the query store.  
  
 Purge Query Data  
 Removes the contents of the query store.  
  
 Pie Charts  
 The left chart shows the total database file consumption on the disk, and the portion of the file which is filled with the query store data.  
  
 The right chart shows the portion of the query store quota which is currently used up. Note that the quota is not shown in the left chart. The quota may exceed the current size of the database.  
  
## Remarks  
 The query store feature provides DBAs with insight on query plan choice and performance. It simplifies performance troubleshooting by enabling you to quickly find performance differences caused by changes in query plans. The feature automatically captures a history of queries, plans, and runtime statistics, and retains these for your review. It separates data by time windows, allowing you to see database usage patterns and understand when query plan changes happened on the server. The query store can be configured by using this query store database property page, or by using the [ALTER DATABASE SET](assetId:///f76fbd84-df59-4404-806b-8ecb4497c9cc) option. The query store presents information by using a [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/tokens/ssManStudio_md.md)] dialog box. For more information about query store, see [Monitoring Performance By Using the Query Store](../../Topics/TopicNameNotContainA/Monitoring-Performance-By-Using-the-Query-Store.md).  
  
## See Also  
 [Query Store Stored Procedures (Transact-SQL)](assetId:///9bddbb74-e67a-43e3-b89e-896c498e53cb)   
 [Query Store Catalog Views](assetId:///43d5466a-89e2-4e59-b87e-a2a78e59a1de)