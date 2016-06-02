---
title: SQL Server, Buffer Manager Object
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9775ebde-111d-476c-9188-b77805f90e98
---
# SQL Server, Buffer Manager Object
  The **Buffer Manager** object provides counters to monitor how [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] uses:  
  
-   Memory to store data pages.  
  
-   Counters to monitor the physical I\/O as [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] reads and writes database pages.  
  
-   Buffer pool extension to extend the buffer cache by using fast non\-volatile storage such as solid\-state drives \(SSD\).  
  
 Monitoring the memory and the counters used by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] helps you determine:  
  
-   If bottlenecks exist from inadequate physical memory. If it cannot store frequently accessed data in cache, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] must retrieve the data from disk.  
  
-   If query performance can be improved by adding more memory, or by making more memory available to the data cache or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] internal structures.  
  
-   How often [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] needs to read data from disk. Compared with other operations, such as memory access, physical I\/O consumes a lot of time. Minimizing physical I\/O can improve query performance.  
  
## Buffer Manager Performance Objects  
 This table describes the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] **Buffer Manager** performance objects.  
  
|SQL Server Buffer Manager counters|Description|  
|----------------------------------------|-----------------|  
|**Buffer cache hit ratio**|Indicates the percentage of pages found in the buffer cache without having to read from disk. The ratio is the total number of cache hits divided by the total number of cache lookups over the last few thousand page accesses. After a long period of time, the ratio moves very little. Because reading from the cache is much less expensive than reading from disk, you want this ratio to be high. Generally, you can increase the buffer cache hit ratio by increasing the amount of memory available to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or by using the buffer pool extension feature.|  
|**Checkpoint pages\/sec**|Indicates the number of pages flushed to disk per second by a checkpoint or other operation that require all dirty pages to be flushed.|  
|**Database pages**|Indicates the number of pages in the buffer pool with database content.|  
|**Extension allocated pages**|Total number of non\-free cache pages in the buffer pool extension file.|  
|**Extension free pages**|Total number of free cache pages in the buffer pool extension file.|  
|**Extension in use as percentage**|Percentage of the buffer pool extension paging file occupied by buffer manager pages.|  
|**Extension outstanding IO counter**|I\/O queue length for the buffer pool extension file.|  
|**Extension page evictions\/sec**|Number of pages evicted from the buffer pool extension file per second.|  
|**Extension page reads\/sec**|Number of pages read from the buffer pool extension file per second.|  
|**Extension page unreferenced time**|Average seconds a page will stay in the buffer pool extension without references to it.|  
|**Extension pages writes\/sec**|Number of pages written to the buffer pool extension file per second.|  
|**Free list stalls\/sec**|Indicates the number of requests per second that had to wait for a free page.|  
|**Lazy writes\/sec**|Indicates the number of buffers written per second by the buffer manager's lazy writer. The *lazy writer* is a system process that flushes out batches of dirty, aged buffers \(buffers that contain changes that must be written back to disk before the buffer can be reused for a different page\) and makes them available to user processes. The lazy writer eliminates the need to perform frequent checkpoints in order to create available buffers.|  
|**Page life expectancy**|Indicates the number of seconds a page will stay in the buffer pool without references.|  
|**Page lookups\/sec**|Indicates the number of requests per second to find a page in the buffer pool.|  
|**Page reads\/sec**|Indicates the number of physical database page reads that are issued per second. This statistic displays the total number of physical page reads across all databases. Because physical I\/O is expensive, you may be able to minimize the cost, either by using a larger data cache, intelligent indexes, and more efficient queries, or by changing the database design.|  
|**Page writes\/sec**|Indicates the number of physical database page writes that are issued per second.|  
|**Readahead pages\/sec**|Indicates the number of pages read per second in anticipation of use.|  
  
## See Also  
 [SQL Server:Buffer Node](../Topic/SQL%20Server:Buffer%20Node.md)   
 [Server Memory Server Configuration Options](../../Topics\TopicNameNotContainA/Server-Memory-Server-Configuration-Options.md)   
 [SQL Server, Plan Cache Object](../../Topics\TopicNameNotContainA/SQL-Server,-Plan-Cache-Object.md)   
 [Monitor Resource Usage &#40;System Monitor&#41;](../Topic/Monitor%20Resource%20Usage%20\(System%20Monitor\).md)   
 [sys.dm_os_performance_counters &#40;Transact-SQL&#41;](../Topic/sys.dm_os_performance_counters%20\(Transact-SQL\).md)   
 [Buffer Pool Extension](../../Topics\TopicNameNotContainA/Buffer-Pool-Extension.md)  
  
  