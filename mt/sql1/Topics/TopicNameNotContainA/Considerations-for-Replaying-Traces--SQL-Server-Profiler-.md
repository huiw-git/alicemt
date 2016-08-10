---
title: "Considerations for Replaying Traces (SQL Server Profiler)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 73fa339f-b71a-4be4-97ca-d4ae84c8b90b
caps.latest.revision: 22
caps.handback.revision: 0
manager: jhubbard
---
# Considerations for Replaying Traces (SQL Server Profiler)
[!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)] cannot replay the following kinds of traces:  
  
-   Traces that contain transactional replication and other transaction log activity. These events are skipped. Other types of replication do not mark the transaction log so they are not affected.  
  
-   Traces that contain operations that involve globally unique identifiers (GUID). These events will be skipped.  
  
-   Traces that contain operations on **text**, **ntext**, and **image** columns involving the **bcp** utility, the BULK INSERT, READTEXT, WRITETEXT, and UPDATETEXT statements, and full-text operations. These events are skipped.  
  
-   Traces that contain session binding: **sp_getbindtoken** and **sp_bindsession** system stored procedures. These events are skipped.  
  
> [!NOTE]  
>  If you do not use the preconfigured replay template (**TSQL_Replay**), and do not capture all required data, [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)] does not replay the trace. For more information, see [Replay Requirements](../../Topics/TopicNameNotContainA/Replay-Requirements.md).  
  
 For information about what permissions are required to replay a trace, see [Permissions Required to Run SQL Server Profiler](../../Topics/TopicNameNotContainA/Permissions-Required-to-Run-SQL-Server-Profiler.md).  
  
## See Also  
 [bcp Utility](../../Topics/TopicNameNotContainA/bcp-Utility.md)   
 [SQL Server Event Class Reference](../../Topics/TopicNameNotContainA/SQL-Server-Event-Class-Reference.md)   
 [sp_getbindtoken (Transact-SQL)](assetId:///5db87d77-85fa-45a3-a23a-3ea500f9a5ac)   
 [sp_bindsession (Transact-SQL)](assetId:///1436fe21-ad00-4a98-aca1-1451a5e571d2)   
 [BULK INSERT (Transact-SQL)](assetId:///be3984e1-5ab3-4226-a539-a9f58e1e01e2)   
 [READTEXT (Transact-SQL)](assetId:///91b69853-1381-4306-8343-afdb73105738)   
 [WRITETEXT (Transact-SQL)](assetId:///80c252fd-a8b8-4a2e-888a-059081ed4109)   
 [UPDATETEXT (Transact-SQL)](assetId:///d73c28ee-3972-4afd-af8d-ebbbd9e50793)