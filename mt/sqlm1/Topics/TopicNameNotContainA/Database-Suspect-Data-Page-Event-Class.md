---
title: Database Suspect Data Page Event Class
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 098e1443-a8a0-425c-9311-0a479b1370ed
---
# Database Suspect Data Page Event Class
  The **Database Suspect Data Page** event class indicates when a page is added to the [suspect\_pages](../Topic/suspect_pages%20\(Transact-SQL\).md) table in [msdb](../../Topics\TopicNameNotContainA/msdb-Database.md). Include this event class in traces that are monitoring the occurrence of suspect pages.  
  
> [!NOTE]  
>  This event is issued asynchronously from the insertion of a corresponding row into the **suspect\_pages** table. Therefore, a job listening on this event might not find the corresponding **suspect\_pages** entry immediately.  
  
 When the **Database Suspect Data Page** event class is included in a trace the relative overhead is low. The overhead might be greater if the number of suspect pages increases, for example, if a disk drive is experiencing problems.  
  
## Database Suspect Data Page Event Class Data Columns  
  
|Data Column Name|Data Type|Description|Column ID|Filterable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|ID of the database for which the suspect page event has been raised. This is the same as the **database\_id** column of the **suspect\_pages** table.|3|Yes|  
|**EventClass**|**int**|The type of the event is 213.|27|No|  
|**EventSequence**|**int**|Sequence of event class in batch.|51|No|  
|**SPID**|**int**|ID of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] task that encountered the suspect page.|12|Yes|  
|**StartTime**|**datetime**|Time that the event occurred.|14|Yes|  
|**ObjectID**|**int**|ID of the database file that contains the suspect page. This is the same as the **file\_id** column of the **suspect\_pages** table.|22|Yes|  
|**ObjectID2**|**int**|ID of the suspect page in the file. This is the same as the **page\_id** column of the **suspect\_pages** table.|56|Yes|  
|**Error**|**int**|Type of error that was encountered . This value is the same as the **event\_type** value for the page in the **suspect\_pages** table.|31|Yes|  
  
## See Also  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../Topic/sp_trace_setevent%20\(Transact-SQL\).md)   
 [Manage the suspect_pages Table &#40;SQL Server&#41;](../Topic/Manage%20the%20suspect_pages%20Table%20\(SQL%20Server\).md)  
  
  