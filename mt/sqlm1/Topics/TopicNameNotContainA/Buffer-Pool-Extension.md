---
title: Buffer Pool Extension
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 909ab7d2-2b29-46f5-aea1-280a5f8fedb4
---
# Buffer Pool Extension
  Introduced in [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)], the buffer pool extension provides the seamless integration of a nonvolatile random access memory \(that is, solid\-state drive\) extension to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] buffer pool to significantly improve I\/O throughput. The buffer pool extension is not available in every [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] edition. For more information, see [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md).  
  
## Benefits of the Buffer Pool Extension  
 The primary purpose of a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database is to store and retrieve data, so intensive disk I\/O is a core characteristic of the Database Engine. Because disk I\/O operations can consume many resources and take a relatively long time to finish, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] focuses on making I\/O highly efficient. The buffer pool serves as a primary memory allocation source of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Buffer management is a key component in achieving this efficiency. The buffer management component consists of two mechanisms: the buffer manager to access and update database pages, and the buffer pool\), to reduce database file I\/O.  
  
 Data and index pages are read from disk into the buffer pool and modified pages \(also known as dirty pages\) are written back to disk. Memory pressure on the server and database checkpoints cause hot \(active\) dirty pages in the buffer cache to be evicted from the cache and written to mechanical disks and then read back into the cache. These I\/O operations are typically small random reads and writes on the order of 4 to 16 KB of data. Small random I\/O patterns incur frequent seeks, competing for the mechanical disk arm, increasing I\/O latency, and reducing aggregate I\/O throughput of the system.  
  
 The typical approach to resolving these I\/O bottlenecks is to add more DRAM, or alternatively, added high\-performance SAS spindles. While these options are helpful, they have significant drawbacks: DRAM is more expensive than data storage drives and adding spindles increases capital expenditure in hardware acquisition and increases operational costs by increased power consumption and increased probability of component failure.  
  
 The buffer pool extension feature extends the buffer pool cache with nonvolatile storage \(usually SSD\). Because of this extension, the buffer pool can accommodate a larger database working set, which forces the paging of I\/Os between RAM and the SSDs. This effectively offloads small random I\/Os from mechanical disks to SSDs. Because of the lower latency and better random I\/O performance of SSDs, the buffer pool extension significantly improves I\/O throughput.  
  
 The following list describes the benefits of the buffer pool extension feature.  
  
-   Increased random I\/O throughput  
  
-   Reduced I\/O latency  
  
-   Increased transaction throughput  
  
-   Improved read performance with a larger hybrid buffer pool  
  
-   A caching architecture that can take advantage of present and future low\-cost memory drives  
  
