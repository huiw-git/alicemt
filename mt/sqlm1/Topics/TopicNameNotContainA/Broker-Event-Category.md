---
title: Broker Event Category
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 470dc93c-0dda-4d89-829b-937738d59b31
---
# Broker Event Category
  The **Broker** event category contains general Service Broker events.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Broker:Activation Event Class](../Topic/Broker:Activation%20Event%20Class.md)|An event generated when a queue monitor starts an activation stored procedure.|  
|[Broker:Connection Event Class](../Topic/Broker:Connection%20Event%20Class.md)|An event generated to report the status of a transport connection managed by Service Broker.|  
|[Broker:Conversation Event Class](../Topic/Broker:Conversation%20Event%20Class.md)|An event generated to report the progress of a conversation.|  
|[Broker:Conversation Group Event Class](../Topic/Broker:Conversation%20Group%20Event%20Class.md)|An event generated when the database creates or drops a conversation group.|  
|[Broker:Corrupted Message Event Class](../Topic/Broker:Corrupted%20Message%20Event%20Class.md)|An event generated to report that the database has received a corrupt message.|  
|[Broker:Forwarded Message Dropped Event Class](../Topic/Broker:Forwarded%20Message%20Dropped%20Event%20Class.md)|An event generated when SQL Server drops a Service Broker message that was to have been forwarded.|  
|[Broker:Forwarded Message Sent Event Class](../Topic/Broker:Forwarded%20Message%20Sent%20Event%20Class.md)|An event generated when SQL Server forwards a Service Broker message.|  
|[Broker:Message Classify Event Class](../Topic/Broker:Message%20Classify%20Event%20Class.md)|An event generated when Service Broker determines the routing for a message.|  
|[Broker:Message Drop Event Class](../Topic/Broker:Message%20Drop%20Event%20Class.md)|An event generated when Service Broker is unable to retain a received message that should have been delivered to a service in this instance|  
|[Broker:Remote Message Ack Event Class](../Topic/Broker:Remote%20Message%20Ack%20Event%20Class.md)|An event generated when Service Broker sends or receives a message acknowledgement.|  
  
 Two security audit events are also provided for Service Broker. For more information on those events, see [Audit Broker Login Event Class](../../Topics\TopicNameNotContainA/Audit-Broker-Login-Event-Class.md) and [Audit Broker Conversation Event Class](../../Topics\TopicNameNotContainA/Audit-Broker-Conversation-Event-Class.md).  
  
## See Also  
 [Security Audit Event Category](../../Topics\TopicNameNotContainA/Security-Audit-Event-Category.md)  
  
  