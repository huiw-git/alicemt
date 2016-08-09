---
title: "Manually Fail Over a Database Mirroring Session (Transact-SQL)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 36218d61-b5f5-4194-905a-608e0e903db4
caps.latest.revision: 33
caps.handback.revision: 0
manager: jhubbard
---
# Manually Fail Over a Database Mirroring Session (Transact-SQL)
When the mirrored database is synchronized (that is, when the database is in the SYNCHRONIZED state), the database owner can initiate manual failover to the mirror server. Manual failover can be initiated only from the principal server.  
  
### To manually fail over a database mirroring session  
  
1.  Connect to the principal server.  
  
2.  Set the database context to the **master** database:  
  
     **USE master;**  
  
3.  Issue the following statement on the principal server:  
  
     [ALTER DATABASE](assetId:///27a032ef-1cf6-4959-8e67-03d28c4b3465) *database_name* SET PARTNER FAILOVER, where *database_name* is the mirrored database.  
  
     This initiates an immediate transition of the mirror server to the principal role.  
  
 On the former principal, clients are disconnected from the database and in-flight transactions are rolled back.  
  
> [!NOTE]  
>  Transactions that have been prepared by using the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Distributed Transaction Coordinator but are still not committed when a failover occurs are considered aborted after the database has failed over.  
  
## See Also  
 [ALTER DATABASE Database Mirroring (Transact-SQL)](assetId:///27a032ef-1cf6-4959-8e67-03d28c4b3465)   
 [Manually Fail Over a Database Mirroring Session (SQL Server Management Studio)](../../Topics/TopicNameContainA/Manually-Fail-Over-a-Database-Mirroring-Session--SQL-Server-Management-Studio-.md)   
 [Role Switching During a Database Mirroring Session (SQL Server)](../../Topics/TopicNameContainA/Role-Switching-During-a-Database-Mirroring-Session--SQL-Server-.md)