---
title: "SQL Server Audit Records"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7a291015-df15-44fe-8d53-c6d90a157118
caps.latest.revision: 20
caps.handback.revision: 0
manager: jhubbard
---
# SQL Server Audit Records
The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Audit feature enables you to audit server-level and database-level groups of events and events. For more information, see [SQL Server Audit (Database Engine)](../../Topics/TopicNameNotContainA/SQL-Server-Audit--Database-Engine-.md). [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
 Audits consist of zero or more audit action items, which are recorded to an audit *target*. The audit target can be a binary file, the Windows Application event log or the Windows Security event log. The records sent to the target can contain the elements described in the following table.  
  
|Column name|Description|Type|Always available|  
|-----------------|-----------------|----------|----------------------|  
|**event_time**|Date/time when the auditable action is fired.|**datetime2**|Yes|  
|**sequence_no**|Tracks the sequence of records within a single audit record that was too large to fit in the write buffer for audits.|**int**|Yes|  
|**action_id**|ID of the action<br /><br /> Tip: To use **action_id** as a predicate it must be converted from a character string to a numeric value. For more information, see [Filter SQL Server Audit on action_id / class_type predicate](http://blogs.msdn.com/b/sqlsecurity/archive/2012/10/03/filter-sql-server-audit-on-action-id-class-type-predicate.aspx).|**varchar(4)**|Yes|  
|**succeeded**|Indicates if the action that triggered the event succeeded|**bit** – 1 = Success, 0 = Fail|Yes|  
|**permission_bitmask**|When applicable, shows the permissions that were granted, denied, or revoked|**bigint**|No|  
|**is_column_permission**|Flag indicating a column level permission|**bit** – 1 = True, 0 = False|No|  
|**session_id**|ID of the session on which the event occurred.|**int**|Yes|  
|**server_principal_id**|ID of the login context that the action is performed in.|**int**|Yes|  
|**database_principal_id**|ID of the database user context that the action is performed in.|**int**|No|  
|**object_ id**|The primary ID of the entity on which the audit occurred. This includes:<br /><br /> server objects<br /><br /> databases<br /><br /> database objects<br /><br /> schema objects|**int**|No|  
|**target_server_principal_id**|Server principal that the auditable action applies to.|**int**|Yes|  
|**target_database_principal_id**|Database principal that the auditable action applies to.|**int**|No|  
|**class_type**|Type of auditable entity that the audit occurs on.|**varchar(2)**|Yes|  
|**session_server_principal_name**|Server principal for the session.|**sysname**|Yes|  
|**server_principal_name**|Current login.|**sysname**|Yes|  
|**server_principal_sid**|Current login SID.|**varbinary**|Yes|  
|**database_principal_name**|Current user.|**sysname**|No|  
|**target_server_principal_name**|Target login of the action.|**sysname**|No|  
|**target_server_principal_sid**|SID of the target login.|**varbinary**|No|  
|**target_database_principal_name**|Target user of the action.|**sysname**|No|  
|**server_instance_name**|Name of the server instance where the audit occurred. Uses the standard machine\instance format.|**nvarchar(120)**|Yes|  
|**database_name**|The database context in which the action occurred.|**sysname**|No|  
|**schema_name**|The schema context in which the action occurred.|**sysname**|No|  
|**object_name**|The name of the entity on which the audit occurred. This includes:<br /><br /> server objects<br /><br /> databases<br /><br /> database objects<br /><br /> schema objects<br /><br /> TSQL statement (if any)|**sysname**|No|  
|**statement**|TSQL statement (if any)|**nvarchar(4000)**|No|  
|**additional_information**|Any additional information about the event, stored as XML.|**nvarchar(4000)**|No|  
  
## Remarks  
 Some actions do not populate a column's value because it might be non-applicable to the action.  
  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Audit stores 4000 characters of data for character fields in an audit record. When the **additional_information** and **statement** values returned from an auditable action return more than 4000 characters, the **sequence_no** column is used to write multiple records into the audit report for a single audit action to record this data. The process is as follows:  
  
-   The **statement** column is divided into 4000 characters.  
  
-   [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Audit writes as the first row for the audit record with the partial data. All the other fields are duplicated in each row.  
  
-   The **sequence_no** value is incremented.  
  
-   This process is repeated until all the data is recorded.  
  
 You can connect the data by reading the rows sequentially using the **sequence_no** value, and the **event_Time**, **action_id** and **session_id** columns to identify the action.  
  
## Related Content  
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