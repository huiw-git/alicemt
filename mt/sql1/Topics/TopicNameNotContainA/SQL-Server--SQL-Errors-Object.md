---
title: "SQL Server, SQL Errors Object"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
caps.latest.revision: 15
caps.handback.revision: 0
manager: jhubbard
---
# SQL Server, SQL Errors Object
The **SQLServer:SQL Errors** object in Microsoft [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] provides counters to monitor **SQL Errors**.  
  
 This table describes the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] **SQL Errors** counters.  
  
|SQL Server SQL Errors counters|Description|  
|------------------------------------|-----------------|  
|**Errors/sec**|Number of errors/sec.|  
  
 Each counter in the object contains the following instances:  
  
|Item|Definition|  
|----------|----------------|  
|**_Total**|Information for all errors.|  
|**DB Offline Errors**|Tracks severe errors that cause [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] to take the current database offline.|  
|**Info Errors**|Information related to error messages that provide information to users but do not cause errors.|  
|**Kill Connection Errors**|Tracks severe errors that cause [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] to kill the current connection.|  
|**User Errors**|Information about user errors.|  
  
## See Also  
 [Monitor Resource Usage (System Monitor)](../../Topics/TopicNameNotContainA/Monitor-Resource-Usage--System-Monitor-.md)