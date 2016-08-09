---
title: "SQL Server Audit (Database Engine)"
ms.custom: na
ms.date: 2016-04-05
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0c1fca2e-f22b-4fe8-806f-c87806664f00
caps.latest.revision: 58
manager: jhubbard
---
# SQL Server Audit (Database Engine)
*Auditing* an instance of the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)] or an individual database involves tracking and logging events that occur on the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)]. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] audit lets you create server audits, which can contain server audit specifications for server level events, and database audit specifications for database level events. Audited events can be written to the event logs or to audit files.  
  
 There are several levels of auditing for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], depending on government or standards requirements for your installation. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Audit provides the tools and processes you must have to enable, store, and view audits on various server and database objects.  
  
 You can record server audit action groups per-instance, and either database audit action groups or database audit actions per database. The audit event will occur every time that the auditable action is encountered.  
  
 All editions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] support server level audits. Database level auditing is limited to Enterprise, Developer, and Evaluation editions. For more information, see [Features Supported by the Editions of SQL Server 2016](../../Topics/TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md).  
  
> [!NOTE]  
>  This     topic applies to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  For [!INCLUDE[ssSDS](../../Topics/TopicNameContainA/tokens/ssSDS_md.md)], see [Get started with SQL database auditing](https://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/).  
  
## SQL Server Audit Components  
 An *audit* is the combination of several elements into a single package for a specific group of server actions or database actions. The components of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] audit combine to produce an output that is called an audit, just as a report definition combined with graphics and data elements produces a report.  
  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] audit uses *Extended Events* to help create an audit. For more information about Extended Events, see [Extended Events](../../Topics/TopicNameNotContainA/Extended-Events.md).  
  
### SQL Server Audit  
 The *SQL Server Audit* object collects a single instance of server or database-level actions and groups of actions to monitor. The audit is at the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance level. You can have multiple audits per [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance.  
  
 When you define an audit, you specify the location for the output of the results. This is the audit destination. The audit is created in a *disabled* state, and does not automatically audit any actions. After the audit is enabled, the audit destination receives data from the audit.  
  
### Server Audit Specification  
 The *Server Audit Specification* object belongs to an audit. You can create one server audit specification per audit, because both are created at the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance scope.  
  
 The server audit specification collects many server-level action groups raised by the Extended Events feature. You can include *audit action groups* in a server audit specification. Audit action groups are predefined groups of actions, which are atomic events occurring in the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)]. These actions are sent to the audit, which records them in the target.  
  
 Server-level audit action groups are described in the topic [SQL Server Audit Action Groups and Actions](../../Topics/TopicNameNotContainA/SQL-Server-Audit-Action-Groups-and-Actions.md).  
  
### Database Audit Specification  
 The *Database Audit Specification* object also belongs to a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] audit. You can create one database audit specification per [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] database per audit.  
  
 The database audit specification collects database-level audit actions raised by the Extended Events feature. You can add either audit action groups or audit events to a database audit specification. *Audit events* are the atomic actions that can be audited by the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] engine. *Audit action groups* are predefined groups of actions. Both are at the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] database scope. These actions are sent to the audit, which records them in the target. Do not include server-scoped objects, such as the system views, in a user database audit specification.  
  
 Database-level audit action groups and audit actions are described in the topic [SQL Server Audit Action Groups and Actions](../../Topics/TopicNameNotContainA/SQL-Server-Audit-Action-Groups-and-Actions.md).  
  
### Target  
 The results of an audit are sent to a target, which can be a file, the Windows Security event log, or the Windows Application event log. Logs must be reviewed and archived periodically to make sure that the target has sufficient space to write additional records.  
  
