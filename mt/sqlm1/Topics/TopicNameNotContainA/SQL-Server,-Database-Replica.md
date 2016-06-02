---
title: SQL Server, Database Replica
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a5f6bdce-2b13-4924-aaeb-b50b57d624d8
---
# SQL Server, Database Replica
  The **SQLServer:Database Replica** performance object contains performance counters that report information about the secondary databases of an Always On availability group in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. This object is valid only on an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that hosts a secondary replica.  
  
|Counter Name|Description|View on…|  
|------------------|-----------------|--------------|  
|**File Bytes Received\/sec**|Amount of FILESTREAM data received by the secondary replica for the secondary database in the last second.|Secondary replica|  
|**Log Bytes Received\/sec**|Amount of log records received by the secondary replica for the database in the last second.|Secondary replica|  
|**Log remaining for undo**|The amount of log in kilobytes remaining to complete the undo phase.|Secondary replica|  
|**Log Send Queue**|Amount of log records in the log files of the primary database, in kilobytes, that has not yet been sent to the secondary replica. This value is sent to the secondary replica from the primary replica. Queue size does not include FILESTREAM files that are sent to a secondary.|Secondary replica|  
|**Mirrored Write Transaction\/sec**|Number of transactions that were written to the primary database and then waited to commit until the log was sent to the secondary database, in the last second.|Primary replica|  
|**Recovery Queue**|Amount of log records in the log files of the secondary replica that has not yet been redone.|Secondary replica|  
|**Redo blocked\/sec**|Number of times the redo thread is blocked on locks held by readers of the database.|Secondary replica|  
|**Redo Bytes Remaining**|The amount of log in kilobytes remaining to be redone to finish the reverting phase.|Secondary replica|  
|**Redone Bytes\/sec**|Amount of log records redone on the secondary database in the last second.|Secondary replica|  
|**Total Log requiring undo**|Total kilobytes of log that must be undone.|Secondary replica|  
|**Transaction Delay**|Delay in waiting for unterminated commit acknowledgement, in milliseconds.|Primary replica|  
  
## See Also  
 [Monitor Resource Usage &#40;System Monitor&#41;](../Topic/Monitor%20Resource%20Usage%20\(System%20Monitor\).md)   
 [SQL Server, Availability Replica](../../Topics\TopicNameNotContainA/SQL-Server,-Availability-Replica.md)   
 [SQL Server, Databases Object](../../Topics\TopicNameNotContainA/SQL-Server,-Databases-Object.md)   
 [AlwaysOn Availability Groups &#40;SQL Server&#41;](../Topic/AlwaysOn%20Availability%20Groups%20\(SQL%20Server\).md)  
  
  