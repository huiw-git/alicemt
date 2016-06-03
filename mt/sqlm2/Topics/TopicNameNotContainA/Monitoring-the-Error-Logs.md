---
title: Monitoring the Error Logs
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e250336b-0695-44f6-a42f-23222f94e377
---
# Monitoring the Error Logs
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] logs certain system events and user\-defined events to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] error log and the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows application log. Both logs automatically timestamp all recorded events. Use the information in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] error log to troubleshoot problems related to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
 The Windows application log provides an overall picture of events that occur on the Windows operating system, as well as events in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent. Use the Windows Event Viewer to view the Windows application log and to filter the information. For example, you can filter events, such as information, warning, error, success audit, and failure audit.  
  
## Comparing Error and Application Log Output  
 You can use both the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] error log and the Windows application log to identify the cause of problems. For example, while monitoring the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] error log, you may encounter error messages that do not contain cause information. By comparing the dates and times for events between these logs, you can narrow the list of probable causes. The [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] Log File Viewer lets you integrate [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent, and the Windows logs into a single list, making it easy to understand related server events and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] events. For more information, see the topic "Log File Viewer" in SQL Server Books Online.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Viewing the SQL Server Error Log](../../Topics\TopicNameNotContainA/Viewing-the-SQL-Server-Error-Log.md)|Contains information about the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] error log and how to view it.|  
|[Viewing the Windows Application Log](../../Topics\TopicNameNotContainA/Viewing-the-Windows-Application-Log.md)|Contains information about the Windows application log and how to view it.|  
  
  