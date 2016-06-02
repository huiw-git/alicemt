---
title: SQL Server Audit Action Groups and Actions
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b7422911-7524-4bcd-9ab9-e460d5897b3d
---
# SQL Server Audit Action Groups and Actions
  The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Audit feature enables you to audit server\-level and database\-level groups of events and individual events. For more information, see [SQL Server Audit &#40;Database Engine&#41;](../Topic/SQL%20Server%20Audit%20\(Database%20Engine\).md).  
  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] audits consist of zero or more audit action items. These audit action items can be either a group of actions, such as Server\_Object\_Change\_Group, or individual actions such as SELECT operations on a table.  
  
> [!NOTE]  
>  Server\_Object\_Change\_Group includes CREATE, ALTER, and DROP for any server object \(Database or Endpoint\).  
  
 Audits can have the following categories of actions:  
  
-   Server\-level. These actions include server operations, such as management changes and logon and logoff operations.  
  
-   Database\-level. These actions encompass data manipulation languages \(DML\) and data definition language \(DDL\) operations.  
  
-   Audit\-level. These actions include actions in the auditing process.  
  
 Some actions performed on [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] auditing components are intrinsically audited in a specific audit, and in these cases audit events occur automatically because the event occurred on the parent object.  
  
 The following actions are intrinsically audited:  
  
-   Server Audit State Change \(setting State to ON or OFF\)  
  
 The following events are not intrinsically audited:  
  
-   CREATE SERVER AUDIT SPECIFICATION  
  
-   ALTER SERVER AUDIT SPECIFICATION  
  
-   DROP SERVER AUDIT SPECIFICATION  
  
-   CREATE DATABASE AUDIT SPECIFICATION  
  
-   ALTER DATABASE AUDIT SPECIFICATION  
  
-   DROP DATABASE AUDIT SPECIFICATION  
  
 All audits are disabled when initially created.  
  
## Server\-Level Audit Action Groups  
 Server\-level audit action groups are actions similar to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] security audit event classes. For more information, see [SQL Server Event Class Reference](../../Topics\TopicNameNotContainA/SQL-Server-Event-Class-Reference.md).  
  
 The following table describes the server\-level audit action groups and provides the equivalent SQL Server Event Class where applicable.  
  
