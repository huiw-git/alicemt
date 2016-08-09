---
title: "Move Database Files"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 89f01b10-5fae-4ed8-b0fb-a4b9f540fd28
caps.latest.revision: 35
caps.handback.revision: 0
manager: jhubbard
---
# Move Database Files
In [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], you can move system and user databases by specifying the new file location in the FILENAME clause of the [ALTER DATABASE](assetId:///15f8affd-8f39-4021-b092-0379fc6983da) statement. Data, log, and full-text catalog files can be moved in this way. This may be useful in the following situations:  
  
-   Failure recovery. For example, the database is in suspect mode or has shut down, because of a hardware failure.  
  
-   Planned relocation.  
  
-   Relocation for scheduled disk maintenance.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Move User Databases](../../Topics/TopicNameNotContainA/Move-User-Databases.md)|Describes the procedures for moving user database files and full-text catalog files to a new location.|  
|[Move System Databases](../../Topics/TopicNameNotContainA/Move-System-Databases.md)|Describes the procedures for moving system database files to a new location.|  
  
## See Also  
 [ALTER DATABASE (Transact-SQL)](assetId:///15f8affd-8f39-4021-b092-0379fc6983da)   
 [CREATE DATABASE (Transact-SQL)](assetId:///29ddac46-7a0f-4151-bd94-75c1908c89f8)   
 [Database Detach and Attach (SQL Server)](../../Topics/TopicNameNotContainA/Database-Detach-and-Attach--SQL-Server-.md)