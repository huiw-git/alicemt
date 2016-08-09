---
title: "SQL Server Audit Action Groups and Actions"
ms.custom: na
ms.date: 2016-05-17
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b7422911-7524-4bcd-9ab9-e460d5897b3d
caps.latest.revision: 44
caps.handback.revision: 0
manager: jhubbard
---
# SQL Server Audit Action Groups and Actions
The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Audit feature enables you to audit server-level and database-level groups of events and individual events. For more information, see [SQL Server Audit (Database Engine)](../../Topics/TopicNameNotContainA/SQL-Server-Audit--Database-Engine-.md).  
  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] audits consist of zero or more audit action items. These audit action items can be either a group of actions, such as Server_Object_Change_Group, or individual actions such as SELECT operations on a table.  
  
> [!NOTE]  
>  Server_Object_Change_Group includes CREATE, ALTER, and DROP for any server object (Database or Endpoint).  
  
 Audits can have the following categories of actions:  
  
-   Server-level. These actions include server operations, such as management changes and logon and logoff operations.  
  
-   Database-level. These actions encompass data manipulation languages (DML) and data definition language (DDL) operations.  
  
-   Audit-level. These actions include actions in the auditing process.  
  
 Some actions performed on [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] auditing components are intrinsically audited in a specific audit, and in these cases audit events occur automatically because the event occurred on the parent object.  
  
 The following actions are intrinsically audited:  
  
-   Server Audit State Change (setting State to ON or OFF)  
  
 The following events are not intrinsically audited:  
  
-   CREATE SERVER AUDIT SPECIFICATION  
  
-   ALTER SERVER AUDIT SPECIFICATION  
  
-   DROP SERVER AUDIT SPECIFICATION  
  
-   CREATE DATABASE AUDIT SPECIFICATION  
  
-   ALTER DATABASE AUDIT SPECIFICATION  
  
-   DROP DATABASE AUDIT SPECIFICATION  
  
 All audits are disabled when initially created.  
  
## Server-Level Audit Action Groups  
 Server-level audit action groups are actions similar to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] security audit event classes. For more information, see [SQL Server Event Class Reference](../../Topics/TopicNameNotContainA/SQL-Server-Event-Class-Reference.md).  
  
 The following table describes the server-level audit action groups and provides the equivalent SQL Server Event Class where applicable.  
  
