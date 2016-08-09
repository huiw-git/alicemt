---
title: "Database States"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b7f1f111-ca73-4a89-b567-a98d64d6ecb3
caps.latest.revision: 21
caps.handback.revision: 0
manager: jhubbard
---
# Database States
A database is always in one specific state. For example, these states include ONLINE, OFFLINE, or SUSPECT. To verify the current state of a database, select the **state_desc** column in the [sys.databases](assetId:///46c288c1-3410-4d68-a027-3bbf33239289) catalog view or the **Status** property in the [DATABASEPROPERTYEX](assetId:///8a9e0ffb-28b5-4640-95b2-a54e3e5ad941) function.  
  
## Database State Definitions  
 The following table defines the database states.  
  
|State|Definition|  
|-----------|----------------|  
|ONLINE|Database is available for access. The primary filegroup is online, although the undo phase of recovery may not have been completed.|  
|OFFLINE|Database is unavailable. A database becomes offline by explicit user action and remains offline until additional user action is taken. For example, the database may be taken offline in order to move a file to a new disk. The database is then brought back online after the move has been completed.|  
|RESTORING|One or more files of the primary filegroup are being restored, or one or more secondary files are being restored offline. The database is unavailable.|  
|RECOVERING|Database is being recovered. The recovering process is a transient state; the database will automatically become online if the recovery succeeds. If the recovery fails, the database will become suspect. The database is unavailable.|  
|RECOVERY PENDING|[!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] has encountered a resource-related error during recovery. The database is not damaged, but files may be missing or system resource limitations may be preventing it from starting. The database is unavailable. Additional action by the user is required to resolve the error and let the recovery process be completed.|  
|SUSPECT|At least the primary filegroup is suspect and may be damaged. The database cannot be recovered during startup of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. The database is unavailable. Additional action by the user is required to resolve the problem.|  
|EMERGENCY|User has changed the database and set the status to EMERGENCY. The database is in single-user mode and may be repaired or restored. The database is marked READ_ONLY, logging is disabled, and access is limited to members of the **sysadmin** fixed server role. EMERGENCY is primarily used for troubleshooting purposes. For example, a database marked as suspect can be set to the EMERGENCY state. This could permit the system administrator read-only access to the database. Only members of the **sysadmin** fixed server role can set a database to the EMERGENCY state.|  
  
## Related Content  
 [ALTER DATABASE (Transact-SQL)](assetId:///15f8affd-8f39-4021-b092-0379fc6983da)  
  
 [Mirroring States (SQL Server)](../../Topics/TopicNameNotContainA/Mirroring-States--SQL-Server-.md)  
  
 [File States](../../Topics/TopicNameNotContainA/File-States.md)