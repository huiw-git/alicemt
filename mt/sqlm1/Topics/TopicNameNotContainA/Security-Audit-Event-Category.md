---
title: Security Audit Event Category
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9686a495-68d7-4137-8e30-2655aa519f6c
---
# Security Audit Event Category
  The Security Audit event category has the event classes described in the following table.  
  
|Event Class|Event Id|Description|  
|-----------------|--------------|-----------------|  
|Audit Login|1|Records all new connection events since the trace started, such as when a client requested a connection to a server running an instance of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)].|  
|Audit Logout|2|Records all new disconnect events since the trace started, such as when a client issues a disconnect command.|  
|Audit Server Starts and Stops|4|Records shutdown, start, and pause activities for services.|  
|Audit Object Permission Event|18|Records all object permission changes.|  
|Audit Admin Operations Event|19|Records server operations for backup, restore, synchronize, attach, detach, image load, and image save.|  
  
 For information about the columns associated with each of the Security Audit event classes, see [Security Audit Data Columns](../../Topics\TopicNameNotContainA/Security-Audit-Data-Columns.md).  
  
## See Also  
 [Analysis Services Trace Events](../../Topics\TopicNameNotContainA/Analysis-Services-Trace-Events.md)  
  
  