|Action group name|Description|  
|-----------------------|-----------------|  
|APPLICATION_ROLE_CHANGE_PASSWORD_GROUP|This event is raised whenever a password is changed for an application role. Equivalent to the [Audit App Role Change Password Event Class](../../Topics/TopicNameNotContainA/Audit-App-Role-Change-Password-Event-Class.md).|  
|AUDIT_CHANGE_GROUP|This event is raised whenever any audit is created, modified or deleted. This event is raised whenever any audit specification is created, modified, or deleted. Any change to an audit is audited in that audit. Equivalent to the [Audit Change Audit Event Class](../../Topics/TopicNameNotContainA/Audit-Change-Audit-Event-Class.md).|  
|BACKUP_RESTORE_GROUP|This event is raised whenever a backup or restore command is issued. Equivalent to the [Audit Backup and Restore Event Class](../../Topics/TopicNameNotContainA/Audit-Backup-and-Restore-Event-Class.md).|  
|BROKER_LOGIN_GROUP|This event is raised to report audit messages related to Service Broker transport security. Equivalent to the [Audit Broker Login Event Class](../../Topics/TopicNameNotContainA/Audit-Broker-Login-Event-Class.md).|  
|DATABASE_CHANGE_GROUP|This event is raised when a database is created, altered, or dropped. This event is raised whenever any database is created, altered or dropped. Equivalent to the [Audit Database Management Event Class](../../Topics/TopicNameNotContainA/Audit-Database-Management-Event-Class.md).|  
|DATABASE_LOGOUT_GROUP|This event is raised when a contained database user logs out of a database. Equivalent to the Audit Database Logout Event Class.|  
|DATABASE_MIRRORING_LOGIN_GROUP|This event is raised to report audit messages related to database mirroring transport security. Equivalent to the [Audit Database Mirroring Login Event Class](../../Topics/TopicNameNotContainA/Audit-Database-Mirroring-Login-Event-Class.md).|  
|DATABASE_OBJECT_ACCESS_GROUP|This event is raised whenever database objects such as message type, assembly, contract are accessed. This event is raised for any access to any database. Note: This could potentially lead to large audit records.<br /><br /> Equivalent to the [Audit Database Object Access Event Class](../../Topics/TopicNameNotContainA/Audit-Database-Object-Access-Event-Class.md).|  
|DATABASE_OBJECT_CHANGE_GROUP|This event is raised when a CREATE, ALTER, or DROP statement is executed on database objects, such as schemas. This event is raised whenever any database object is created, altered or dropped. Note: This could lead to very large quantities of audit records.<br /><br /> Equivalent to the [Audit Database Object Management Event Class](../../Topics/TopicNameNotContainA/Audit-Database-Object-Management-Event-Class.md).|  
|DATABASE_OBJECT_OWNERSHIP_CHANGE_GROUP|This event is raised when a change of owner for objects within database scope. This event is raised for any object ownership change in any database on the server. Equivalent to the [Audit Database Object Take Ownership Event Class](../../Topics/TopicNameNotContainA/Audit-Database-Object-Take-Ownership-Event-Class.md).|  
|DATABASE_OBJECT_PERMISSION_CHANGE_GROUP|This event is raised when a GRANT, REVOKE, or DENY has been issued for database objects, such as assemblies and schemas. This event is raised for any object permission change for any database on the server. Equivalent to the [Audit Database Object GDR Event Class](../../Topics/TopicNameNotContainA/Audit-Database-Object-GDR-Event-Class.md).|  
|DATABASE_OPERATION_GROUP|This event is raised when operations in a database, such as checkpoint or subscribe query notification, occur. This event is raised on any database operation on any database. Equivalent to the [Audit Database Operation Event Class](../../Topics/TopicNameNotContainA/Audit-Database-Operation-Event-Class.md).|  
|DATABASE_OWNERSHIP_CHANGE_GROUP|This event is raised when you use the ALTER AUTHORIZATION statement to change the owner of a database, and the permissions that are required to do that are checked. This event is raised for any database ownership change on any database on the server. Equivalent to the [Audit Change Database Owner Event Class](../../Topics/TopicNameNotContainA/Audit-Change-Database-Owner-Event-Class.md).|  
|DATABASE_PERMISSION_CHANGE_GROUP|This event is raised whenever a GRANT, REVOKE, or DENY is issued for a statement permission by any principal in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] (This applies to database-only events, such as granting permissions on a database).<br /><br /> This event is raised for any database permission change (GDR) for any database in the server. Equivalent to the [Audit Database Scope GDR Event Class](../../Topics/TopicNameNotContainA/Audit-Database-Scope-GDR-Event-Class.md).|  
|DATABASE_PRINCIPAL_CHANGE_GROUP|This event is raised when principals, such as users, are created, altered, or dropped from a database. Equivalent to the [Audit Database Principal Management Event Class](../../Topics/TopicNameNotContainA/Audit-Database-Principal-Management-Event-Class.md). (Also equivalent to the Audit Add DB Principal Event Class, which occurs on the deprecated sp_grantdbaccess, sp_revokedbaccess, sp_addPrincipal, and sp_dropPrincipal stored procedures.)<br /><br /> This event is raised whenever a database role is added to or removed by using the sp_addrole, sp_droprole stored procedures. This event is raised whenever any database principals are created, altered, or dropped from any database. Equivalent to the [Audit Add Role Event Class](../../Topics/TopicNameNotContainA/Audit-Add-Role-Event-Class.md).|  
|DATABASE_PRINCIPAL_IMPERSONATION_GROUP|This event is raised when there is an impersonation operation in the database scope such as EXECUTE AS <principal\> or SETPRINCIPAL. This event is raised for impersonations done in any database. Equivalent to the [Audit Database Principal Impersonation Event Class](../../Topics/TopicNameNotContainA/Audit-Database-Principal-Impersonation-Event-Class.md).|  
|DATABASE_ROLE_MEMBER_CHANGE_GROUP|This event is raised whenever a login is added to or removed from a database role. This event class is raised for the sp_addrolemember, sp_changegroup, and sp_droprolemember stored procedures. This event is raised on any Database role member change in any database. Equivalent to the [Audit Add Member to DB Role Event Class](../../Topics/TopicNameNotContainA/Audit-Add-Member-to-DB-Role-Event-Class.md).|  
|DBCC_GROUP|This event is raised whenever a principal issues any DBCC command. Equivalent to the [Audit DBCC Event Class](../../Topics/TopicNameNotContainA/Audit-DBCC-Event-Class.md).|  
|FAILED_DATABASE_AUTHENTICATION_GROUP|Indicates that a principal tried to log on to a contained database and failed. Events in this class are raised by new connections or by connections that are reused from a connection pool. Equivalent to the [Audit Login Failed Event Class](../../Topics/TopicNameNotContainA/Audit-Login-Failed-Event-Class.md).|  
|FAILED_LOGIN_GROUP|Indicates that a principal tried to log on to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] and failed. Events in this class are raised by new connections or by connections that are reused from a connection pool. Equivalent to the [Audit Login Failed Event Class](../../Topics/TopicNameNotContainA/Audit-Login-Failed-Event-Class.md).|  
|FULLTEXT_GROUP|Indicates fulltext event occurred. Equivalent to the [Audit Fulltext Event Class](../../Topics/TopicNameNotContainA/Audit-Fulltext-Event-Class.md).|  
|LOGIN_CHANGE_PASSWORD_GROUP|This event is raised whenever a login password is changed by way of ALTER LOGIN statement or sp_password stored procedure. Equivalent to the [Audit Login Change Password Event Class](../../Topics/TopicNameNotContainA/Audit-Login-Change-Password-Event-Class.md).|  
|LOGOUT_GROUP|Indicates that a principal has logged out of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. Events in this class are raised by new connections or by connections that are reused from a connection pool. Equivalent to the [Audit Logout Event Class](../../Topics/TopicNameNotContainA/Audit-Logout-Event-Class.md).|  
|SCHEMA_OBJECT_ACCESS_GROUP|This event is raised whenever an object permission has been used in the schema. Equivalent to the [Audit Schema Object Access Event Class](../../Topics/TopicNameNotContainA/Audit-Schema-Object-Access-Event-Class.md).|  
|SCHEMA_OBJECT_CHANGE_GROUP|This event is raised when a CREATE, ALTER, or DROP operation is performed on a schema. Equivalent to the [Audit Schema Object Management Event Class](../../Topics/TopicNameNotContainA/Audit-Schema-Object-Management-Event-Class.md).<br /><br /> This event is raised on schema objects. Equivalent to the [Audit Object Derived Permission Event Class](../../Topics/TopicNameNotContainA/Audit-Object-Derived-Permission-Event-Class.md).<br /><br /> This event is raised whenever any schema of any database changes. Equivalent to the [Audit Statement Permission Event Class](../../Topics/TopicNameNotContainA/Audit-Statement-Permission-Event-Class.md).|  
|SCHEMA_OBJECT_OWNERSHIP_CHANGE_GROUP|This event is raised when the permissions to change the owner of schema object (such as a table, procedure, or function) is checked. This occurs when the ALTER AUTHORIZATION statement is used to assign an owner to an object. This event is raised for any schema ownership change for any database on the server. Equivalent to the [Audit Schema Object Take Ownership Event Class](../../Topics/TopicNameNotContainA/Audit-Schema-Object-Take-Ownership-Event-Class.md).|  
|SCHEMA_OBJECT_PERMISSION_CHANGE_GROUP|This event is raised whenever a grant, deny, revoke is performed against a schema object. Equivalent to the [Audit Schema Object GDR Event Class](../../Topics/TopicNameNotContainA/Audit-Schema-Object-GDR-Event-Class.md).|  
|SERVER_OBJECT_CHANGE_GROUP|This event is raised for CREATE, ALTER, or DROP operations on server objects. Equivalent to the [Audit Server Object Management Event Class](../../Topics/TopicNameNotContainA/Audit-Server-Object-Management-Event-Class.md).|  
|SERVER_OBJECT_OWNERSHIP_CHANGE_GROUP|This event is raised when the owner is changed for objects in server scope. Equivalent to the [Audit Server Object Take Ownership Event Class](../../Topics/TopicNameNotContainA/Audit-Server-Object-Take-Ownership-Event-Class.md).|  
|SERVER_OBJECT_PERMISSION_CHANGE_GROUP|This event is raised whenever a GRANT, REVOKE, or DENY is issued for a server object permission by any principal in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. Equivalent to the [Audit Server Object GDR Event Class](../../Topics/TopicNameNotContainA/Audit-Server-Object-GDR-Event-Class.md).|  
|SERVER_OPERATION_GROUP|This event is raised when Security Audit operations such as altering settings, resources, external access, or authorization are used. Equivalent to the [Audit Server Operation Event Class](../../Topics/TopicNameNotContainA/Audit-Server-Operation-Event-Class.md).|  
|SERVER_PERMISSION_CHANGE_GROUP|This event is raised when a GRANT, REVOKE, or DENY is issued for permissions in the server scope, such as creating a login. Equivalent to the [Audit Server Scope GDR Event Class](../../Topics/TopicNameNotContainA/Audit-Server-Scope-GDR-Event-Class.md).|  
|SERVER_PRINCIPAL_CHANGE_GROUP|This event is raised when server principals are created, altered, or dropped. Equivalent to the [Audit Server Principal Management Event Class](../../Topics/TopicNameNotContainA/Audit-Server-Principal-Management-Event-Class.md).<br /><br /> This event is raised when a principal issues the sp_defaultdb or sp_defaultlanguage stored procedures or ALTER LOGIN statements. Equivalent to the [Audit Addlogin Event Class](../../Topics/TopicNameNotContainA/Audit-Addlogin-Event-Class.md).<br /><br /> This event is raised on the sp_addlogin and sp_droplogin stored procedures. Also equivalent to the [Audit Login Change Property Event Class](../../Topics/TopicNameNotContainA/Audit-Login-Change-Property-Event-Class.md).<br /><br /> This event is raised for the sp_grantlogin or  sp_revokelogin stored procedures. Equivalent to the [Audit Login GDR Event Class](../../Topics/TopicNameNotContainA/Audit-Login-GDR-Event-Class.md).|  
|SERVER_PRINCIPAL_IMPERSONATION_GROUP|This event is raised when there is an impersonation within server scope, such as EXECUTE AS <login\>. Equivalent to the [Audit Server Principal Impersonation Event Class](../../Topics/TopicNameNotContainA/Audit-Server-Principal-Impersonation-Event-Class.md).|  
|SERVER_ROLE_MEMBER_CHANGE_GROUP|This event is raised whenever a login is added or removed from a fixed server role. This event is raised for the sp_addsrvrolemember and sp_dropsrvrolemember stored procedures. Equivalent to the [Audit Add Login to Server Role Event Class](../../Topics/TopicNameNotContainA/Audit-Add-Login-to-Server-Role-Event-Class.md).|  
|SERVER_STATE_CHANGE_GROUP|This event is raised when the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] service state is modified. Equivalent to the [Audit Server Starts and Stops Event Class](../../Topics/TopicNameNotContainA/Audit-Server-Starts-and-Stops-Event-Class.md).|  
|SUCCESSFUL_DATABASE_AUTHENTICATION_GROUP|Indicates that a principal successfully logged in to a contained database. Equivalent to the Audit Successful Database Authentication Event Class.|  
|SUCCESSFUL_LOGIN_GROUP|Indicates that a principal has successfully logged in to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. Events in this class are raised by new connections or by connections that are reused from a connection pool. Equivalent to the [Audit Login Event Class](../../Topics/TopicNameNotContainA/Audit-Login-Event-Class.md).|  
|TRACE_CHANGE_GROUP|This event is raised for all statements that check for the ALTER TRACE permission. Equivalent to the [Audit Server Alter Trace Event Class](../../Topics/TopicNameNotContainA/Audit-Server-Alter-Trace-Event-Class.md).|  
|USER_CHANGE_PASSWORD_GROUP|This event is raised whenever the password of a contained database user is changed by using the ALTER USER statement.|  
|USER_DEFINED_AUDIT_GROUP|This group monitors events raised by using [sp_audit_write (Transact-SQL)](assetId:///4c523848-1ce6-49ad-92b3-e0e90f24f1c2). Typically triggers or stored procedures include calls to **sp_audit_write** to enable auditing of important events.|  
  
### Considerations  
 Server-level action groups cover actions across a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance. For example, any schema object access check in any database is recorded if the appropriate action group is added to a server audit specification. In a database audit specification, only schema object accesses in that database are recorded.  
  
 Server-level actions do not allow for detailed filtering on database-level actions. A database-level audit, such as audit of SELECT actions on the Customers table for logins in the Employee group is required to implement detailed action filtering. Do not include server-scoped objects, such as the system views, in a user database audit specification.  
  
## Database-Level Audit Action Groups  
 Database-Level Audit Action Groups are actions similar to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Security Audit Event classes. For more information about event classes, see [SQL Server Event Class Reference](../../Topics/TopicNameNotContainA/SQL-Server-Event-Class-Reference.md).  
  
 The following table describes the database-level audit action groups and provides their equivalent SQL Server Event Class where applicable.  
  
|Action group name|Description|  
|-----------------------|-----------------|  
|APPLICATION_ROLE_CHANGE_PASSWORD_GROUP|This event is raised whenever a password is changed for an application role. Equivalent to the [Audit App Role Change Password Event Class](../../Topics/TopicNameNotContainA/Audit-App-Role-Change-Password-Event-Class.md).|  
|AUDIT_CHANGE_GROUP|This event is raised whenever any audit is created, modified or deleted. This event is raised whenever any audit specification is created, modified, or deleted. Any change to an audit is audited in that audit. Equivalent to the [Audit Change Audit Event Class](../../Topics/TopicNameNotContainA/Audit-Change-Audit-Event-Class.md).|  
|BACKUP_RESTORE_GROUP|This event is raised whenever a backup or restore command is issued. Equivalent to the [Audit Backup and Restore Event Class](../../Topics/TopicNameNotContainA/Audit-Backup-and-Restore-Event-Class.md).|  
|DATABASE_CHANGE_GROUP|This event is raised when a database is created, altered, or dropped. Equivalent to the [Audit Database Management Event Class](../../Topics/TopicNameNotContainA/Audit-Database-Management-Event-Class.md).|  
|DATABASE_LOGOUT_GROUP|This event is raised when a contained database user logs out of a database. Equivalent to the [Audit Backup and Restore Event Class](../../Topics/TopicNameNotContainA/Audit-Backup-and-Restore-Event-Class.md).|  
|DATABASE_OBJECT_ACCESS_GROUP|This event is raised whenever database objects such as certificates and asymmetric keys are accessed. Equivalent to the [Audit Database Object Access Event Class](../../Topics/TopicNameNotContainA/Audit-Database-Object-Access-Event-Class.md).|  
|DATABASE_OBJECT_CHANGE_GROUP|This event is raised when a CREATE, ALTER, or DROP statement is executed on database objects, such as schemas. Equivalent to the [Audit Database Object Management Event Class](../../Topics/TopicNameNotContainA/Audit-Database-Object-Management-Event-Class.md).|  
|DATABASE_OBJECT_OWNERSHIP_CHANGE_GROUP|This event is raised when a change of owner for objects within database scope occurs. Equivalent to the [Audit Database Object Take Ownership Event Class](../../Topics/TopicNameNotContainA/Audit-Database-Object-Take-Ownership-Event-Class.md).|  
|DATABASE_OBJECT_PERMISSION_CHANGE_GROUP|This event is raised when a GRANT, REVOKE, or DENY has been issued for database objects, such as assemblies and schemas. Equivalent to the [Audit Database Object GDR Event Class](../../Topics/TopicNameNotContainA/Audit-Database-Object-GDR-Event-Class.md).|  
|DATABASE_OPERATION_GROUP|This event is raised when operations in a database, such as checkpoint or subscribe query notification, occur. Equivalent to the [Audit Database Operation Event Class](../../Topics/TopicNameNotContainA/Audit-Database-Operation-Event-Class.md).|  
|DATABASE_OWNERSHIP_CHANGE_GROUP|This event is raised when you use the ALTER AUTHORIZATION statement to change the owner of a database, and the permissions that are required to do that are checked. Equivalent to the [Audit Change Database Owner Event Class](../../Topics/TopicNameNotContainA/Audit-Change-Database-Owner-Event-Class.md).|  
|DATABASE_PERMISSION_CHANGE_GROUP|This event is raised whenever a GRANT, REVOKE, or DENY is issued for a statement permission by any user in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] for database-only events such as granting permissions on a database. Equivalent to the [Audit Database Scope GDR Event Class](../../Topics/TopicNameNotContainA/Audit-Database-Scope-GDR-Event-Class.md).|  
|DATABASE_PRINCIPAL_CHANGE_GROUP|This event is raised when principals, such as users, are created, altered, or dropped from a database. Equivalent to the [Audit Database Principal Management Event Class](../../Topics/TopicNameNotContainA/Audit-Database-Principal-Management-Event-Class.md). Also equivalent to the [Audit Add DB User Event Class](../../Topics/TopicNameNotContainA/Audit-Add-DB-User-Event-Class.md), which occurs on deprecated sp_grantdbaccess, sp_revokedbaccess, sp_adduser, and sp_dropuser stored procedures.<br /><br /> This event is raised whenever a database role is added to or removed using deprecated sp_addrole and sp_droprole stored procedures. Equivalent to the [Audit Add Role Event Class](../../Topics/TopicNameNotContainA/Audit-Add-Role-Event-Class.md).|  
|DATABASE_PRINCIPAL_IMPERSONATION_GROUP|This event is raised when there is an impersonation within database scope such as EXECUTE AS <user\>. Equivalent to the [Audit Database Principal Impersonation Event Class](../../Topics/TopicNameNotContainA/Audit-Database-Principal-Impersonation-Event-Class.md).|  
|DATABASE_ROLE_MEMBER_CHANGE_GROUP|This event is raised whenever a login is added to or removed from a database role. This event class is used with the sp_addrolemember, sp_changegroup, and sp_droprolemember stored procedures.Equivalent to the [Audit Add Member to DB Role Event Class](../../Topics/TopicNameNotContainA/Audit-Add-Member-to-DB-Role-Event-Class.md)|  
|DBCC_GROUP|This event is raised whenever a principal issues any DBCC command. Equivalent to the [Audit DBCC Event Class](../../Topics/TopicNameNotContainA/Audit-DBCC-Event-Class.md).|  
|FAILED_DATABASE_AUTHENTICATION_GROUP|Indicates that a principal tried to log on to a contained database and failed. Events in this class are raised by new connections or by connections that are reused from a connection pool. This event is raised.|  
|SCHEMA_OBJECT_ACCESS_GROUP|This event is raised whenever an object permission has been used in the schema. Equivalent to the [Audit Schema Object Access Event Class](../../Topics/TopicNameNotContainA/Audit-Schema-Object-Access-Event-Class.md).|  
|SCHEMA_OBJECT_CHANGE_GROUP|This event is raised when a CREATE, ALTER, or DROP operation is performed on a schema. Equivalent to the [Audit Schema Object Management Event Class](../../Topics/TopicNameNotContainA/Audit-Schema-Object-Management-Event-Class.md).<br /><br /> This event is raised on schema objects. Equivalent to the [Audit Object Derived Permission Event Class](../../Topics/TopicNameNotContainA/Audit-Object-Derived-Permission-Event-Class.md). Also equivalent to the [Audit Statement Permission Event Class](../../Topics/TopicNameNotContainA/Audit-Statement-Permission-Event-Class.md).|  
|SCHEMA_OBJECT_OWNERSHIP_CHANGE_GROUP|This event is raised when the permissions to change the owner of schema object such as a table, procedure, or function is checked. This occurs when the ALTER AUTHORIZATION statement is used to assign an owner to an object. Equivalent to the [Audit Schema Object Take Ownership Event Class](../../Topics/TopicNameNotContainA/Audit-Schema-Object-Take-Ownership-Event-Class.md).|  
|SCHEMA_OBJECT_PERMISSION_CHANGE_GROUP|This event is raised whenever a grant, deny, or revoke is issued for a schema object. Equivalent to the [Audit Schema Object GDR Event Class](../../Topics/TopicNameNotContainA/Audit-Schema-Object-GDR-Event-Class.md).|  
|SUCCESSFUL_DATABASE_AUTHENTICATION_GROUP|Indicates that a principal successfully logged in to a contained database. Equivalent to the Audit Successful Database Authentication Event Class.|  
|USER_CHANGE_PASSWORD_GROUP|This event is raised whenever the password of a contained database user is changed by using the ALTER USER statement.|  
|USER_DEFINED_AUDIT_GROUP|This group monitors events raised by using [sp_audit_write (Transact-SQL)](assetId:///4c523848-1ce6-49ad-92b3-e0e90f24f1c2).|  
  
## Database-Level Audit Actions  
 Database-level actions support the auditing of specific actions directly on database schema and schema objects, such as Tables, Views, Stored Procedures, Functions, Extended Stored Procedures, Queues, Synonyms. Types, XML Schema Collection, Database, and Schema are not audited. The audit of schema objects may be configured on Schema and Database, which means that events on all schema objects contained by the specified schema or database will be audited. The following table describes database-level audit actions.  
  
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
 Database-level audit actions do not apply to Columns.  
  
 When the query processor parameterizes the query, the parameter can appear in the audit event log instead of the column values of the query.  
  
## Audit-Level Audit Action Groups  
 You can also audit the actions in the auditing process. This can be in the server scope or the database scope. In the database scope, it only occurs for database audit specifications. The following table describes audit-level audit action groups.  
  
|Action group name|Description|  
|-----------------------|-----------------|  
|AUDIT_ CHANGE_GROUP|This event is raised whenever one of the following commands are issued:<br /><br /> CREATE SERVER AUDIT<br /><br /> ALTER SERVER AUDIT<br /><br /> DROP SERVER AUDIT<br /><br /> CREATE SERVER AUDIT SPECIFICATION<br /><br /> ALTER SERVER AUDIT SPECIFICATION<br /><br /> DROP SERVER AUDIT SPECIFICATION<br /><br /> CREATE DATABASE AUDIT SPECIFICATION<br /><br /> ALTER DATABASE AUDIT SPECIFICATION<br /><br /> DROP DATABASE AUDIT SPECIFICATION|  
  
## Related Content  
 [Create a Server Audit and Server Audit Specification](../../Topics/TopicNameContainA/Create-a-Server-Audit-and-Server-Audit-Specification.md)  
  
 [Create a Server Audit and Database Audit Specification](../../Topics/TopicNameContainA/Create-a-Server-Audit-and-Database-Audit-Specification.md)  
  
 [CREATE SERVER AUDIT (Transact-SQL)](assetId:///1c321680-562e-41f1-8eb1-e7fa5ae45cc5)  
  
 [ALTER SERVER AUDIT (Transact-SQL)](assetId:///63426d31-7a5c-4378-aa9e-afcf4f64ceb3)  
  
 [DROP SERVER AUDIT (Transact-SQL)](assetId:///faace8a3-daa9-4208-a2cd-4249eb32175c)  
  
 [CREATE SERVER AUDIT SPECIFICATION (Transact-SQL)](assetId:///db77fa77-fedb-40ac-83e6-06343063e518)  
  
 [ALTER SERVER AUDIT SPECIFICATION (Transact-SQL)](assetId:///9cac288b-940e-4c16-88d6-de06aeed2b47)  
  
 [DROP SERVER AUDIT SPECIFICATION (Transact-SQL)](assetId:///76635b80-5c05-4d01-a4e2-8277cd09251b)  
  
 [CREATE DATABASE AUDIT SPECIFICATION (Transact-SQL)](assetId:///0544da48-0ca3-4a01-ba4c-940e23dc315b)  
  
 [ALTER DATABASE AUDIT SPECIFICATION (Transact-SQL)](assetId:///85f4e7e6-a330-4de0-9048-64f386ccc314)  
  
 [DROP DATABASE AUDIT SPECIFICATION (Transact-SQL)](assetId:///3c387c6e-9a67-4daa-b64a-c87f6b3c9c4f)  
  
 [ALTER AUTHORIZATION (Transact-SQL)](assetId:///8c805ae2-91ed-4133-96f6-9835c908f373)  
  
 [fn_get_audit_file (Transact-SQL)](assetId:///d6a78d14-bb1f-4987-b7b6-579ddd4167f5)  
  
 [sys.server_audits (Transact-SQL)](assetId:///c2c4a000-1127-46a8-b1e9-947fd1136e1e)  
  
 [sys.server_file_audits (Transact-SQL)](assetId:///553288a0-be57-4d79-ae53-b7cbd065e127)  
  
 [sys.server_audit_specifications (Transact-SQL)](assetId:///fa496c6c-2a54-4fda-a238-db490c6b3afd)  
  
 [sys.server_audit_specifications_details (Transact-SQL)](assetId:///792724dc-402e-4b17-9f2c-029d910bf88e)  
  
 [sys.database_ audit_specifications (Transact-SQL)](assetId:///bf80e5c6-0588-4eb7-86ff-aa7c73461335)  
  
 [sys.database_audit_specification_details (Transact-SQL)](assetId:///03fc60a9-1696-4109-b15e-a50046310859)  
  
 [sys.dm_server_audit_status](assetId:///4aa32d54-2ae1-437e-bbaa-7f1df1404b44)  
  
 [sys.dm_audit_actions](assetId:///b987c2b9-998a-4a5f-a82d-280dc6963cbe)  
  
 [sys.dm_audit_class_type_map](assetId:///e10b5431-1bb0-47ca-8fd0-c04bd73a4410)