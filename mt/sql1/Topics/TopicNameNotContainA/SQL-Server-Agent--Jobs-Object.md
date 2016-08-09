---
title: "SQL Server Agent, Jobs Object"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 225b5e2d-4a78-4178-b2b6-b419df83c4aa
caps.latest.revision: 22
manager: jhubbard
---
# SQL Server Agent, Jobs Object
The SQL Server Agent **Jobs** performance object contains performance counters that report information about SQL Server Agent jobs. The table below lists the counters that this object contains.  
  
 The table below contains the **SQLAgent:Jobs** counters.  
  
|Name|Description|  
|----------|-----------------|  
|**Active Jobs**|This counter reports the number of jobs currently running.|  
|**Failed jobs**|This counter reports the number of jobs that exited with failure.|  
|**Job success rate**|This counter reports the percentage of executed jobs that completed successfully.|  
|**Jobs activated/minute**|This counter reports the number of jobs launched within the last minute.|  
|**Queued jobs**|This counter reports the number of jobs that are ready for SQL Server Agent to run, but which have not yet started running.|  
|**Successful jobs**|This counter reports the number of jobs that exited with success.|  
  
 Each counter in the object contains the following instances:  
  
|Instance|Description|  
|--------------|-----------------|  
|**_Total**|Information for all jobs.|  
|**Alerts**|Information for jobs started by alerts.|  
|**Others**|Information for jobs that were not started by alerts or schedules. Typically these are jobs started manually using **sp_start_job**.|  
|**Schedules**|Information for jobs started by schedules.|  
  
## See Also  
 [Monitoring Resource Usage (System Monitor)](assetId:///69e06724-25c7-4fb3-8a5b-3d4596f21756)   
 [Using Performance Objects](assetId:///830b843a-6b2a-4620-a51b-98358e9fc54b)   
 [Monitor Resource Usage (System Monitor)](../../Topics/TopicNameNotContainA/Monitor-Resource-Usage--System-Monitor-.md)