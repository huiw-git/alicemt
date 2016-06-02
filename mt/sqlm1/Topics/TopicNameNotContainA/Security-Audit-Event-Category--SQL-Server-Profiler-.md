---
title: Security Audit Event Category (SQL Server Profiler)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e64f7695-2f23-4adb-b83d-52f147cc1a2f
---
# Security Audit Event Category (SQL Server Profiler)
  The **Security Audit** event category contains security audit events.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Audit Add DB User Event Class](../../Topics\TopicNameNotContainA/Audit-Add-DB-User-Event-Class.md)|Indicates that a login has been added or removed as a database user to a database.|  
|[Audit Add Login to Server Role Event Class](../../Topics\TopicNameNotContainA/Audit-Add-Login-to-Server-Role-Event-Class.md)|Indicates that a login was added or removed from a fixed server role.|  
|[Audit Add Member to DB Role Event Class](../../Topics\TopicNameNotContainA/Audit-Add-Member-to-DB-Role-Event-Class.md)|Indicates that a login has been added to or removed from a role.|  
|[Audit Add Role Event Class](../../Topics\TopicNameNotContainA/Audit-Add-Role-Event-Class.md)|Indicates that a database role was added to or removed from a database.|  
|[Audit Addlogin Event Class](../../Topics\TopicNameNotContainA/Audit-Addlogin-Event-Class.md)|Indicates that a login has been added or removed.|  
|[Audit App Role Change Password Event Class](../../Topics\TopicNameNotContainA/Audit-App-Role-Change-Password-Event-Class.md)|Indicates that a password has been changed for an application role.|  
|[Audit Backup and Restore Event Class](../../Topics\TopicNameNotContainA/Audit-Backup-and-Restore-Event-Class.md)|Indicates that a backup or restore statement has been issued.|  
|[Audit Broker Conversation Event Class](../../Topics\TopicNameNotContainA/Audit-Broker-Conversation-Event-Class.md)|Reports audit messages related to Service Broker dialog security.|  
|[Audit Broker Login Event Class](../../Topics\TopicNameNotContainA/Audit-Broker-Login-Event-Class.md)|Reports audit messages related to Service Broker transport security.|  
|[Audit Change Audit Event Class](../../Topics\TopicNameNotContainA/Audit-Change-Audit-Event-Class.md)|Indicates that an audit trace modification has been made.|  
|[Audit Change Database Owner Event Class](../../Topics\TopicNameNotContainA/Audit-Change-Database-Owner-Event-Class.md)|Indicates that the permissions to change the owner of a database have been checked.|  
|[Audit Database Management Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Management-Event-Class.md)|Indicates that a database has been created, altered, or dropped.|  
|[Audit Database Mirroring Login Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Mirroring-Login-Event-Class.md)|Reports audit messages related to database mirroring transport security.|  
|[Audit Database Object Access Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Object-Access-Event-Class.md)|Indicates that a database object, such as a schema, has been accessed.|  
|[Audit Database Object GDR Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Object-GDR-Event-Class.md)|Indicates that a GDR event for a database object has occurred.|  
|[Audit Database Object Management Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Object-Management-Event-Class.md)|Indicates that a CREATE, ALTER, or DROP statement was executed on a database object.|  
|[Audit Database Object Take Ownership Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Object-Take-Ownership-Event-Class.md)|Indicates that there has been a change of owner for objects in database scope.|  
|[Audit Database Operation Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Operation-Event-Class.md)|Indicates that various operations such as checkpoint or subscribe query notification have occurred.|  
|[Audit Database Principal Impersonation Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Principal-Impersonation-Event-Class.md)|Indicates that an impersonation has occurred within the database scope.|  
|[Audit Database Principal Management Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Principal-Management-Event-Class.md)|Indicates that principals have been created, altered, or dropped from a database.|  
|[Audit Database Scope GDR Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Scope-GDR-Event-Class.md)|Indicates that a GRANT, REVOKE, or DENY has been issued for a statement permission by a user in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].|  
|[Audit DBCC Event Class](../../Topics\TopicNameNotContainA/Audit-DBCC-Event-Class.md)|Indicates that a DBCC command has been issued.|  
|[Audit Fulltext Event Class](../../Topics\TopicNameNotContainA/Audit-Fulltext-Event-Class.md)|Indicates that a full\-text event has occured.|  
|[Audit Login Change Password Event Class](../../Topics\TopicNameNotContainA/Audit-Login-Change-Password-Event-Class.md)|Indicates that a user has changed their [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login password.|  
|[Audit Login Change Property Event Class](../../Topics\TopicNameNotContainA/Audit-Login-Change-Property-Event-Class.md)|Indicates that **sp\_defaultdb**, **sp\_defaultlanguage**, or ALTER LOGIN was used to modify a property of a login.|  
|[Audit Login Event Class](../../Topics\TopicNameNotContainA/Audit-Login-Event-Class.md)|Indicates that a user has successfully logged into [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].|  
|[Audit Login Failed Event Class](../../Topics\TopicNameNotContainA/Audit-Login-Failed-Event-Class.md)|Indicates that a user attempted to log in to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and failed.|  
|[Audit Login GDR Event Class](../../Topics\TopicNameNotContainA/Audit-Login-GDR-Event-Class.md)|Indicates that a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows login right was added or removed.|  
|[Audit Logout Event Class](../../Topics\TopicNameNotContainA/Audit-Logout-Event-Class.md)|Indicates that a user has logged out of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].|  
|[Audit Object Derived Permission Event Class](../../Topics\TopicNameNotContainA/Audit-Object-Derived-Permission-Event-Class.md)|Indicates that a CREATE, ALTER, or DROP was issued for an object.|  
|[Audit Schema Object Access Event Class](../../Topics\TopicNameNotContainA/Audit-Schema-Object-Access-Event-Class.md)|Indicates that an object permission \(such as SELECT\) has been used.|  
|[Audit Schema Object GDR Event Class](../../Topics\TopicNameNotContainA/Audit-Schema-Object-GDR-Event-Class.md)|Indicates that a GRANT, REVOKE, or DENY was issued for a schema object permission by a user in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].|  
|[Audit Schema Object Management Event Class](../../Topics\TopicNameNotContainA/Audit-Schema-Object-Management-Event-Class.md)|Indicates that a server object has been created, altered, or dropped.|  
|[Audit Schema Object Take Ownership Event Class](../../Topics\TopicNameNotContainA/Audit-Schema-Object-Take-Ownership-Event-Class.md)|Indicates that the permissions to change the owner of schema object have been checked.|  
|[Audit Server Alter Trace Event Class](../../Topics\TopicNameNotContainA/Audit-Server-Alter-Trace-Event-Class.md)|Indicates that the ALTER TRACE permission has been checked.|  
|[Audit Server Object GDR Event Class](../../Topics\TopicNameNotContainA/Audit-Server-Object-GDR-Event-Class.md)|Indicates that a GDR event for a schema object has occurred.|  
|[Audit Server Object Management Event Class](../../Topics\TopicNameNotContainA/Audit-Server-Object-Management-Event-Class.md)|Indicates that a CREATE, ALTER, or DROP event has occurred for a server object.|  
|[Audit Server Object Take Ownership Event Class](../../Topics\TopicNameNotContainA/Audit-Server-Object-Take-Ownership-Event-Class.md)|Indicates that a server object owner has changed.|  
|[Audit Server Operation Event Class](../../Topics\TopicNameNotContainA/Audit-Server-Operation-Event-Class.md)|Indicates that Audit operations have occurred in the server.|  
|[Audit Server Principal Impersonation Event Class](../../Topics\TopicNameNotContainA/Audit-Server-Principal-Impersonation-Event-Class.md)|Indicates that an impersonation has occurred within the server scope.|  
|[Audit Server Principal Management Event Class](../../Topics\TopicNameNotContainA/Audit-Server-Principal-Management-Event-Class.md)|Indicates that a CREATE, ALTER, or DROP has occurred for a server principal.|  
|[Audit Server Scope GDR Event Class](../../Topics\TopicNameNotContainA/Audit-Server-Scope-GDR-Event-Class.md)|Indicates that a GDR event has occurred for server permissions.|  
|[Audit Server Starts and Stops Event Class](../../Topics\TopicNameNotContainA/Audit-Server-Starts-and-Stops-Event-Class.md)|Indicates that the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service state has been modified.|  
|[Audit Statement Permission Event Class](../../Topics\TopicNameNotContainA/Audit-Statement-Permission-Event-Class.md)|Indicates that a statement permission has been used.|  
  
## Related Content  
 [Extended Events](../../Topics\TopicNameNotContainA/Extended-Events.md)  
  
  