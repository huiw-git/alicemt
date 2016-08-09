---
title: "Extended Events Tools"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d312a9ff-50ba-4721-baef-50bfd3169d38
caps.latest.revision: 20
caps.handback.revision: 0
manager: jhubbard
---
# Extended Events Tools
You can use the following tools to create and manage [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Extended Events sessions:  
  
-   Data Definition Language (DDL) statements. These enable you to create and modify an Extended Events session.  
  
-   Dynamic management views, catalog views and system tables. These enable you to obtain session data and metadata by using [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements. The system tables help you determine the existing Extended Events equivalents for SQL Trace event classes and columns.  
  
-   The **Extended Events** node of Object Explorer. This enables you to start, stop or delete a session, or to import and export session templates.  
  
-   The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] PowerShell provider. This is a powerful tool that you can use to create, alter, and manage Extended Events sessions. For more information, see [Use the PowerShell Provider for Extended Events](../../Topics/TopicNameNotContainA/Use-the-PowerShell-Provider-for-Extended-Events.md).  
  
-   [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)]. This enables you to create and execute the code samples that are provided in the Extended Events topics. For more information, see [Using Object Explorer](assetId:///469ea8e2-79b9-44c8-bb6f-f0e1c5dbf0f2).  
  
 In addition to sessions that you create, a default system health session exists on the server. The session collects system data that you can use to help troubleshoot performance issues. For more information, see [Use the system_health Session](../../Topics/TopicNameNotContainA/Use-the-system_health-Session.md).  
  
## DDL Statements  
 Use the following DDL statements to create, change, and drop an Extended Events session.  
  
|Name|Description|  
|----------|-----------------|  
|[CREATE EVENT SESSION (Transact-SQL)](assetId:///67683027-2b0f-47aa-b223-604731af8b4d)|Creates an Extended Event session object that identifies the source of the events, the event session targets, and the event session parameters.|  
|[ALTER EVENT SESSION (Transact-SQL)](assetId:///da006ac9-f914-4995-a2fb-25b5d971cd90)|Starts or stops an event session or changes an event session configuration.|  
|[DROP EVENT SESSION (Transact-SQL)](assetId:///92eabe4b-24e2-43b1-978c-31a199964b90)|Drops an event session.|  
  
## Catalog Views  
 Use the following catalog views to obtain the metadata that is created when you create an event session.  
  
|Name|Description|  
|----------|-----------------|  
|[sys.server_event_sessions](assetId:///796f3093-6a3e-4d67-8da6-b9810ae9ef5b)|Lists all event session definitions.|  
|[sys.server_event_session_actions](assetId:///1d8c604e-4361-4846-8661-14cfd1c44f63)|Returns a row for each action on each event of an event session.|  
|[sys.server_event_session_events](assetId:///75986e91-1fc7-4f14-98ac-4e90154a74db)|Returns a row for each event in an event session.|  
|[sys.server_event_session_fields](assetId:///7109f9fb-8a1f-432c-92d1-6f8af3e96af1)|Returns a row for each customizable column that was explicitly set on events and targets.|  
|[sys.server_event_session_targets](assetId:///dda4879d-57ae-4267-b410-1ef5c37404c7)|Returns a row for each event target for an event session.|  
  
## Dynamic Management Views  
 Use the following dynamic management views to obtain session metadata and session data. The metadata is obtained from the catalog views, and the session data is created when you start and run an event session.  
  
> [!NOTE]  
>  These views do not contain session data until a session starts.  
  
|Name|Description|  
|----------|-----------------|  
|[sys.dm_os_dispatcher_pools](assetId:///b9edbc83-c6bc-4753-9bb5-a454cfe7d6bf)|Returns information about session dispatcher pools.|  
|[sys.dm_xe_objects](assetId:///5d944b99-b097-491b-8cbd-b0e42b459ec0)|Returns a row for each object that is exposed by an event package.|  
|[sys.dm_xe_object_columns](assetId:///d96a14f3-4284-45ff-b1fe-4858e540a013)|Returns the schema information for all the objects.|  
|[sys.dm_xe_packages](assetId:///2e5ecbe9-3ea8-45e6-a161-e31671a03e1d)|Lists all the packages registered with the Extended Events engine.|  
|[sys.dm_xe_sessions](assetId:///defd6efb-9507-4247-a91f-dc6ff5841e17)|Returns information about an active Extended Events session.|  
|[sys.dm_xe_session_targets](assetId:///76fbc3e1-ad88-4a47-8bf1-471c3bee5ad8)|Returns information about session targets.|  
|[sys.dm_xe_session_events](assetId:///4f027b31-4e03-43a6-849d-1ba9d8d34ae8)|Returns information about session events.|  
|[sys.dm_xe_session_event_actions](assetId:///0c22a546-683e-4c84-ab97-1e9e95304b03)|Returns information about event session actions.|  
|[sys.dm_xe_map_values](assetId:///c0c5dd7e-9cee-47e2-b65a-88194c00aa1f)|Provides a mapping of internal numeric keys to human-readable text.|  
|[sys.dm_xe_session_object_columns](assetId:///e97f3307-2da6-4c54-b818-a474faec752e)|Shows the configuration values for objects that are bound to a session.|  
  
## System Tables  
 Use the following system tables to obtain information about the Extended Events equivalents for SQL Trace event classes and columns.  
  
|Name|Description|  
|----------|-----------------|  
|[trace_xe_event_map (Transact-SQL)](assetId:///537aa292-3540-47e8-be28-56dc01abc343)|Contains one row for each Extended Events event that is mapped to a SQL Trace event class.|  
|[trace_xe_action_map (Transact-SQL)](assetId:///208a1413-ce7f-4521-b765-d74723627302)|Contains one row for each Extended Events action that is mapped to a SQL Trace column ID.|  
  
## See Also  
 [Dynamic Management Views and Functions](assetId:///cf893ecb-0bf6-4cbf-ac00-8a1099e405b1)   
 [Catalog Views (Transact-SQL)](assetId:///13bccc2f-ed3c-4b58-abd0-ca8bf34a66b8)   
 [Extended Events Tables (Transact-SQL)](assetId:///6d52ff03-f5aa-4f0f-8c98-9b49dc76f94e)   
 [Use the system_health Session](../../Topics/TopicNameNotContainA/Use-the-system_health-Session.md)   
 [Use the PowerShell Provider for Extended Events](../../Topics/TopicNameNotContainA/Use-the-PowerShell-Provider-for-Extended-Events.md)