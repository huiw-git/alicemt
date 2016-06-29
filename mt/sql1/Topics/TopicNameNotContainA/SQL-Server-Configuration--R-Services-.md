---
title: SQL Server Configuration (R Services)
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4b08969f-b90b-46b3-98e7-0bf7734833fc
---
# SQL Server Configuration (R Services)
## Machine Configuration for R Services and SQL Server

The information in this section provides general guidance on the hardware and network configuration of the machine that is used to host [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/includes/rsql_productname_md.md)]. It should be considered in addition to the general [!INCLUDE[ssNoVersion_md](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] performance tuning information provided in the [Performance Center for SQL Server Database Engine and Azure SQL Database](../../Topics/TopicNameNotContainA/Security-Center-for-SQL-Server-Database-Engine-and-Azure-SQL-Database.md).

## Processor

[!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/includes/rsql_productname_md.md)] can perform tasks in parallel by using the available cores on the machine; the more cores that are available, the better the performance. Since [!INCLUDE[ssNoVersion_md](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] is normally used by multiple users simultaneously, the database administrator should determine the ideal number of cores that are needed to support peak workload computations. While the number of cores may not help for IO bound operations, CPU bound algorithms will benefit from faster CPUs with many cores.

## Memory

The amount of memory available on the machine can have a large impact on the performance of advanced analytic algorithms. Insufficient memory may impact the degree of parallelism when using the SQL compute context, the chunk size (rows per read operation,) that can be processed, and the number of simultaneous sessions that can be supported.

A minimum of 32GB is highly recommended. If you have more than 32GB available, you can configure the SQL data source to use more rows per read operation to improve performance.

## Power Options

On the Windows operating system, the __High Performance__ power option should be used. Using a different power setting will result in decreased or inconsistent performance when using [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/includes/rsql_productname_md.md)].

## Disk IO

Training and prediction jobs using [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/includes/rsql_productname_md.md)] are inherently IO bound, and depend on the speed of the disk(s) that the database is stored on. Faster drives, such as solid state drives (SSD) may help. 

Disk IO is also affected by other applications accessing the disk. For example, read operations against a database by other clients. Disk IO performance can also be affected by the filesystem in use. For example, the block size used by the file system. If multiple drives are available, store the databases on a different drive than [!INCLUDE[ssNoVersion_md](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] so that requests for [!INCLUDE[ssNoVersion_md](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] are not hitting the same disk as requests for data stored in the database.

Disk IO can also greatly impact performance when running RevoScaleR analytic functions that use multiple iterations during training. For example, `rxLogit`, `rxDTree`, `rxDForest` and `rxBTrees` all use multiple iterations. When the data source is [!INCLUDE[ssNoVersion_md](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)], these algorithms use temporary files that are optimized to capture the data. These files are automatically cleaned up after the session completes. Having a high performance disk for read/write operations can significantly improve the overall elapsed time for these algorithms.

> [!NOTE]
> [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/includes/rsql_productname_md.md)] requires 8.3 filename support on Windows operating systems. You can use fsutil.exe to determine whether a drive supports 8.3 filenames, or to enable support if it does not. For more information on using fsutil.exe with 8.3 filenames, see [Fsutil 8dot3name](https://technet.microsoft.com/library/ff621566(v=ws.11).aspx).

### Table Compression

IO performance can often be improved by using either compression or columstore indexes. Generally, data is often repeated in several columns within a table, so using a columnstore index takes advantage of these repetitions when compressing the data.

A columnstore index may not be as efficient if there are a lot of insertions into the table, but is a good choice if the data is static or only changes infrequently. If a columnar store is not appropriate, enabling compression on a row major table can be used to improve IO.

For more information, see the following documents:

* [Data Compression](../../Topics/TopicNameNotContainA/Data-Compression.md)

* [Enable Compression on a Table or Index](../../Topics/TopicNameContainA/Enable-Compression-on-a-Table-or-Index.md)

* [Columnstore Indexes Guide](../../Topics/TopicNameNotContainA/Columnstore-Indexes-Guide.md)

## Paging File

The Windows operating system uses a paging file to manage crash dumps and for storing virtual memory pages. If you notice excessive paging, consider increasing the physical memory on the machine. While having more physical memory does not eliminate paging, it does reduce the need for paging.

The speed of the disk that the page file is stored on can also affect performance. Storing the page file on an SSD, or using multiple page files across multiple SSDs, can improve performance.

See [How to determine the appropriate page file size for 64-bit versions of Windows](https://support.microsoft.com/en-us/kb/2860880) for information on sizing the page file.

## Resource Governance

[!INCLUDE[ssNoVersion_md](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] supports resource governance for controlling the various resources used by [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/includes/rsql_productname_md.md)]. For example, the default value for memory consumption by R is limited to 20% of the total memory available for [!INCLUDE[ssNoVersion_md](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)]. This is done to ensure that [!INCLUDE[ssNoVersion_md](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] workflows are not severely affected by long running R jobs. However, these limits can be changed by the database administrator. 

The resources limited are __MAX_CPU_PERCENT__, __MAX_MEMORY_PERCENT__, and __MAX_PROCESSES__. The [!INCLUDE[tsql_md](../../Topics/TopicNameContainA/includes/tsql_md.md)] statement `select * from sys.resource_governor_external_resource_pools` can be used to view the current settings. If [!INCLUDE[ssNoVersion_md](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] is primarily used for R services, then it might be helpful to increase MAX_CPU_PERCENT to 40% or 60%. If there many R sessions using the same [!INCLUDE[ssNoVersion_md](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] at the same time, all three will should be increased. To change a value, the [!INCLUDE[tsql_md](../../Topics/TopicNameContainA/includes/tsql_md.md)] statement can be used. For example, `ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_MEMORY_PERCENT = 40)` sets the memory usage to 40%. The following is an example of setting all three at once: `ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_CPU_PERCENT = 40, MAX_MEMORY_PERCENT = 50, MAX_PROCESSES = 20)`. 

> [!NOTE]
> To make changes to these settings take effect immediately, use `ALTER RESOURCE GOVERNOR RECONFIGURE` command after changing a memory, CPU, or max process setting. 

For more information, see [Resource Governor](../../Topics/TopicNameNotContainA/Resource-Governor.md). Also see [CREATE EXTERNAL RESOURCE POOL](CREATE%20EXTERNAL%20RESOURCE%20POOL%20\(Transact-SQL\).md) for more information on creating and altering the pool used for external resources.