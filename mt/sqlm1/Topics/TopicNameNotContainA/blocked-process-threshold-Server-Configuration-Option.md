---
title: blocked process threshold Server Configuration Option
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3d46d143-bc6a-4220-8b55-6baa37547c25
---
# blocked process threshold Server Configuration Option
  Use the **blocked process threshold** option to specify the threshold, in seconds, at which blocked process reports are generated. The threshold can be set from 0 to 86,400. By default, no blocked process reports are produced. This event is not generated for system tasks or for tasks that are waiting on resources that do not generate detectable deadlocks.  
  
 You can define an [alert](../Topic/Alerts.md) to be executed when this event is generated. So for example, you can choose to page the administrator to take appropriate action to handle the blocking situation.  
  
 Blocked process threshold uses the deadlock monitor background thread to walk through the list of tasks waiting for a time greater than or multiples of the configured threshold. The event is generated once per reporting interval for each of the blocked tasks.  
  
 The blocked process report is done on a best effort basis. There is no guarantee of any real\-time or even close to real\-time reporting.  
  
 The setting takes effect immediately without a server stop and restart.  
  
## Examples  
 The following example sets the `blocked process threshold` to `20` seconds, generating a blocked process report for each task that is blocked.  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
sp_configure 'blocked process threshold', 20 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
## See Also  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../Topic/sp_trace_setevent%20\(Transact-SQL\).md)   
 [Blocked Process Report Event Class](../../Topics\TopicNameNotContainA/Blocked-Process-Report-Event-Class.md)  
  
  