|Action group name|Description|  
|-----------------------|-----------------|  
|APPLICATION\_ROLE\_CHANGE\_PASSWORD\_GROUP|This event is raised whenever a password is changed for an application role. Equivalent to the [Audit App Role Change Password Event Class](../../Topics\TopicNameNotContainA/Audit-App-Role-Change-Password-Event-Class.md).|  
|AUDIT\_CHANGE\_GROUP|This event is raised whenever any audit is created, modified or deleted. This event is raised whenever any audit specification is created, modified, or deleted. Any change to an audit is audited in that audit. Equivalent to the [Audit Change Audit Event Class](../../Topics\TopicNameNotContainA/Audit-Change-Audit-Event-Class.md).|  
|BACKUP\_RESTORE\_GROUP|This event is raised whenever a backup or restore command is issued. Equivalent to the [Audit Backup and Restore Event Class](../../Topics\TopicNameNotContainA/Audit-Backup-and-Restore-Event-Class.md).|  
|BROKER\_LOGIN\_GROUP|This event is raised to report audit messages related to Service Broker transport security. Equivalent to the [Audit Broker Login Event Class](../../Topics\TopicNameNotContainA/Audit-Broker-Login-Event-Class.md).|  
|DATABASE\_CHANGE\_GROUP|This event is raised when a database is created, altered, or dropped. This event is raised whenever any database is created, altered or dropped. Equivalent to the [Audit Database Management Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Management-Event-Class.md).|  
|DATABASE\_LOGOUT\_GROUP|This event is raised when a contained database user logs out of a database. Equivalent to the Audit Database Logout Event Class.|  
|DATABASE\_MIRRORING\_LOGIN\_GROUP|This event is raised to report audit messages related to database mirroring transport security. Equivalent to the [Audit Database Mirroring Login Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Mirroring-Login-Event-Class.md).|  
|DATABASE\_OBJECT\_ACCESS\_GROUP|This event is raised whenever database objects such as message type, assembly, contract are accessed. This event is raised for any access to any database. Note: This could potentially lead to large audit records.<br /><br /> Equivalent to the [Audit Database Object Access Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Object-Access-Event-Class.md).|  
|DATABASE\_OBJECT\_CHANGE\_GROUP|This event is raised when a CREATE, ALTER, or DROP statement is executed on database objects, such as schemas. This event is raised whenever any database object is created, altered or dropped. Note: This could lead to very large quantities of audit records.<br /><br /> Equivalent to the [Audit Database Object Management Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Object-Management-Event-Class.md).|  
|DATABASE\_OBJECT\_OWNERSHIP\_CHANGE\_GROUP|This event is raised when a change of owner for objects within database scope. This event is raised for any object ownership change in any database on the server. Equivalent to the [Audit Database Object Take Ownership Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Object-Take-Ownership-Event-Class.md).|  
|DATABASE\_OBJECT\_PERMISSION\_CHANGE\_GROUP|This event is raised when a GRANT, REVOKE, or DENY has been issued for database objects, such as assemblies and schemas. This event is raised for any object permission change for any database on the server. Equivalent to the [Audit Database Object GDR Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Object-GDR-Event-Class.md).|  
|DATABASE\_OPERATION\_GROUP|This event is raised when operations in a database, such as checkpoint or subscribe query notification, occur. This event is raised on any database operation on any database. Equivalent to the [Audit Database Operation Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Operation-Event-Class.md).|  
|DATABASE\_OWNERSHIP\_CHANGE\_GROUP|This event is raised when you use the ALTER AUTHORIZATION statement to change the owner of a database, and the permissions that are required to do that are checked. This event is raised for any database ownership change on any database on the server. Equivalent to the [Audit Change Database Owner Event Class](../../Topics\TopicNameNotContainA/Audit-Change-Database-Owner-Event-Class.md).|  
|DATABASE\_PERMISSION\_CHANGE\_GROUP|This event is raised whenever a GRANT, REVOKE, or DENY is issued for a statement permission by any principal in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] \(This applies to database\-only events, such as granting permissions on a database\).<br /><br /> This event is raised for any database permission change \(GDR\) for any database in the server. Equivalent to the [Audit Database Scope GDR Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Scope-GDR-Event-Class.md).|  
|DATABASE\_PRINCIPAL\_CHANGE\_GROUP|This event is raised when principals, such as users, are created, altered, or dropped from a database. Equivalent to the [Audit Database Principal Management Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Principal-Management-Event-Class.md). \(Also equivalent to the Audit Add DB Principal Event Class, which occurs on the deprecated sp\_grantdbaccess, sp\_revokedbaccess, sp\_addPrincipal, and sp\_dropPrincipal stored procedures.\)<br /><br /> This event is raised whenever a database role is added to or removed by using the sp\_addrole, sp\_droprole stored procedures. This event is raised whenever any database principals are created, altered, or dropped from any database. Equivalent to the [Audit Add Role Event Class](../../Topics\TopicNameNotContainA/Audit-Add-Role-Event-Class.md).|  
|DATABASE\_PRINCIPAL\_IMPERSONATION\_GROUP|This event is raised when there is an impersonation operation in the database scope such as EXECUTE AS \<principal\> or SETPRINCIPAL. This event is raised for impersonations done in any database. Equivalent to the [Audit Database Principal Impersonation Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Principal-Impersonation-Event-Class.md).|  
|DATABASE\_ROLE\_MEMBER\_CHANGE\_GROUP|This event is raised whenever a login is added to or removed from a database role. This event class is raised for the sp\_addrolemember, sp\_changegroup, and sp\_droprolemember stored procedures. This event is raised on any Database role member change in any database. Equivalent to the [Audit Add Member to DB Role Event Class](../../Topics\TopicNameNotContainA/Audit-Add-Member-to-DB-Role-Event-Class.md).|  
|DBCC\_GROUP|This event is raised whenever a principal issues any DBCC command. Equivalent to the [Audit DBCC Event Class](../../Topics\TopicNameNotContainA/Audit-DBCC-Event-Class.md).|  
|FAILED\_DATABASE\_AUTHENTICATION\_GROUP|Indicates that a principal tried to log on to a contained database and failed. Events in this class are raised by new connections or by connections that are reused from a connection pool. Equivalent to the [Audit Login Failed Event Class](../../Topics\TopicNameNotContainA/Audit-Login-Failed-Event-Class.md).|  
|FAILED\_LOGIN\_GROUP|Indicates that a principal tried to log on to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and failed. Events in this class are raised by new connections or by connections that are reused from a connection pool. Equivalent to the [Audit Login Failed Event Class](../../Topics\TopicNameNotContainA/Audit-Login-Failed-Event-Class.md).|  
|FULLTEXT\_GROUP|Indicates fulltext event occurred. Equivalent to the [Audit Fulltext Event Class](../../Topics\TopicNameNotContainA/Audit-Fulltext-Event-Class.md).|  
|LOGIN\_CHANGE\_PASSWORD\_GROUP|This event is raised whenever a login password is changed by way of ALTER LOGIN statement or sp\_password stored procedure. Equivalent to the [Audit Login Change Password Event Class](../../Topics\TopicNameNotContainA/Audit-Login-Change-Password-Event-Class.md).|  
|LOGOUT\_GROUP|Indicates that a principal has logged out of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Events in this class are raised by new connections or by connections that are reused from a connection pool. Equivalent to the [Audit Logout Event Class](../../Topics\TopicNameNotContainA/Audit-Logout-Event-Class.md).|  
|SCHEMA\_OBJECT\_ACCESS\_GROUP|This event is raised whenever an object permission has been used in the schema. Equivalent to the [Audit Schema Object Access Event Class](../../Topics\TopicNameNotContainA/Audit-Schema-Object-Access-Event-Class.md).|  
|SCHEMA\_OBJECT\_CHANGE\_GROUP|This event is raised when a CREATE, ALTER, or DROP operation is performed on a schema. Equivalent to the [Audit Schema Object Management Event Class](../../Topics\TopicNameNotContainA/Audit-Schema-Object-Management-Event-Class.md).<br /><br /> This event is raised on schema objects. Equivalent to the [Audit Object Derived Permission Event Class](../../Topics\TopicNameNotContainA/Audit-Object-Derived-Permission-Event-Class.md).<br /><br /> This event is raised whenever any schema of any database changes. Equivalent to the [Audit Statement Permission Event Class](../../Topics\TopicNameNotContainA/Audit-Statement-Permission-Event-Class.md).|  
|SCHEMA\_OBJECT\_OWNERSHIP\_CHANGE\_GROUP|This event is raised when the permissions to change the owner of schema object \(such as a table, procedure, or function\) is checked. This occurs when the ALTER AUTHORIZATION statement is used to assign an owner to an object. This event is raised for any schema ownership change for any database on the server. Equivalent to the [Audit Schema Object Take Ownership Event Class](../../Topics\TopicNameNotContainA/Audit-Schema-Object-Take-Ownership-Event-Class.md).|  
|SCHEMA\_OBJECT\_PERMISSION\_CHANGE\_GROUP|This event is raised whenever a grant, deny, revoke is performed against a schema object. Equivalent to the [Audit Schema Object GDR Event Class](../../Topics\TopicNameNotContainA/Audit-Schema-Object-GDR-Event-Class.md).|  
|SERVER\_OBJECT\_CHANGE\_GROUP|This event is raised for CREATE, ALTER, or DROP operations on server objects. Equivalent to the [Audit Server Object Management Event Class](../../Topics\TopicNameNotContainA/Audit-Server-Object-Management-Event-Class.md).|  
|SERVER\_OBJECT\_OWNERSHIP\_CHANGE\_GROUP|This event is raised when the owner is changed for objects in server scope. Equivalent to the [Audit Server Object Take Ownership Event Class](../../Topics\TopicNameNotContainA/Audit-Server-Object-Take-Ownership-Event-Class.md).|  
|SERVER\_OBJECT\_PERMISSION\_CHANGE\_GROUP|This event is raised whenever a GRANT, REVOKE, or DENY is issued for a server object permission by any principal in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Equivalent to the [Audit Server Object GDR Event Class](../../Topics\TopicNameNotContainA/Audit-Server-Object-GDR-Event-Class.md).|  
|SERVER\_OPERATION\_GROUP|This event is raised when Security Audit operations such as altering settings, resources, external access, or authorization are used. Equivalent to the [Audit Server Operation Event Class](../../Topics\TopicNameNotContainA/Audit-Server-Operation-Event-Class.md).|  
|SERVER\_PERMISSION\_CHANGE\_GROUP|This event is raised when a GRANT, REVOKE, or DENY is issued for permissions in the server scope, such as creating a login. Equivalent to the [Audit Server Scope GDR Event Class](../../Topics\TopicNameNotContainA/Audit-Server-Scope-GDR-Event-Class.md).|  
|SERVER\_PRINCIPAL\_CHANGE\_GROUP|This event is raised when server principals are created, altered, or dropped. Equivalent to the [Audit Server Principal Management Event Class](../../Topics\TopicNameNotContainA/Audit-Server-Principal-Management-Event-Class.md).<br /><br /> This event is raised when a principal issues the sp\_defaultdb or sp\_defaultlanguage stored procedures or ALTER LOGIN statements. Equivalent to the [Audit Addlogin Event Class](../../Topics\TopicNameNotContainA/Audit-Addlogin-Event-Class.md).<br /><br /> This event is raised on the sp\_addlogin and sp\_droplogin stored procedures. Also equivalent to the [Audit Login Change Property Event Class](../../Topics\TopicNameNotContainA/Audit-Login-Change-Property-Event-Class.md).<br /><br /> This event is raised for the sp\_grantlogin or  sp\_revokelogin stored procedures. Equivalent to the [Audit Login GDR Event Class](../../Topics\TopicNameNotContainA/Audit-Login-GDR-Event-Class.md).|  
|SERVER\_PRINCIPAL\_IMPERSONATION\_GROUP|This event is raised when there is an impersonation within server scope, such as EXECUTE AS \<login\>. Equivalent to the [Audit Server Principal Impersonation Event Class](../../Topics\TopicNameNotContainA/Audit-Server-Principal-Impersonation-Event-Class.md).|  
|SERVER\_ROLE\_MEMBER\_CHANGE\_GROUP|This event is raised whenever a login is added or removed from a fixed server role. This event is raised for the sp\_addsrvrolemember and sp\_dropsrvrolemember stored procedures. Equivalent to the [Audit Add Login to Server Role Event Class](../../Topics\TopicNameNotContainA/Audit-Add-Login-to-Server-Role-Event-Class.md).|  
|SERVER\_STATE\_CHANGE\_GROUP|This event is raised when the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service state is modified. Equivalent to the [Audit Server Starts and Stops Event Class](../../Topics\TopicNameNotContainA/Audit-Server-Starts-and-Stops-Event-Class.md).|  
|SUCCESSFUL\_DATABASE\_AUTHENTICATION\_GROUP|Indicates that a principal successfully logged in to a contained database. Equivalent to the Audit Successful Database Authentication Event Class.|  
|SUCCESSFUL\_LOGIN\_GROUP|Indicates that a principal has successfully logged in to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Events in this class are raised by new connections or by connections that are reused from a connection pool. Equivalent to the [Audit Login Event Class](../../Topics\TopicNameNotContainA/Audit-Login-Event-Class.md).|  
|TRACE\_CHANGE\_GROUP|This event is raised for all statements that check for the ALTER TRACE permission. Equivalent to the [Audit Server Alter Trace Event Class](../../Topics\TopicNameNotContainA/Audit-Server-Alter-Trace-Event-Class.md).|  
|TRANSACTION\_GROUP|This event is raised for BEGIN TRANSACTION, ROLLBACK TRANSACTION, and COMMIT TRANSACTION operations, both for explicit calls to those statements and implicit transaction operations. This event is also raised for UNDO operations for individual statements caused by the rollback of a transaction.|  
|USER\_CHANGE\_PASSWORD\_GROUP|This event is raised whenever the password of a contained database user is changed by using the ALTER USER statement.|  
|USER\_DEFINED\_AUDIT\_GROUP|This group monitors events raised by using [sp_audit_write &#40;Transact-SQL&#41;](../Topic/sp_audit_write%20\(Transact-SQL\).md). Typically triggers or stored procedures include calls to **sp\_audit\_write** to enable auditing of important events.|  
  
### Considerations  
 Server\-level action groups cover actions across a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance. For example, any schema object access check in any database is recorded if the appropriate action group is added to a server audit specification. In a database audit specification, only schema object accesses in that database are recorded.  
  
 Server\-level actions do not allow for detailed filtering on database\-level actions. A database\-level audit, such as audit of SELECT actions on the Customers table for logins in the Employee group is required to implement detailed action filtering. Do not include server\-scoped objects, such as the system views, in a user database audit specification.  
  
## Database\-Level Audit Action Groups  
 Database\-Level Audit Action Groups are actions similar to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Security Audit Event classes. For more information about event classes, see [SQL Server Event Class Reference](../../Topics\TopicNameNotContainA/SQL-Server-Event-Class-Reference.md).  
  
 The following table describes the database\-level audit action groups and provides their equivalent SQL Server Event Class where applicable.  
  
|Action group name|Description|  
|-----------------------|-----------------|  
|APPLICATION\_ROLE\_CHANGE\_PASSWORD\_GROUP|This event is raised whenever a password is changed for an application role. Equivalent to the [Audit App Role Change Password Event Class](../../Topics\TopicNameNotContainA/Audit-App-Role-Change-Password-Event-Class.md).|  
|AUDIT\_CHANGE\_GROUP|This event is raised whenever any audit is created, modified or deleted. This event is raised whenever any audit specification is created, modified, or deleted. Any change to an audit is audited in that audit. Equivalent to the [Audit Change Audit Event Class](../../Topics\TopicNameNotContainA/Audit-Change-Audit-Event-Class.md).|  
|BACKUP\_RESTORE\_GROUP|This event is raised whenever a backup or restore command is issued. Equivalent to the [Audit Backup and Restore Event Class](../../Topics\TopicNameNotContainA/Audit-Backup-and-Restore-Event-Class.md).|  
|DATABASE\_CHANGE\_GROUP|This event is raised when a database is created, altered, or dropped. Equivalent to the [Audit Database Management Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Management-Event-Class.md).|  
|DATABASE\_LOGOUT\_GROUP|This event is raised when a contained database user logs out of a database. Equivalent to the [Audit Backup and Restore Event Class](../../Topics\TopicNameNotContainA/Audit-Backup-and-Restore-Event-Class.md).|  
|DATABASE\_OBJECT\_ACCESS\_GROUP|This event is raised whenever database objects such as certificates and asymmetric keys are accessed. Equivalent to the [Audit Database Object Access Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Object-Access-Event-Class.md).|  
|DATABASE\_OBJECT\_CHANGE\_GROUP|This event is raised when a CREATE, ALTER, or DROP statement is executed on database objects, such as schemas. Equivalent to the [Audit Database Object Management Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Object-Management-Event-Class.md).|  
|DATABASE\_OBJECT\_OWNERSHIP\_CHANGE\_GROUP|This event is raised when a change of owner for objects within database scope occurs. Equivalent to the [Audit Database Object Take Ownership Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Object-Take-Ownership-Event-Class.md).|  
|DATABASE\_OBJECT\_PERMISSION\_CHANGE\_GROUP|This event is raised when a GRANT, REVOKE, or DENY has been issued for database objects, such as assemblies and schemas. Equivalent to the [Audit Database Object GDR Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Object-GDR-Event-Class.md).|  
|DATABASE\_OPERATION\_GROUP|This event is raised when operations in a database, such as checkpoint or subscribe query notification, occur. Equivalent to the [Audit Database Operation Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Operation-Event-Class.md).|  
|DATABASE\_OWNERSHIP\_CHANGE\_GROUP|This event is raised when you use the ALTER AUTHORIZATION statement to change the owner of a database, and the permissions that are required to do that are checked. Equivalent to the [Audit Change Database Owner Event Class](../../Topics\TopicNameNotContainA/Audit-Change-Database-Owner-Event-Class.md).|  
|DATABASE\_PERMISSION\_CHANGE\_GROUP|This event is raised whenever a GRANT, REVOKE, or DENY is issued for a statement permission by any user in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] for database\-only events such as granting permissions on a database. Equivalent to the [Audit Database Scope GDR Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Scope-GDR-Event-Class.md).|  
|DATABASE\_PRINCIPAL\_CHANGE\_GROUP|This event is raised when principals, such as users, are created, altered, or dropped from a database. Equivalent to the [Audit Database Principal Management Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Principal-Management-Event-Class.md). Also equivalent to the [Audit Add DB User Event Class](../../Topics\TopicNameNotContainA/Audit-Add-DB-User-Event-Class.md), which occurs on deprecated sp\_grantdbaccess, sp\_revokedbaccess, sp\_adduser, and sp\_dropuser stored procedures.<br /><br /> This event is raised whenever a database role is added to or removed using deprecated sp\_addrole and sp\_droprole stored procedures. Equivalent to the [Audit Add Role Event Class](../../Topics\TopicNameNotContainA/Audit-Add-Role-Event-Class.md).|  
|DATABASE\_PRINCIPAL\_IMPERSONATION\_GROUP|This event is raised when there is an impersonation within database scope such as EXECUTE AS \<user\>. Equivalent to the [Audit Database Principal Impersonation Event Class](../../Topics\TopicNameNotContainA/Audit-Database-Principal-Impersonation-Event-Class.md).|  
|DATABASE\_ROLE\_MEMBER\_CHANGE\_GROUP|This event is raised whenever a login is added to or removed from a database role. This event class is used with the sp\_addrolemember, sp\_changegroup, and sp\_droprolemember stored procedures.Equivalent to the [Audit Add Member to DB Role Event Class](../../Topics\TopicNameNotContainA/Audit-Add-Member-to-DB-Role-Event-Class.md)|  
|DBCC\_GROUP|This event is raised whenever a principal issues any DBCC command. Equivalent to the [Audit DBCC Event Class](../../Topics\TopicNameNotContainA/Audit-DBCC-Event-Class.md).|  
|FAILED\_DATABASE\_AUTHENTICATION\_GROUP|Indicates that a principal tried to log on to a contained database and failed. Events in this class are raised by new connections or by connections that are reused from a connection pool. This event is raised.|  
|SCHEMA\_OBJECT\_ACCESS\_GROUP|This event is raised whenever an object permission has been used in the schema. Equivalent to the [Audit Schema Object Access Event Class](../../Topics\TopicNameNotContainA/Audit-Schema-Object-Access-Event-Class.md).|  
|SCHEMA\_OBJECT\_CHANGE\_GROUP|This event is raised when a CREATE, ALTER, or DROP operation is performed on a schema. Equivalent to the [Audit Schema Object Management Event Class](../../Topics\TopicNameNotContainA/Audit-Schema-Object-Management-Event-Class.md).<br /><br /> This event is raised on schema objects. Equivalent to the [Audit Object Derived Permission Event Class](../../Topics\TopicNameNotContainA/Audit-Object-Derived-Permission-Event-Class.md). Also equivalent to the [Audit Statement Permission Event Class](../../Topics\TopicNameNotContainA/Audit-Statement-Permission-Event-Class.md).|  
|SCHEMA\_OBJECT\_OWNERSHIP\_CHANGE\_GROUP|This event is raised when the permissions to change the owner of schema object such as a table, procedure, or function is checked. This occurs when the ALTER AUTHORIZATION statement is used to assign an owner to an object. Equivalent to the [Audit Schema Object Take Ownership Event Class](../../Topics\TopicNameNotContainA/Audit-Schema-Object-Take-Ownership-Event-Class.md).|  
|SCHEMA\_OBJECT\_PERMISSION\_CHANGE\_GROUP|This event is raised whenever a grant, deny, or revoke is issued for a schema object. Equivalent to the [Audit Schema Object GDR Event Class](../../Topics\TopicNameNotContainA/Audit-Schema-Object-GDR-Event-Class.md).|  
|SUCCESSFUL\_DATABASE\_AUTHENTICATION\_GROUP|Indicates that a principal successfully logged in to a contained database. Equivalent to the Audit Successful Database Authentication Event Class.|  
|USER\_CHANGE\_PASSWORD\_GROUP|This event is raised whenever the password of a contained database user is changed by using the ALTER USER statement.|  
|USER\_DEFINED\_AUDIT\_GROUP|This group monitors events raised by using [sp_audit_write &#40;Transact-SQL&#41;](../Topic/sp_audit_write%20\(Transact-SQL\).md).|  
  
## Database\-Level Audit Actions  
 Database\-level actions support the auditing of specific actions directly on database schema and schema objects, such as Tables, Views, Stored Procedures, Functions, Extended Stored Procedures, Queues, Synonyms. Types, XML Schema Collection, Database, and Schema are not audited. The audit of schema objects may be configured on Schema and Database, which means that events on all schema objects contained by the specified schema or database will be audited. The following table describes database\-level audit actions.  
  
|Action|Description|  
|------------|-----------------|  
|SELECT|This event is raised whenever a SELECT is issued.|  
|UPDATE|This event is raised whenever an UPDATE is issued.|  
|INSERT|This event is raised whenever an INSERT is issued.|  
|DELETE|This event is raised whenever a DELETE is issued.|  
|EXECUTE|This event is raised whenever an EXECUTE is issued.|  
|RECEIVE|This event is raised whenever a RECEIVE is issued.|  
|REFERENCES|This event is raised whenever a REFERENCES permission is checked.|  
  
### Considerations  
 Database\-level audit actions do not apply to Columns.  
  
 When the query processor parameterizes the query, the parameter can appear in the audit event log instead of the column values of the query.  
  
## Audit\-Level Audit Action Groups  
 You can also audit the actions in the auditing process. This can be in the server scope or the database scope. In the database scope, it only occurs for database audit specifications. The following table describes audit\-level audit action groups.  
  
|Action group name|Description|  
|-----------------------|-----------------|  
|AUDIT\_ CHANGE\_GROUP|This event is raised whenever one of the following commands are issued:<br /><br /> CREATE SERVER AUDIT<br /><br /> ALTER SERVER AUDIT<br /><br /> DROP SERVER AUDIT<br /><br /> CREATE SERVER AUDIT SPECIFICATION<br /><br /> ALTER SERVER AUDIT SPECIFICATION<br /><br /> DROP SERVER AUDIT SPECIFICATION<br /><br /> CREATE DATABASE AUDIT SPECIFICATION<br /><br /> ALTER DATABASE AUDIT SPECIFICATION<br /><br /> DROP DATABASE AUDIT SPECIFICATION|  
  
## Related Content  
 [Create a Server Audit and Server Audit Specification](../../Topics\TopicNameContainA/Create-a-Server-Audit-and-Server-Audit-Specification.md)  
  
 [Create a Server Audit and Database Audit Specification](../../Topics\TopicNameContainA/Create-a-Server-Audit-and-Database-Audit-Specification.md)  
  
 [CREATE SERVER AUDIT &#40;Transact-SQL&#41;](../Topic/CREATE%20SERVER%20AUDIT%20\(Transact-SQL\).md)  
  
 [ALTER SERVER AUDIT  &#40;Transact-SQL&#41;](../Topic/ALTER%20SERVER%20AUDIT%20%20\(Transact-SQL\).md)  
  
 [DROP SERVER AUDIT  &#40;Transact-SQL&#41;](../Topic/DROP%20SERVER%20AUDIT%20%20\(Transact-SQL\).md)  
  
 [CREATE SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../Topic/CREATE%20SERVER%20AUDIT%20SPECIFICATION%20\(Transact-SQL\).md)  
  
 [ALTER SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../Topic/ALTER%20SERVER%20AUDIT%20SPECIFICATION%20\(Transact-SQL\).md)  
  
 [DROP SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../Topic/DROP%20SERVER%20AUDIT%20SPECIFICATION%20\(Transact-SQL\).md)  
  
 [CREATE DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../Topic/CREATE%20DATABASE%20AUDIT%20SPECIFICATION%20\(Transact-SQL\).md)  
  
 [ALTER DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20AUDIT%20SPECIFICATION%20\(Transact-SQL\).md)  
  
 [DROP DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../Topic/DROP%20DATABASE%20AUDIT%20SPECIFICATION%20\(Transact-SQL\).md)  
  
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../Topic/ALTER%20AUTHORIZATION%20\(Transact-SQL\).md)  
  
 [sys.fn_get_audit_file &#40;Transact-SQL&#41;](../Topic/sys.fn_get_audit_file%20\(Transact-SQL\).md)  
  
 [sys.server_audits &#40;Transact-SQL&#41;](../Topic/sys.server_audits%20\(Transact-SQL\).md)  
  
 [sys.server_file_audits &#40;Transact-SQL&#41;](../Topic/sys.server_file_audits%20\(Transact-SQL\).md)  
  
 [sys.server_audit_specifications &#40;Transact-SQL&#41;](../Topic/sys.server_audit_specifications%20\(Transact-SQL\).md)  
  
 [sys.server_audit_specification_details &#40;Transact-SQL&#41;](../Topic/sys.server_audit_specification_details%20\(Transact-SQL\).md)  
  
 [sys.database_audit_specifications &#40;Transact-SQL&#41;](../Topic/sys.database_audit_specifications%20\(Transact-SQL\).md)  
  
 [sys.database_audit_specification_details &#40;Transact-SQL&#41;](../Topic/sys.database_audit_specification_details%20\(Transact-SQL\).md)  
  
 [sys.dm_server_audit_status &#40;Transact-SQL&#41;](../Topic/sys.dm_server_audit_status%20\(Transact-SQL\).md)  
  
 [sys.dm_audit_actions &#40;Transact-SQL&#41;](../Topic/sys.dm_audit_actions%20\(Transact-SQL\).md)  
  
 [sys.dm_audit_class_type_map &#40;Transact-SQL&#41;](../Topic/sys.dm_audit_class_type_map%20\(Transact-SQL\).md)  
  
  