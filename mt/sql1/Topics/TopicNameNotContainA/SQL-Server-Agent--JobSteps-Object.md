---
title: "SQL Server Agent, JobSteps Object"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 44f9983c-1753-4fe0-8475-973aa2460b3a
caps.latest.revision: 24
caps.handback.revision: 0
manager: jhubbard
---
# SQL Server Agent, JobSteps Object
The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent **JobSteps** performance object contains performance counters that report information about [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent job steps. The table below lists the counters that this object contains.  
  
 The table below contains the **SQLAgent:JobSteps** counters.  
  
|Name|Description|  
|----------|-----------------|  
|**Active steps**|This counter reports the number of job steps currently running.|  
|**Queued steps**|This counter reports the number of job steps that are ready for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent to run, but which have not yet started running.|  
|**Total step retries**|This counter reports the total number of times that [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] has retried a job step since the last server restart.|  
  
 Each counter in the object contains the following instances:  
  
|Instance|Description|  
|--------------|-----------------|  
|**_Total**|Information for all job steps.|  
|**ActiveScripting**|Information for job steps that use the **ActiveScripting** subsystem.|  
|**ANALYSISCOMMAND**|Information for job steps that use the ANALYSISCOMMAND subsystem.|  
|**ANALYSISQUERY**|Information for job steps that use the ANALYSISQUERY subsystem.|  
|**CmdExec**|Information for job steps that use the **CmdExec** subsystem.|  
|**Distribution**|Information for job steps that use the **Distribution** subsystem.|  
|**Dts**|Information for job steps that use the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] subsystem.|  
|**LogReader**|Information for job steps that use the **LogReader** subsystem.|  
|**Merge**|Information for job steps that use the **Merge** subsystem.|  
|**PowerShell**|Information for job steps that use the **PowerShell** subsystem.|  
|**QueueReader**|Information for job steps that use the **QueueReader** subsystem.|  
|**Snapshot**|Information for job steps that use the **Snapshot** subsystem.|  
|**TSQL**|Information for job steps that execute [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)].|  
  
## See Also  
 [Monitoring Resource Usage (System Monitor)](assetId:///51352afc-a0a4-428b-8985-f9e58bb57c31)   
 [Using Performance Objects](assetId:///830b843a-6b2a-4620-a51b-98358e9fc54b)   
 [Monitor Resource Usage (System Monitor)](../../Topics/TopicNameNotContainA/Monitor-Resource-Usage--System-Monitor-.md)