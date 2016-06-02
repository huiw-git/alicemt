---
title: SQL Server, SQL Errors Object
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
---
# SQL Server, SQL Errors Object
  The **SQLServer:SQL Errors** object in Microsoft [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provides counters to monitor **SQL Errors**.  
  
 This table describes the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] **SQL Errors** counters.  
  
|SQL Server SQL Errors counters|Description|  
|------------------------------------|-----------------|  
|**Errors\/sec**|Number of errors\/sec.|  
  
 Each counter in the object contains the following instances:  
  
|Item|Definition|  
|----------|----------------|  
|**\_Total**|Information for all errors.|  
|**DB Offline Errors**|Tracks severe errors that cause [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to take the current database offline.|  
|**Info Errors**|Information related to error messages that provide information to users but do not cause errors.|  
|**Kill Connection Errors**|Tracks severe errors that cause [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to kill the current connection.|  
|**User Errors**|Information about user errors.|  
  
## See Also  
 [Monitor Resource Usage &#40;System Monitor&#41;](../Topic/Monitor%20Resource%20Usage%20\(System%20Monitor\).md)  
  
  