### Concepts  
 The following terms are applicable to the buffer pool extension feature.  
  
 Solid\-state drive \(SSD\)  
 Solid\-state drives store data in memory \(RAM\) in a persistent manner. For more information, see [this definition](http://en.wikipedia.org/wiki/Solid-state_drive).  
  
 Buffer  
 In [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], A buffer is an 8\-KB page in memory, the same size as a data or index page. Thus, the buffer cache is divided into 8\-KB pages. A page remains in the buffer cache until the buffer manager needs the buffer area to read in more data. Data is written back to disk only if it is modified. These in\-memory modified pages are known as dirty pages. A page is clean when it is equivalent to its database image on disk. Data in the buffer cache can be modified multiple times before being written back to disk.  
  
 Buffer pool  
 Also called buffer cache. The buffer pool is a global resource shared by all databases for their cached data pages. The maximum and minimum size of the buffer pool cache is determined during startup or when the instance of SQL server is dynamically reconfigured by using sp\_configure. This size determines the maximum number of pages that can be cached in the buffer pool at any time in the running instance.  
  
 The maximum memory that can be comitted by Buffer Pool Extension can be limited by the other applications running on the machine in case those create significant memory pressure.  
  
 Checkpoint  
 A checkpoint creates a known good point from which the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] can start applying changes contained in the transaction log during recovery after an unexpected shutdown or crash. A checkpoint writes the dirty pages and transaction log information from memory to disk and, also, records information about the transaction log. For more information, see [Database Checkpoints &#40;SQL Server&#41;](../Topic/Database%20Checkpoints%20\(SQL%20Server\).md).  
  
## Buffer Pool Extension Details  
 SSD storage is used as an extension to the memory subsystem rather than the disk storage subsystem. That is, the buffer pool extension file allows the buffer pool manager to use both DRAM and NAND\-Flash memory to maintain a much larger buffer pool of lukewarm pages in nonvolatile random access memory backed by SSDs. This creates a multilevel caching hierarchy with level 1 \(L1\) as the DRAM and level 2 \(L2\) as the buffer pool extension file on the SSD. Only clean pages are written to the L2 cache, which helps maintain data safety. The buffer manager handles the movement of clean pages between the L1 and L2 caches.  
  
 The following illustration provides a high\-level architectural overview of the buffer pool relative to other [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] components.  
  
 ![SSD Buffer Pool Extension Architecture](../../Images\Image\ImageNotContaina/SSDBufferPoolExtensionArchitecture.gif "SSDBufferPoolExtensionArchitecture")  
  
 When enabled, the buffer pool extension specifies the size and file path of the buffer pool caching file on the SSD. This file is a contiguous extent of storage on the SSD and is statically configured during startup of the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Alterations to the file configuration parameters can only be done when the buffer pool extension feature is disabled. When the buffer pool extension is disabled, all related configuration settings are removed from the registry. The buffer pool extension file is deleted upon shutdown of the instance of SQL Server.  
  
## Best Practices  
 We recommend that you follow these best practices.  
  
-   After enabling Buffer Pool Extension for the first time it is recommended to restart the SQL Server instance to get the maximum performance benefits.  
  
-   The buffer pool extension size can be up to 32 times the value of max\_server\_memory.  We recommend a ratio between the size of the physical memory \(max\_server\_memory\) and the size of the buffer pool extension of 1:16 or less. A lower ratio in the range of 1:4 to 1:8 may be optimal. For information about setting the max\_server\_memory option, see [Server Memory Server Configuration Options](../../Topics\TopicNameNotContainA/Server-Memory-Server-Configuration-Options.md).  
  
-   Test the buffer pool extension thoroughly before implementing in a production environment. Once in production, avoid making configuration changes to the file or turning the feature off. These activities may have a negative impact on server performance because the buffer pool is significantly reduced in size when the feature is disabled. When disabled, the memory used to support the feature is not reclaimed until the instance of SQL Server is restarted. However, if the feature is re\-enabled, the memory will be reused without restarting the instance.  
  
## Return Information about the Buffer Pool Extension  
 You can use the following dynamic management views to display the configuration of the buffer pool extension and return information about the data pages in the extension.  
  
-   [sys.dm_os_buffer_pool_extension_configuration &#40;Transact-SQL&#41;](../Topic/sys.dm_os_buffer_pool_extension_configuration%20\(Transact-SQL\).md)  
  
-   [sys.dm_os_buffer_descriptors &#40;Transact-SQL&#41;](../Topic/sys.dm_os_buffer_descriptors%20\(Transact-SQL\).md)  
  
 Performance counters are available in the SQL Server, Buffer Manager Object to track the data pages in the buffer pool extension file. For more information, see [buffer pool extension performance counters](../../Topics\TopicNameNotContainA/SQL-Server,-Buffer-Manager-Object.md).  
  
 The following Xevents are available.  
  
|XEvent|Description|Parameters|  
|------------|-----------------|----------------|  
|sqlserver.buffer\_pool\_extension\_pages\_written|Fires when a page or group of pages are evicted from the buffer pool and written to the buffer pool extension file.|*number\_page*<br /><br /> *first\_page\_id*<br /><br /> *first\_page\_offset*<br /><br /> *initiator\_numa\_node\_id*|  
|sqlserver.buffer\_pool\_extension\_pages\_read|Fires when a page is read from the buffer pool extension file to the buffer pool.|*number\_page*<br /><br /> *first\_page\_id*<br /><br /> *first\_page\_offset*<br /><br /> *initiator\_numa\_node\_id*|  
|sqlserver.buffer\_pool\_extension\_pages\_evicted|Fires when a page is evicted from the buffer pool extension file.|*number\_page*<br /><br /> *first\_page\_id*<br /><br /> *first\_page\_offset*<br /><br /> *initiator\_numa\_node\_id*|  
|sqlserver.buffer\_pool\_eviction\_thresholds\_recalculated|Fires when the eviction threshold is calculated.|*warm\_threshold*<br /><br /> *cold\_threshold*<br /><br /> *pages\_bypassed\_eviction*<br /><br /> *eviction\_bypass\_reason*<br /><br /> *eviction\_bypass\_reason\_description*|  
  
## Related Tasks  
  
|||  
|-|-|  
|**Task Description**|**Topic**|  
|Enable and configure the buffer pool extension.|[ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../Topic/ALTER%20SERVER%20CONFIGURATION%20\(Transact-SQL\).md)|  
|Modify the buffer pool extension configuration|[ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../Topic/ALTER%20SERVER%20CONFIGURATION%20\(Transact-SQL\).md)|  
|View the buffer pool extension configuration|[sys.dm_os_buffer_pool_extension_configuration &#40;Transact-SQL&#41;](../Topic/sys.dm_os_buffer_pool_extension_configuration%20\(Transact-SQL\).md)|  
|Monitor the buffer pool extension|[sys.dm_os_buffer_descriptors &#40;Transact-SQL&#41;](../Topic/sys.dm_os_buffer_descriptors%20\(Transact-SQL\).md)<br /><br /> [Performance counters](../../Topics\TopicNameNotContainA/SQL-Server,-Buffer-Manager-Object.md)|  
  
  