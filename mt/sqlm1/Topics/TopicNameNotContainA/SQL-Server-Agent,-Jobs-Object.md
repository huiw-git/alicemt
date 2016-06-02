---
title: SQL Server Agent, Jobs Object
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 225b5e2d-4a78-4178-b2b6-b419df83c4aa
---
# SQL Server Agent, Jobs Object
  The SQL Server Agent **Jobs** performance object contains performance counters that report information about SQL Server Agent jobs. The table below lists the counters that this object contains.  
  
 The table below contains the **SQLAgent:Jobs** counters.  
  
|Name|Description|  
|----------|-----------------|  
|**Active Jobs**|This counter reports the number of jobs currently running.|  
|**Failed jobs**|This counter reports the number of jobs that exited with failure.|  
|**Job success rate**|This counter reports the percentage of executed jobs that completed successfully.|  
|**Jobs activated\/minute**|This counter reports the number of jobs launched within the last minute.|  
|**Queued jobs**|This counter reports the number of jobs that are ready for SQL Server Agent to run, but which have not yet started running.|  
|**Successful jobs**|This counter reports the number of jobs that exited with success.|  
  
 Each counter in the object contains the following instances:  
  
|Instance|Description|  
|--------------|-----------------|  
|**\_Total**|Information for all jobs.|  
|**Alerts**|Information for jobs started by alerts.|  
|**Others**|Information for jobs that were not started by alerts or schedules. Typically these are jobs started manually using **sp\_start\_job**.|  
|**Schedules**|Information for jobs started by schedules.|  
  
## See Also  
 [Implement Jobs](../Topic/Implement%20Jobs.md)   
 [Use Performance Objects](../Topic/Use%20Performance%20Objects.md)   
 [Monitor Resource Usage &#40;System Monitor&#41;](../Topic/Monitor%20Resource%20Usage%20\(System%20Monitor\).md)  
  
  