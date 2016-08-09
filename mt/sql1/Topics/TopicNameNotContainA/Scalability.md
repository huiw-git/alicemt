---
title: "Scalability"
ms.custom: na
ms.date: 2015-08-27
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a4891c57-56bb-49f4-9bb5-f11b745279e5
caps.latest.revision: 7
caps.handback.revision: 0
manager: jhubbard
---
# Scalability
SQL Server 2016 contains scalability enhancements to the on-disk storage for memory-optimized tables.  
  
-   **Multiple threads to persist memory-optimized tables**  
  
     In the previous release of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], there was a single offline checkpoint thread that scanned the transaction log for changes to memory-optimized tables and persisted them in checkpoint files (such as data and delta files). With larger number of COREs, the single offline checkpoint thread could fall behind.  
  
     In [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)], there are multiple concurrent threads responsible to persist changes to memory-optimized tables.  
  
-   **Multi-threaded recovery**  
  
     In the previous release of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], the log apply as part of recovery operation was single threaded. In [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)], the log apply is multi-threaded.  
  
-   **MERGE Operation**  
  
     The MERGE operation is now multi-threaded.  
  
-   **Dynamic management views**  
  
     [sys.dm_db_xtp_checkpoint_stats (Transact-SQL)](assetId:///8d0b18ca-db4d-4376-9905-3e4457727c46) and [sys.dm_db_xtp_checkpoint_files (Transact-SQL)](assetId:///ac8e6333-7a9f-478a-b446-5602283e81c9)have been changed significantly.  
  
 Manual Merge has been disabled as multi-threaded merge is expected to keep up with the load.  
  
 The In-memory OLTP engine continues to use memory-optimized filegroup based on FILESTREAM, but the individual files in the filegroup are decoupled from FILESTREAM. These files are fully managed (such as for create, drop, and garbage collection) by the In-Memory OLTP engine. [DBCC SHRINKFILE (Transact-SQL)](assetId:///e02b2318-bee9-4d84-a61f-2fddcf268c9f) is not supported.