---
title: Database States
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b7f1f111-ca73-4a89-b567-a98d64d6ecb3
---
# Database States
  A database is always in one specific state. For example, these states include ONLINE, OFFLINE, or SUSPECT. To verify the current state of a database, select the **state\_desc** column in the [sys.databases](../Topic/sys.databases%20\(Transact-SQL\).md) catalog view or the **Status** property in the [DATABASEPROPERTYEX](../Topic/DATABASEPROPERTYEX%20\(Transact-SQL\).md) function.  
  
## Database State Definitions  
 The following table defines the database states.  
  
|State|Definition|  
|-----------|----------------|  
|ONLINE|Database is available for access. The primary filegroup is online, although the undo phase of recovery may not have been completed.|  
|OFFLINE|Database is unavailable. A database becomes offline by explicit user action and remains offline until additional user action is taken. For example, the database may be taken offline in order to move a file to a new disk. The database is then brought back online after the move has been completed.|  
|RESTORING|One or more files of the primary filegroup are being restored, or one or more secondary files are being restored offline. The database is unavailable.|  
|RECOVERING|Database is being recovered. The recovering process is a transient state; the database will automatically become online if the recovery succeeds. If the recovery fails, the database will become suspect. The database is unavailable.|  
|RECOVERY PENDING|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] has encountered a resource\-related error during recovery. The database is not damaged, but files may be missing or system resource limitations may be preventing it from starting. The database is unavailable. Additional action by the user is required to resolve the error and let the recovery process be completed.|  
|SUSPECT|At least the primary filegroup is suspect and may be damaged. The database cannot be recovered during startup of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. The database is unavailable. Additional action by the user is required to resolve the problem.|  
|EMERGENCY|User has changed the database and set the status to EMERGENCY. The database is in single\-user mode and may be repaired or restored. The database is marked READ\_ONLY, logging is disabled, and access is limited to members of the **sysadmin** fixed server role. EMERGENCY is primarily used for troubleshooting purposes. For example, a database marked as suspect can be set to the EMERGENCY state. This could permit the system administrator read\-only access to the database. Only members of the **sysadmin** fixed server role can set a database to the EMERGENCY state.|  
  
## Related Content  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20\(Transact-SQL\).md)  
  
 [Mirroring States &#40;SQL Server&#41;](../Topic/Mirroring%20States%20\(SQL%20Server\).md)  
  
 [File States](../../Topics\TopicNameNotContainA/File-States.md)  
  
  