> [!IMPORTANT]  
>  Any authenticated user can read and write to the Windows Application event log. The Application event log requires lower permissions than the Windows Security event log and is less secure than the Windows Security event log.  
  
 Writing to the Windows Security log requires the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] service account to be added to the **Generate security audits** policy. By default, the Local System, Local Service, and Network Service are part of this policy. This setting can be configured by using the security policy snap-in (secpol.msc). Additionally, the **Audit object access** security policy must be enabled for both **Success** and **Failure**. This setting can be configured by using the security policy snap-in (secpol.msc). In [!INCLUDE[wiprlhext](../../Topics/TopicNameContainA/tokens/wiprlhext_md.md)] or Windows Server 2008, you can set the more granular **application generated** policy from the command line by using the audit policy program (**AuditPol.exe)**. For more information about the steps to enable writing to the Windows Security log, see [Write SQL Server Audit Events to the Security Log](../../Topics/TopicNameNotContainA/Write-SQL-Server-Audit-Events-to-the-Security-Log.md). For more information about the Auditpol.exe program, see Knowledge Base article 921469, [How to use Group Policy to configure detailed security auditing](http://support.microsoft.com/kb/921469/). The Windows event logs are global to the Windows operating system. For more information about the Windows event logs, see [Event Viewer Overview](http://go.microsoft.com/fwlink/?LinkId=101455). If you need more precise permissions on the audit, use the binary file target.  
  
 When you are saving audit information to a file, to help prevent tampering, you can restrict access to the file location in the following ways:  
  
-   The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Service Account must have both Read and Write permission.  
  
-   Audit Administrators typically require Read and Write permission. This assumes that the Audit Administrators are Windows accounts for administration of audit files, such as: copying them to different shares, backing them up, and so on.  
  
-   Audit Readers that are authorized to read audit files must have Read permission.  
  
 Even when the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] is writing to a file, other Windows users can read the audit file if they have permission. The [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] does not take an exclusive lock that prevents read operations.  
  
 Because the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] can access the file, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] logins that have CONTROL SERVER permission can use the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] to access the audit files. To record any user that is reading the audit file, define an audit on master.sys.fn_get_audit_file. This records the logins with CONTROL SERVER permission that have accessed the audit file through [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
 If an Audit Administrator copies the file to a different location (for archive purposes, and so on), the ACLs on the new location should be reduced to the following permissions:  
  
-   Audit Administrator – Read / Write  
  
-   Audit Reader – Read  
  
 We recommend that you generate audit reports from a separate instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], such as an instance of [!INCLUDE[ssExpress](../../Topics/TopicNameContainA/tokens/ssExpress_md.md)], to which only Audit Administrators or Audit Readers have access. By using a separate instance of the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] for reporting, you can help prevent unauthorized users from obtaining access to the audit record.  
  
 You can offer additional protection against unauthorized access by encrypting the folder in which the audit file is stored by using Windows BitLocker Drive Encryption or Windows Encrypting File System.  
  
 For more information about the audit records that are written to the target, see [SQL Server Audit Records](../../Topics/TopicNameNotContainA/SQL-Server-Audit-Records.md).  
  
