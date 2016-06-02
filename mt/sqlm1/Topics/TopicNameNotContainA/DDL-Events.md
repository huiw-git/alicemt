---
title: DDL Events
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-ddl
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 62ef24b4-3553-4aed-b62a-670980bae501
---
# DDL Events
  The following tables list the DDL events that can be used to fire a DDL trigger or event notification. Note that each event corresponds to a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement or stored procedure, with the statement syntax modified to include an underscore character \(\_\) between keywords.  
  
> [!IMPORTANT]  
>  System stored procedures that perform DDL\-like operations also fire DDL triggers and event notifications. Test your DDL triggers and event notifications to determine their responses to system stored procedures that are run. For example, the CREATE TYPE statement and **sp\_addtype** stored procedure will both fire a DDL trigger or event notification that is created on a CREATE\_TYPE event.  
  
## DDL Statements That Have Server or Database Scope  
 DDL triggers or event notifications can be created to fire in response to the following events when they occur in the database in which the trigger or event notification is created, or anywhere in the server instance.  
  
||||  
|-|-|-|  
|CREATE\_APPLICATION\_ROLE \(Applies to the CREATE APPLICATION ROLE statement and **sp\_addapprole**. If a new schema is created, this event also triggers a CREATE\_SCHEMA event.\)|ALTER\_APPLICATION\_ROLE \(Applies to the ALTER APPLICATION ROLE statement and **sp\_approlepassword**.\)|DROP\_APPLICATION\_ROLE \(Applies to the DROP APPLICATION ROLE statement and **sp\_dropapprole**.\)|  
|CREATE\_ASSEMBLY|ALTER\_ASSEMBLY|DROP\_ASSEMBLY|  
|CREATE\_ASYMMETRIC\_KEY|ALTER\_ASYMMETRIC\_KEY|DROP\_ASYMMETRIC\_KEY|  
|ALTER\_AUTHORIZATION|ALTER\_AUTHORIZATION\_DATABASE \(Applies to the ALTER AUTHORIZATION statement when ON DATABASE is specified, and **sp\_changedbowner**.\)||  
|CREATE\_BROKER\_PRIORITY|CREATE\_BROKER\_PRIORITY|CREATE\_BROKER\_PRIORITY|  
|CREATE\_CERTIFICATE|ALTER\_CERTIFICATE|DROP\_CERTIFICATE|  
|CREATE\_CONTRACT|DROP\_CONTRACT||  
|CREATE\_CREDENTIAL|ALTER\_CREDENTIAL|DROP\_CREDENTIAL|  
|GRANT\_DATABASE|DENY\_DATABASE|REVOKE\_DATABASE|  
|CREATE\_DATABASE\_AUDIT\_SPEFICIATION|ALTER\_DATABASE\_AUDIT\_SPEFICIATION|DENY\_DATABASE\_AUDIT\_SPEFICIATION|  
|CREATE\_DATABASE\_ENCRYPTION\_KEY|ALTER\_DATABASE\_ENCRYPTION\_KEY|DROP\_DATABASE\_ENCRYPTION\_KEY|  
|CREATE\_DEFAULT|DROP\_DEFAULT||  
|BIND\_DEFAULT \(Applies to **sp\_bindefault**.\)|UNBIND\_DEFAULT \(Applies to **sp\_unbindefault**.\)||  
|CREATE\_EVENT\_NOTIFICATION|DROP\_EVENT\_NOTIFICATION||  
|CREATE\_EXTENDED\_PROPERTY \(Applies to **sp\_addextendedproperty**.\)|ALTER\_EXTENDED\_PROPERTY \(Applies to **sp\_updateextendedproperty**.\)|DROP\_EXTENDED\_PROPERTY \(Applies to **sp\_dropextendedproperty**.\)|  
|CREATE\_FULLTEXT\_CATALOG \(Applies to the CREATE FULLTEXT CATALOG statement and **sp\_fulltextcatalog** when *create* is specified.\)|ALTER\_FULLTEXT\_CATALOG \(Applies to the ALTER FULLTEXT CATALOG statement, **sp\_fulltextcatalog** when *start\_incremental*, *start\_full*, *Stop*, or *Rebuild* is specified, and **sp\_fulltext\_database** when *enable* is specified.\)|DROP\_FULLTEXT\_CATALOG \(Applies to the DROP FULLTEXT CATALOG statement and **sp\_fulltextcatalog** when *drop* is specified.\)|  
|CREATE\_FULLTEXT\_INDEX \(Applies to the CREATE FULLTEXT INDEX statement and **sp\_fulltexttable** when *create* is specified.\)|ALTER\_FULLTEXT\_INDEX \(Applies to the ALTER FULLTEXT INDEX statement, **sp\_fulltextcatalog** when *start\_full*, *start\_incremental*, or *stop* is specified, **sp\_fulltext\_column**, and **sp\_fulltext\_table** when any action other than *create* or *drop* is specified.\)|DROP\_FULLTEXT\_INDEX \(Applies to the DROP FULLTEXT INDEX statement and **sp\_fulltexttable** when *drop* is specified.\)|  
|CREATE\_FULLTEXT\_STOPLIST|ALTER\_FULLTEXT\_STOPLIST|DROP\_FULLTEXT\_STOPLIST|  
|CREATE\_FUNCTION|ALTER\_FUNCTION|DROP\_FUNCTION|  
|CREATE\_INDEX|ALTER\_INDEX \(Applies to the ALTER INDEX statement and **sp\_indexoption**.\)|DROP\_INDEX|  
|CREATE\_MASTER\_KEY|ALTER\_MASTER\_KEY|DROP\_MASTER\_KEY|  
|CREATE\_MESSAGE\_TYPE|ALTER\_MESSAGE\_TYPE|DROP\_MESSAGE\_TYPE|  
|CREATE\_PARTITION\_FUNCTION|ALTER\_PARTITION\_FUNCTION|DROP\_PARTITION\_FUNCTION|  
|CREATE\_PARTITION\_SCHEME|ALTER\_PARTITION\_SCHEME|DROP\_PARTITION\_SCHEME|  
|CREATE\_PLAN\_GUIDE \(Applies to **sp\_create\_plan\_guide**.\)|ALTER\_PLAN\_GUIDE \(Applies to **sp\_control\_plan\_guide** when ENABLE, ENABLE ALL, DISABLE, or DISABLE ALL is specified.\)|DROP\_PLAN\_GUIDE \(Applies to **sp\_control\_plan\_guide** when DROP or DROP ALL is specified.\)|  
|CREATE\_PROCEDURE|ALTER\_PROCEDURE \(Applies to the ALTER PROCEDURE statement and **sp\_procoption**.\)|DROP\_PROCEDURE|  
|CREATE\_QUEUE|ALTER\_QUEUE|DROP\_QUEUE|  
|CREATE\_REMOTE\_SERVICE\_BINDING|ALTER\_REMOTE\_SERVICE\_BINDING|DROP\_REMOTE\_SERVICE\_BINDING|  
|CREATE\_SPATIAL\_INDEX|||  
|RENAME \(Applies to **sp\_rename**\)|||  
|CREATE\_ROLE \(Applies to the CREATE ROLE statement, **sp\_addrole**, and **sp\_addgroup**.\)|ALTER\_ROLE|DROP\_ROLE \(Applies to the DROP ROLE statement, **sp\_droprole**, and **sp\_dropgroup**.\)|  
|ADD\_ROLE\_MEMBER|DROP\_ROLE\_MEMBER||  
|CREATE\_ROUTE|ALTER\_ROUTE|DROP\_ROUTE|  
|CREATE\_RULE|DROP\_RULE||  
|BIND\_RULE \(Applies to **sp\_bindrule**.\)|UNBIND\_RULE \(Applies to **sp\_unbindrule**.\)||  
|CREATE\_SCHEMA \(Applies to the CREATE SCHEMA statement, **sp\_addrole**, **sp\_adduser**, **sp\_addgroup**, and **sp\_grantdbaccess**.\)|ALTER\_SCHEMA \(Applies to the ALTER SCHEMA statement and **sp\_changeobjectowner**.\)|DROP\_SCHEMA|  
|CREATE\_SEARCH\_PROPERTY\_LIST|ALTER\_SEARCH\_PROPERTY\_LIST|DROP\_SEARCH\_PROPERTY\_LIST|  
|CREATE\_SEQUENCE\_EVENTS|CREATE\_SEQUENCE\_EVENTS|CREATE\_SEQUENCE\_EVENTS|  
|CREATE\_SERVER\_ROLE|ALTER\_SERVER\_ROLE|DROP\_SERVER\_ROLE|  
|CREATE\_SERVICE|ALTER\_SERVICE|DROP\_SERVICE|  
|ALTER\_SERVICE\_MASTER\_KEY|BACKUP\_SERVICE\_MASTER\_KEY|RESTORE\_SERVICE\_MASTER\_KEY|  
|ADD\_SIGNATURE \(for signature operations on non\-schema scoped objects; database, assembly, trigger\)|DROP\_SIGNATURE||  
|ADD\_SIGNATURE\_SCHEMA\_OBJECT \(for schema scoped objects; stored procedures, functions\)|DROP\_SIGNATURE\_SCHEMA\_OBJECT||  
|CREATE\_SPATIAL\_INDEX|ALTER\_INDEX can be used for spatial indexes.|DROP\_INDEX can be used for spatial indexes.|  
|CREATE\_STATISTICS|DROP\_STATISTICS|UPDATE\_STATISTICS|  
|CREATE\_SYMMETRIC\_KEY|ALTER\_SYMMETRIC\_KEY|DROP\_SYMMETRIC\_KEY|  
|CREATE\_SYNONYM|DROP\_SYNONYM||  
|CREATE\_TABLE|ALTER\_TABLE \(Applies to the ALTER TABLE statement and **sp\_tableoption**.\)|DROP\_TABLE|  
|CREATE\_TRIGGER|ALTER\_TRIGGER \(Applies to the ALTER TRIGGER statement and **sp\_settriggerorder**.\)|DROP\_TRIGGER|  
|CREATE\_TYPE \(Applies to the CREATE TYPE statement and **sp\_addtype**.\)|DROP\_TYPE \(Applies to the DROP TYPE statement and **sp\_droptype**.\)||  
|CREATE\_USER \(Applies to the CREATE USER statement, **sp\_adduser**, and **sp\_grantdbaccess**.\)|ALTER\_USER \(Applies to ALTER USER statement and **sp\_change\_users\_login**.\)|DROP\_USER \(Applies to the DROP USER statement, **sp\_dropuser**, and **sp\_revokedbaccess**.\)|  
|CREATE\_VIEW|ALTER\_VIEW|DROP\_VIEW|  
|CREATE\_XML\_INDEX|ALTER\_INDEX can be used for XML indexes.|DROP\_INDEX can be used for XML indexes.|  
|CREATE\_XML\_SCHEMA\_COLLECTION|ALTER\_XML\_SCHEMA\_COLLECTION|DROP\_XML\_SCHEMA\_COLLECTION|  
  
