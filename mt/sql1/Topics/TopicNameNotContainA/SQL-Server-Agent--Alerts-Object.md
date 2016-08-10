---
title: "SQL Server Agent, Alerts Object"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e5e37f74-ee88-46d0-ad8f-71fd1b1fa64a
caps.latest.revision: 25
caps.handback.revision: 0
manager: jhubbard
---
# SQL Server Agent, Alerts Object
The SQL Server Agent **Alerts** performance object contains performance counters that report information about SQL Server Agent alerts. The table below lists the counters that this object contains.  
  
 The table below contains the **SQLAgent:Alerts** counters.  
  
|Name|Description|  
|----------|-----------------|  
|**Activated alerts**|This counter reports the total number of alerts that SQL Server Agent has activated since the last time that SQL Server Agent restarted.|  
|**Alerts activated/minute**|This counter reports the number of alerts that SQL Server Agent activated within the last minute.|  
  
> [!NOTE]  
>  To use this SQL Server Agent object, users must be a member of the **sysadmin** fixed server role.  
  
## See Also  
 [Monitoring Resource Usage (System Monitor)](assetId:///3f57d0f0-4781-46ec-82cd-b751dc5affef)   
 [Using Performance Objects](assetId:///830b843a-6b2a-4620-a51b-98358e9fc54b)   
 [Monitor Resource Usage (System Monitor)](../../Topics/TopicNameNotContainA/Monitor-Resource-Usage--System-Monitor-.md)