## Overview of Using SQL Server Audit  
 You can use [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] to define an audit. After the audit is created and enabled, the target will receive entries.  
  
 You can read the Windows event logs by using the **Event Viewer** utility in Windows. For file targets, you can use either the **Log File Viewer** in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or the [fn_get_audit_file](assetId:///d6a78d14-bb1f-4987-b7b6-579ddd4167f5) function to read the target file.  
  
 The general process for creating and using an audit is as follows.  
  
1.  Create an audit and define the target.  
  
2.  Create either a server audit specification or database audit specification that maps to the audit. Enable the audit specification.  
  
3.  Enable the audit.  
  
4.  Read the audit events by using the Windows **Event Viewer**, **Log File Viewe**r, or the fn_get_audit_file function.  
  
 For more information, see [Create a Server Audit and Server Audit Specification](../../Topics/TopicNameContainA/Create-a-Server-Audit-and-Server-Audit-Specification.md) and [Create a Server Audit and Database Audit Specification](../../Topics/TopicNameContainA/Create-a-Server-Audit-and-Database-Audit-Specification.md).  
  
## Considerations  
 In the case of a failure during audit initiation, the server will not start. In this case, the server can be started by using the **–f** option at the command line.  
  
 When an audit failure causes the server to shut down or not to start because ON_FAILURE=SHUTDOWN is specified for the audit, the MSG_AUDIT_FORCED_SHUTDOWN event will be written to the log. Because the shutdown will occur on the first encounter of this setting, the event will be written one time. This event is written after the failure message for the audit causing the shutdown. An administrator can bypass audit-induced shutdowns by starting [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] in Single User mode using the **–m** flag. If you start in Single User mode, you will downgrade any audit where ON_FAILURE=SHUTDOWN is specified to run in that session as ON_FAILURE=CONTINUE. When [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is started by using the **–m** flag, the MSG_AUDIT_SHUTDOWN_BYPASSED message will be written to the error log.  
  
 For more information about service startup options, see [Database Engine Service Startup Options](../../Topics/TopicNameNotContainA/Database-Engine-Service-Startup-Options.md).  
  
### Attaching a Database with an Audit Defined  
 Attaching a database that has an audit specification and specifies a GUID that does not exist on the server will cause an *orphaned* audit specification. Because an audit with a matching GUID does not exist on the server instance, no audit events will be recorded. To correct this situation, use the ALTER DATABASE AUDIT SPECIFICATION command to connect the orphaned audit specification to an existing server audit. Or, use the CREATE SERVER AUDIT command to create a new server audit with the specified GUID.  
  
 You can attach a database that has an audit specification defined on it to another edition of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] that does not support [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] audit, such as [!INCLUDE[ssExpress](../../Topics/TopicNameContainA/tokens/ssExpress_md.md)] but it will not record audit events.  
  
### Database Mirroring and SQL Server Audit  
 A database that has a database audit specification defined and that uses database mirroring will include the database audit specification. To work correctly on the mirrored SQL instance, the following items must be configured:  
  
-   The mirror server must have an audit with the same GUID to enable the database audit specification to write audit records. This can be configured by using the command CREATE AUDIT WITH GUID**=***<GUID from source Server Audit*>.  
  
-   For binary file targets, the mirror server service account must have appropriate permissions to the location where the audit trail is being written.  
  
-   For Windows event log targets, the security policy on the computer where the mirror server is located must allow for service account access to the security or application event log.  
  
### Auditing Administrators  
 Members of the **sysadmin** fixed server role are identified as the **dbo** user in each database. To audit actions of the administrators, audit the actions of the **dbo** user.  
  
## Creating and Managing Audits with Transact-SQL  
 You can use DDL statements, dynamic management views and functions, and catalog views to implement all aspects of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Audit.  
  
### Data Definition Language Statements  
 You can use the following DDL statements to create, alter, and drop audit specifications:  
  
|||  
|-|-|  
|[ALTER AUTHORIZATION](assetId:///8c805ae2-91ed-4133-96f6-9835c908f373)|[CREATE SERVER AUDIT](assetId:///1c321680-562e-41f1-8eb1-e7fa5ae45cc5)|  
|[ALTER DATABASE AUDIT SPECIFICATION](assetId:///85f4e7e6-a330-4de0-9048-64f386ccc314)|[CREATE SERVER AUDIT SPECIFICATION](assetId:///db77fa77-fedb-40ac-83e6-06343063e518)|  
|[ALTER SERVER AUDIT](assetId:///63426d31-7a5c-4378-aa9e-afcf4f64ceb3)|[DROP DATABASE AUDIT SPECIFICATION](assetId:///3c387c6e-9a67-4daa-b64a-c87f6b3c9c4f)|  
|[ALTER SERVER AUDIT SPECIFICATION](assetId:///9cac288b-940e-4c16-88d6-de06aeed2b47)|[DROP SERVER AUDIT](assetId:///faace8a3-daa9-4208-a2cd-4249eb32175c)|  
|[CREATE DATABASE AUDIT SPECIFICATION](assetId:///0544da48-0ca3-4a01-ba4c-940e23dc315b)|[DROP SERVER AUDIT SPECIFICATION](assetId:///76635b80-5c05-4d01-a4e2-8277cd09251b)|  
  
### Dynamic Views and Functions  
 The following table lists the dynamic views and function that you can use for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Auditing.  
  
|Dynamic views and functions|Description|  
|---------------------------------|-----------------|  
|[sys.dm_audit_actions](assetId:///b987c2b9-998a-4a5f-a82d-280dc6963cbe)|Returns a row for every audit action that can be reported in the audit log and every audit action group that can be configured as part of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Audit.|  
|[sys.dm_server_audit_status](assetId:///4aa32d54-2ae1-437e-bbaa-7f1df1404b44)|Provides information about the current state of the audit.|  
|[sys.dm_audit_class_type_map](assetId:///e10b5431-1bb0-47ca-8fd0-c04bd73a4410)|Returns a table that maps the class_type field in the audit log to the class_desc field in sys.dm_audit_actions.|  
|[fn_get_audit_file](assetId:///d6a78d14-bb1f-4987-b7b6-579ddd4167f5)|Returns information from an audit file created by a server audit.|  
  
### Catalog Views  
 The following table lists the catalog views that you can use for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] auditing.  
  
|Catalog views|Description|  
|-------------------|-----------------|  
|[sys.database_ audit_specifications](assetId:///bf80e5c6-0588-4eb7-86ff-aa7c73461335)|Contains information about the database audit specifications in a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] audit on a server instance.|  
|[sys.database_audit_specification_details](assetId:///03fc60a9-1696-4109-b15e-a50046310859)|Contains information about the database audit specifications in a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] audit on a server instance for all databases.|  
|[sys.server_audits](assetId:///c2c4a000-1127-46a8-b1e9-947fd1136e1e)|Contains one row for each [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] audit in a server instance.|  
|[sys.server_audit_specifications](assetId:///fa496c6c-2a54-4fda-a238-db490c6b3afd)|Contains information about the server audit specifications in a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] audit on a server instance.|  
|[sys.server_audit_specifications_details](assetId:///792724dc-402e-4b17-9f2c-029d910bf88e)|Contains information about the server audit specification details (actions) in a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] audit on a server instance.|  
|[sys.server_file_audits](assetId:///553288a0-be57-4d79-ae53-b7cbd065e127)|Contains stores extended information about the file audit type in a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] audit on a server instance.|  
  
## Permissions  
 Each feature and command for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Audit has individual permission requirements.  
  
 To create, alter, or drop a Server Audit or Server Audit Specification, server principals require the ALTER ANY SERVER AUDIT or the CONTROL SERVER permission. To create, alter, or drop a Database Audit Specification, database principals require the ALTER ANY DATABASE AUDIT permission or the ALTER or CONTROL permission on the database. In addition, principals must have permission to connect to the database, or ALTER ANY SERVER AUDIT or CONTROL SERVER permissions.  
  
 The VIEW ANY DEFINITION permission provides access to view the server level audit views and VIEW DEFINITION provides access to view the database level audit views. Denial of these permissions, overrides the ability to view the catalog views, even if the principal has the ALTER ANY SERVER AUDIT or ALTER ANY DATABASE AUDIT permissions.  
  
 For more information about how to grant rights and permissions, see [GRANT (Transact-SQL)](assetId:///a760c16a-4d2d-43f2-be81-ae9315f38185).  
  
> [!CAUTION]  
>  Principals in the sysadmin role can tamper with any audit component and those in the db_owner role can tamper with audit specifications in a database. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Audit will validate that a logon that creates or alters an audit specification has at least the ALTER ANY DATABASE AUDIT permission. However, it does no validation when you attach a database. You should assume all Database Audit Specifications are only as trustworthy as those principals in the sysadmin or db_owner role.  
  
## Related Tasks  
 [Create a Server Audit and Server Audit Specification](../../Topics/TopicNameContainA/Create-a-Server-Audit-and-Server-Audit-Specification.md)  
  
 [Create a Server Audit and Database Audit Specification](../../Topics/TopicNameContainA/Create-a-Server-Audit-and-Database-Audit-Specification.md)  
  
 [View a SQL Server Audit Log](../../Topics/TopicNameContainA/View-a-SQL-Server-Audit-Log.md)  
  
 [Write SQL Server Audit Events to the Security Log](../../Topics/TopicNameNotContainA/Write-SQL-Server-Audit-Events-to-the-Security-Log.md)  
  
## Topics Closely Related to Auditing  
 [Server Properties (Security Page)](../../Topics/TopicNameNotContainA/Server-Properties--Security-Page-.md)  
 Explains how to turn on login auditing for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. The audit records are stored in the Windows application log.  
  
 [c2 audit mode Server Configuration Option](../../Topics/TopicNameNotContainA/c2-audit-mode-Server-Configuration-Option.md)  
 Explains the C2 security compliance auditing mode in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
 [Security Audit Event Category (SQL Server Profiler)](../../Topics/TopicNameNotContainA/Security-Audit-Event-Category--SQL-Server-Profiler-.md)  
 Explains the audit events you can use in [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)]. For more information, see [SQL Server Profiler](../../Topics/TopicNameNotContainA/SQL-Server-Profiler.md).  
  
 [SQL Trace](../../Topics/TopicNameNotContainA/SQL-Trace.md)  
 Explains how SQL Trace can be used from within your own applications to create traces manually, instead of using [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Profiler.  
  
 [DDL Triggers](../../Topics/TopicNameNotContainA/DDL-Triggers.md)  
 Explains how you can use Data Definition Language (DDL) triggers to track changes to your databases.  
  
 [Microsoft TechNet: SQL Server TechCenter: SQL Server 2005 Security and Protection](http://go.microsoft.com/fwlink/?LinkId=101152)  
 Provides up-to-date information about [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] security.  
  
## See Also  
 [SQL Server Audit Action Groups and Actions](../../Topics/TopicNameNotContainA/SQL-Server-Audit-Action-Groups-and-Actions.md)   
 [SQL Server Audit Records](../../Topics/TopicNameNotContainA/SQL-Server-Audit-Records.md)