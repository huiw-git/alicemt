---
title: FT:Crawl Started Event Class
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2535b856-97e8-4fb2-8ba0-5d5446355fa6
---
# FT:Crawl Started Event Class
  The **FT:Crawl Started** event class indicates that a full\-text crawl \(population\) has started. Use this event class to check if a crawl request is actually being picked up by worker tasks.  
  
## FT: Crawl Started Event Class Data Columns  
  
|Data column name|Data type|Description|Column ID|Filterable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|ID of the database in which the full\-text crawl was started. Determine the value for a database by using the DB\_ID function.|3|Yes|  
|**EventClass**|**int**|Type of event \= 155.|27|No|  
|**EventSequence**|**int**|Sequence of a given event within the request.|51|No|  
|**IsSystem**|**int**|Indicates whether the event occurred on a system process or a user process. 1 \= system, 0 \= user.|60|Yes|  
|**ObjectID**|**int**|System\-assigned ID of the object. The full\-text crawl was started on the full\-text index on this object.|22|Yes|  
|**SessionLoginName**|**nvarchar**|Login name of the user who originated the session. For example, if you connect to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2. This column displays both [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows logins.|64|Yes|  
|**SPID**|**int**|ID of the session on which the event occurred.|12|Yes|  
|**StartTime**|**datetime**|Time at which the event started, if available.|14|Yes|  
|**TextData**|**ntext**|Full\-text crawl type. The value can be Full, Incremental, Manual, or Auto.|1|Yes|  
|**TransactionID**|**bigint**|System\-assigned ID of the transaction.|4|Yes|  
  
## See Also  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../Topic/sp_trace_setevent%20\(Transact-SQL\).md)  
  
  