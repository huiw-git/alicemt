---
title: "Database Suspect Data Page Event Class"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 098e1443-a8a0-425c-9311-0a479b1370ed
caps.latest.revision: 12
manager: jhubbard
---
# Database Suspect Data Page Event Class
The **Database Suspect Data Page** event class indicates when a page is added to the [suspect_pages](assetId:///119c8d62-eea8-44fb-bf72-de469c838c50) table in [msdb](../../Topics/TopicNameNotContainA/msdb-Database.md). Include this event class in traces that are monitoring the occurrence of suspect pages.  
  
> [!NOTE]  
>  This event is issued asynchronously from the insertion of a corresponding row into the **suspect_pages** table. Therefore, a job listening on this event might not find the corresponding **suspect_pages** entry immediately.  
  
 When the **Database Suspect Data Page** event class is included in a trace the relative overhead is low. The overhead might be greater if the number of suspect pages increases, for example, if a disk drive is experiencing problems.  
  
## Database Suspect Data Page Event Class Data Columns  
  
|Data Column Name|Data Type|Description|Column ID|Filterable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|ID of the database for which the suspect page event has been raised. This is the same as the **database_id** column of the **suspect_pages** table.|3|Yes|  
|**EventClass**|**int**|The type of the event is 213.|27|No|  
|**EventSequence**|**int**|Sequence of event class in batch.|51|No|  
|**SPID**|**int**|ID of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] task that encountered the suspect page.|12|Yes|  
|**StartTime**|**datetime**|Time that the event occurred.|14|Yes|  
|**ObjectID**|**int**|ID of the database file that contains the suspect page. This is the same as the **file_id** column of the **suspect_pages** table.|22|Yes|  
|**ObjectID2**|**int**|ID of the suspect page in the file. This is the same as the **page_id** column of the **suspect_pages** table.|56|Yes|  
|**Error**|**int**|Type of error that was encountered . This value is the same as the **event_type** value for the page in the **suspect_pages** table.|31|Yes|  
  
## See Also  
 [sp_trace_setevent (Transact-SQL)](assetId:///7662d1d9-6d0f-443a-b011-c901a8b77a44)   
 [Manage the suspect_pages Table (SQL Server)](../../Topics/TopicNameNotContainA/Manage-the-suspect_pages-Table--SQL-Server-.md)