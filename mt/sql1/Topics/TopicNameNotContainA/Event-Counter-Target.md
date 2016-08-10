---
title: "Event Counter Target"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 342e08d1-dcca-4a71-ae64-cb61b55b85bc
caps.latest.revision: 15
caps.handback.revision: 0
manager: jhubbard
---
# Event Counter Target
The event counter target counts all events that occur during an Extended Events session. By using the event counter target, you can obtain information about workload characteristics without adding the overhead of full event collection. This target has no customizable parameters.  
  
## Adding the Target to a Session  
 To add the event counter target to an Extended Events session, you must include the following statement when you create or alter an event session:  
  
```  
ADD TARGET package0.event_counter  
```  
  
## Reviewing the Target Output  
 To review the output from the event counter target, you can use the following query, replacing *session_name* with the name of the event session:  
  
```  
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 The following example shows the event counter target output format.  
  
```  
<CounterTarget truncated = "0">  
  <Packages>  
    <Package name = "[package name]">  
      <Event name = "[event name]" count = "[number]" />  
    </Package>  
  </Packages>  
</CounterTarget>  
```  
  
## See Also  
 [SQL Server Extended Events Targets](../../Topics/TopicNameNotContainA/SQL-Server-Extended-Events-Targets.md)   
 [sys.dm_xe_session_targets (Transact-SQL)](assetId:///76fbc3e1-ad88-4a47-8bf1-471c3bee5ad8)   
 [CREATE EVENT SESSION (Transact-SQL)](assetId:///67683027-2b0f-47aa-b223-604731af8b4d)   
 [ALTER EVENT SESSION (Transact-SQL)](assetId:///da006ac9-f914-4995-a2fb-25b5d971cd90)