---
title: Restore a Database and Bind it to a Resource Pool
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0d20a569-8a27-409c-bcab-0effefb48013
---
# Restore a Database and Bind it to a Resource Pool
  Even though you have enough memory to restore a database with memory\-optimized tables, you want to follow best practices and bind the database to a named resource pool. Since the database must exist before you can bind it to the pool restoring your database is a multi\-step process. This topic walks you through that process.  
  
## Restoring a database with memory\-optimized tables  
 The following steps fully restore the database IMOLTP\_DB and bind it to the Pool\_IMOLTP.  
  
1.  [Restore with NORECOVERY](../../Topics\TopicNameContainA/Restore-a-Database-and-Bind-it-to-a-Resource-Pool.md)  
  
2.  [Create the resource pool](../../Topics\TopicNameContainA/Restore-a-Database-and-Bind-it-to-a-Resource-Pool.md)  
  
3.  [Bind the database and resource pool](../../Topics\TopicNameContainA/Restore-a-Database-and-Bind-it-to-a-Resource-Pool.md)  
  
4.  [Restore with RECOVERY](../../Topics\TopicNameContainA/Restore-a-Database-and-Bind-it-to-a-Resource-Pool.md)  
  
5.  [Monitor the resource pool performance](../../Topics\TopicNameContainA/Restore-a-Database-and-Bind-it-to-a-Resource-Pool.md)  
  
###  <a name="bkmk_NORECOVERY"></a> Restore with NORECOVERY  
 When you restore a database, NORECOVERY causes the database to be created and the disk image restored without consuming memory.  
  
```tsql  
RESTORE DATABASE IMOLTP_DB   
   FROM DISK = 'C:\IMOLTP_test\IMOLTP_DB.bak'  
   WITH NORECOVERY  
```  
  
###  <a name="bkmk_createPool"></a> Create the resource pool  
 The following [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] creates a resource pool named Pool\_IMOLTP with 50% of memory available for its use.  After the pool is created, the Resource Governor is reconfigured to include Pool\_IMOLTP.  
  
```tsql  
CREATE RESOURCE POOL Pool_IMOLTP WITH (MAX_MEMORY_PERCENT = 50);  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
###  <a name="bkmk_bind"></a> Bind the database and resource pool  
 Use the system function `sp_xtp_bind_db_resource_pool` to bind the database to the resource pool. The function takes two parameters: the database name followed by the resource pool name.  
  
 The following [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] defines a binding of the database IMOLTP\_DB to the resource pool Pool\_IMOLTP. The binding does not become effective until you complete the next step.  
  
```tsql  
EXEC sp_xtp_bind_db_resource_pool 'IMOLTP_DB', 'Pool_IMOLTP'  
GO  
```  
  
###  <a name="bkmk_RECOVERY"></a> Restore with RECOVERY  
 When you restore the database with recovery the database is brought online and all the data restored.  
  
```tsql  
RESTORE DATABASE IMOLTP_DB   
   WITH RECOVERY  
```  
  
###  <a name="bkmk_Monitor"></a> Monitor the resource pool performance  
 Once the database is bound to the named resource pool and restored with recovery, monitor the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], Resource Pool Stats Object. For more information see [SQL Server, Resource Pool Stats Object](../../Topics\TopicNameNotContainA/SQL-Server,-Resource-Pool-Stats-Object.md).  
  
## See Also  
 [Bind a Database with Memory-Optimized Tables to a Resource Pool](../../Topics\TopicNameContainA/Bind-a-Database-with-Memory-Optimized-Tables-to-a-Resource-Pool.md)   
 [sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](../Topic/sys.sp_xtp_bind_db_resource_pool%20\(Transact-SQL\).md)   
 [SQL Server, Resource Pool Stats Object](../../Topics\TopicNameNotContainA/SQL-Server,-Resource-Pool-Stats-Object.md)   
 [sys.dm\_resource\_governor\_resource\_pools](../Topic/sys.sp_xtp_unbind_db_resource_pool%20\(Transact-SQL\).md)  
  
  