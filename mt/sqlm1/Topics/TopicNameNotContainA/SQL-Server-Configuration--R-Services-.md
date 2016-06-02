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

The information in this section provides general guidance on the hardware and network configuration of the machine that is used to host [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)]. It should be considered in addition to the general [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)] performance tuning information provided in the [Performance Center for SQL Server Database Engine and Azure SQL Database](../../Topics\TopicNameNotContainA/Security-Center-for-SQL-Server-Database-Engine-and-Azure-SQL-Database.md).

## Processor

[!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] can perform tasks in parallel by using the available cores on the machine; the more cores that are available, the better the performance. Since [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)] is normally used by multiple users simultaneously, the database administrator should determine the ideal number of cores that are needed to support peak workload computations. While the number of cores may not help for IO bound operations, CPU bound algorithms will benefit from faster CPUs with many cores.

## Memory

The amount of memory available on the machine can have a large impact on the performance of advanced analytic algorithms. Insufficient memory may impact the degree of parallelism when using the SQL compute context, the chunk size (rows per read operation,) that can be processed, and the number of simultaneous sessions that can be supported.

A minimum of 32GB is highly recommended. If you have more than 32GB available, you can configure the SQL data source to use more rows per read operation to improve performance.

## Power Options

On the Windows operating system, the __High Performance__ power option should be used. Using a different power setting will result in decreased or inconsistent performance when using [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)].

## Disk

Training and prediction jobs using [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] are inherently IO bound, and depend on the speed of the disk(s) that the database is stored on. Faster drives, such as solid state drives (SSD) may help; however, disk IO is also affected by other applications accessing the disk. For example, read operations against a database by other clients. Disk IO performance can also be affected by the filesystem in use. For example, the block size used by the file system.

### IO

The database should be stored on a fast storage media such as an SSD. If multiple drives are available, store the databases on a different drive than [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)].

> [!NOTE]
> [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] requires 8.3 filename support on Windows operating systems. You can use fsutil.exe to determine whether a drive supports 8.3 filenames, or to enable support if it does not. For more information on using fsutil.exe with 8.3 filenames, see [Fsutil 8dot3name](https://technet.microsoft.com/library/ff621566(v=ws.11).aspx).

Disk IO can also greatly impact performance when running RevoScaleR analytic functions that use multiple iterations during training. For example, `rxLogit`, `rxDTree`, `rxDForest` and `rxBTrees` all use multiple iterations. When the data source is [!INCLUDE[ssNoVersion_md](../../Token\Other/ssNoVersion_md.md)], these algorithms use temporary files that are optimized to capture the data. These files are automatically cleaned up after the session completes. Having a high performance disk for read/write operations can significantly improve the overall elapsed time for these algorithms.

## Paging File

The Windows operating system uses a paging file to manage crash dumps and for storing virtual memory pages. If you notice excessive paging, consider increasing the physical memory on the machine. While having more physical memory does not eliminate paging, it does reduce the need for paging.

The speed of the disk that the page file is stored on can also affect performance. Storing the page file on an SSD, or using multiple page files across multiple SSDs, can improve performance.

See [How to determine the appropriate page file size for 64-bit versions of Windows](https://support.microsoft.com/en-us/kb/2860880) for information on sizing the page file.