## DDL Statements That Have Server Scope  
 DDL triggers or event notifications can be created to fire in response to the following events when they occur anywhere in the server instance.  
  
||||  
|-|-|-|  
|ALTER\_AUTHORIZATION\_SERVER|ALTER\_SERVER\_CONFIGURATION|ALTER\_INSTANCE \(Applies to **sp\_configure** and **sp\_addserver** when a local server instance is specified.\)|  
|CREATE\_AVAILABILITY\_GROUP|ALTER\_AVAILABILITY\_GROUP|DROP\_AVAILABILITY\_GROUP|  
|CREATE\_CREDENTIAL|ALTER\_CREDENTIAL|DROP\_CREDENTIAL|  
|CREATE\_CRYPTOGRAPHIC\_PROVIDER|ALTER\_CRYPTOGRAPHIC\_PROVIDER|DROP\_CRYPTOGRAPHIC\_PROVIDER|  
|CREATE\_DATABASE|ALTER\_DATABASE \(Applies to the ALTER DATABASE statement and **sp\_fulltext\_database**.\)|DROP\_DATABASE|  
|CREATE\_ENDPOINT|ALTER\_ENDPOINT|DROP\_ENDPOINT|  
|CREATE\_EVENT\_SESSION|ALTER\_EVENT\_SESSION|DROP\_EVENT\_SESSION|  
|CREATE\_EXTENDED\_PROCEDURE \(Applies to **sp\_addextendedproc**.\)|DROP\_EXTENDED\_PROCEDURE \(Applies to **sp\_dropextendedproc**.\)||  
|CREATE\_LINKED\_SERVER \(Applies to **sp\_addlinkedserver**.\)|ALTER\_LINKED\_SERVER \(Applies to **sp\_serveroption**.\)|DROP\_LINKED\_SERVER \(Applies to **sp\_dropserver** when a linked server is specified.\)|  
|CREATE\_LINKED\_SERVER\_LOGIN \(Applies to **sp\_addlinkedsrvlogin**.\)|DROP\_LINKED\_SERVER\_LOGIN \(Applies to **sp\_droplinkedsrvlogin**.\)||  
|CREATE\_LOGIN \(Applies to the CREATE LOGIN statement, **sp\_addlogin**, **sp\_grantlogin**, **xp\_grantlogin**, and **sp\_denylogin** when used on a nonexistent login that must be implicitly created.\)|ALTER\_LOGIN \(Applies to the ALTER LOGIN statement, **sp\_defaultdb**, **sp\_defaultlanguage**, **sp\_password**, and **sp\_change\_users\_login** when *Auto\_Fix* is specified.\)|DROP\_LOGIN \(Applies to the DROP LOGIN statement, **sp\_droplogin**, **sp\_revokelogin**, and **xp\_revokelogin**.\)|  
|CREATE\_MESSAGE \(Applies to **sp\_addmessage**.\)|ALTER\_MESSAGE \(Applies to **sp\_altermessage**.\)|DROP\_MESSAGE \(Applies to **sp\_dropmessage**.\)|  
|CREATE\_REMOTE\_SERVER \(Applies to **sp\_addserver**.\)|ALTER\_REMOTE\_SERVER \(Applies to **sp\_setnetname**.\)|DROP\_REMOTE\_SERVER \(Applies to **sp\_dropserver** when a remote server is specified.\)|  
|CREATE\_RESOURCE\_POOL|ALTER\_RESOURCE\_POOL|DROP\_RESOURCE\_POOL|  
|GRANT\_SERVER|DENY\_SERVER|REVOKE\_SERVER|  
|ADD\_SERVER\_ROLE\_MEMBER|DROP\_SERVER\_ROLE\_MEMBER||  
|CREATE\_SERVER\_AUDIT|ALTER\_SERVER\_AUDIT|DROP\_SERVER\_AUDIT|  
|CREATE\_SERVER\_AUDIT\_SPECIFICATION|ALTER\_SERVER\_AUDIT\_SPECIFICATION|DROP\_SERVER\_AUDIT\_SPECIFICATION|  
|CREATE\_WORKLOAD\_GROUP|CREATE\_WORKLOAD\_GROUP|CREATE\_WORKLOAD\_GROUP|  
  
## See Also  
 [DDL Triggers](../../Topics\TopicNameNotContainA/DDL-Triggers.md)   
 [Event Notifications](../../Topics\TopicNameNotContainA/Event-Notifications.md)   
 [DDL Event Groups](../../Topics\TopicNameNotContainA/DDL-Event-Groups.md)  
  
  