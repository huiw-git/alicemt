---
title: Extended Events
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bf3b98a6-51ed-4f2d-9c26-92f07f1fa947
---
# Extended Events
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Extended Events has a highly scalable and highly configurable architecture that allows users to collect as much or as little information as is necessary to troubleshoot or identify a performance problem.  
  
 You can find more information about Extended Events on the web at [SQL Server Extended Events](http://blogs.msdn.com/b/extended_events/).  
  
## Benefits of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Extended Events  
 Extended Events is a light weight performance monitoring system that uses very few performance resources. Extended Events provides two graphical user interfaces \(**New Session Wizard** and **New Session**\) to create, modify, display, and analyze your session data.  
  
## Extended Events Concepts  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Extended Events \(Extended Events\) builds on existing concepts, such as an event or an event consumer, uses concepts from Event Tracing for Windows, and introduces new concepts.  
  
 The following table describes the concepts in Extended Events.  
  
|Topic|Description|  
|-----------|-----------------|  
|[SQL Server Extended Events Packages](../../Topics\TopicNameNotContainA/SQL-Server-Extended-Events-Packages.md)|Describes the Extended Events packages that contain objects that are used for obtaining and processing data when an Extended Events session is running.|  
|[SQL Server Extended Events Targets](../../Topics\TopicNameNotContainA/SQL-Server-Extended-Events-Targets.md)|Describes the event consumers that can receive data during an event session.|  
|[SQL Server Extended Events Engine](../../Topics\TopicNameNotContainA/SQL-Server-Extended-Events-Engine.md)|Describes the engine that implements and manages an Extended Events session.|  
|[SQL Server Extended Events Sessions](../../Topics\TopicNameNotContainA/SQL-Server-Extended-Events-Sessions.md)|Describes the Extended Events session.|  
  
## Extended Events Architecture  
 Extended Events \(Extended Events\) is a general event\-handling system for server systems. The Extended Events infrastructure supports the correlation of data from [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], and under certain conditions, the correlation of data from the operating system and database applications. In the latter case, Extended Events output must be directed to Event Tracing for Windows \(ETW\) to correlate the event data with operating system or application event data.  
  
 All applications have execution points that are useful both inside and outside an application. Inside the application, asynchronous processing may be enqueued using information that is collected during the initial execution of a task. Outside the application, execution points provide monitoring utilities with information about the behavioral and performance characteristics of the monitored application.  
  
 Extended Events supports using event data outside a process. This data is typically used by:  
  
-   Tracing tools, such as SQL Trace and System Monitor.  
  
-   Logging tools, such as the Windows event log or the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] error log.  
  
-   Users administering a product or developing applications on a product.  
  
 Extended Events has the following key design aspects:  
  
-   The Extended Events engine is event agnostic. This enables the engine to bind any event to any target because the engine is not constrained by event content. For more information about the Extended Events engine, see [SQL Server Extended Events Engine](../../Topics\TopicNameNotContainA/SQL-Server-Extended-Events-Engine.md).  
  
-   Events are separated from event consumers, which are called *targets* in Extended Events. This means that any target can receive any event. In addition, any event that is raised can be automatically consumed by the target, which can log or provide additional event context. For more information, see [SQL Server Extended Events Targets](../../Topics\TopicNameNotContainA/SQL-Server-Extended-Events-Targets.md).  
  
-   Events are distinct from the action to take when an event occurs. Therefore, any action can be associated with any event.  
  
-   Predicates can dynamically filter when event data should be captured. This adds to the flexibility of the Extended Events infrastructure. For more information, see [SQL Server Extended Events Packages](../../Topics\TopicNameNotContainA/SQL-Server-Extended-Events-Packages.md).  
  
 Extended Events can synchronously generate event data \(and asynchronously process that data\) which provides a flexible solution for event handling. In addition, Extended Events provides the following features:  
  
-   A unified approach to handling events across the server system, while enabling users to isolate specific events for troubleshooting purposes.  
  
-   Integration with, and support for existing ETW tools.  
  
-   A fully configurable event handling mechanism that is based on [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
-   The ability to dynamically monitor active processes, while having minimal effect on those processes.  
  
-   A default system health session that runs without any noticeable performance effects. The session collects system data that you can use to help troubleshoot performance issues. For more information, see [Use the system_health Session](../../Topics\TopicNameNotContainA/Use-the-system_health-Session.md).  
  
## Extended Events Tasks  
 Using [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] to execute [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] Data Definition Language \(DDL\) statements, dynamic management views and functions, or catalog views, you can create simple or complex [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Extended Events troubleshooting solutions for your [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] environment.  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Use the **Object Explorer** to manage event sessions.|[Manage Event Sessions in the Object Explorer](../../Topics\TopicNameNotContainA/Manage-Event-Sessions-in-the-Object-Explorer.md)|  
|Describes how to create an Extended Events session.|[Create an Extended Events Session](../../Topics\TopicNameNotContainA/Create-an-Extended-Events-Session.md)|  
|Describes how to view and refresh target data.|[View Event Session Data](../../Topics\TopicNameNotContainA/View-Event-Session-Data.md)|  
|Describes how to use Extended Events tools to create and manage your [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Extended Events sessions.|[Extended Events Tools](../../Topics\TopicNameNotContainA/Extended-Events-Tools.md)|  
|Describes how to alter an Extended Events session.|[Alter an Extended Events Session](../../Topics\TopicNameNotContainA/Alter-an-Extended-Events-Session.md)|  
|Describes how to copy or export target data.|[Copy or Export Target Data](../../Topics\TopicNameNotContainA/Copy-or-Export-Target-Data.md)|  
|Describes how to modify your trace results view to customize how you want to analyze your data.|[Modify the Trace Results View](../../Topics\TopicNameNotContainA/Modify-the-Trace-Results-View.md)|  
|Describes how to get information about the fields associated with the events.|[Get the Fields for All Events](../../Topics\TopicNameNotContainA/Get-the-Fields-for-All-Events.md)|  
|Describes how to find out what events are available in the registered packages.|[View the Events for Registered Packages](../../Topics\TopicNameNotContainA/View-the-Events-for-Registered-Packages.md)|  
|Describes how to determine what Extended Events targets are available in the registered packages.|[View the Extended Events Targets for Registered Packages](../../Topics\TopicNameNotContainA/View-the-Extended-Events-Targets-for-Registered-Packages.md)|  
|Describes how to view the Extended Events events and actions that are equivalent to each SQL Trace event and its associated columns.|[View the Extended Events Equivalents to SQL Trace Event Classes](../../Topics\TopicNameNotContainA/View-the-Extended-Events-Equivalents-to-SQL-Trace-Event-Classes.md)|  
|Describes how to find the parameters you can set when you use the ADD TARGET argument in CREATE EVENT SESSION or ALTER EVENT SESSION.|[Get the Configurable Parameters for the ADD TARGET Argument](../../Topics\TopicNameNotContainA/Get-the-Configurable-Parameters-for-the-ADD-TARGET-Argument.md)|  
|Describes how to convert an existing SQL Trace script to an Extended Events session.|[Convert an Existing SQL Trace Script to an Extended Events Session](../../Topics\TopicNameNotContainA/Convert-an-Existing-SQL-Trace-Script-to-an-Extended-Events-Session.md)|  
|Describes how to determine which queries are holding the lock, the plan of the query, and the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] stack at the time the lock was taken.|[Determine Which Queries Are Holding Locks](../../Topics\TopicNameNotContainA/Determine-Which-Queries-Are-Holding-Locks.md)|  
|Describes how to identify the source of locks that are hindering database performance.|[Find the Objects That Have the Most Locks Taken on Them](../../Topics\TopicNameNotContainA/Find-the-Objects-That-Have-the-Most-Locks-Taken-on-Them.md)|  
|Describes how to use Extended Events with Event Tracing for Windows to monitor system activity.|[Monitor System Activity Using Extended Events](../../Topics\TopicNameNotContainA/Monitor-System-Activity-Using-Extended-Events.md)|  
  
## See Also  
 [Data-tier Applications](../../Topics\TopicNameNotContainA/Data-tier-Applications.md)   
 [DAC Support For SQL Server Objects and Versions](../../Topics\TopicNameNotContainA/DAC-Support-For-SQL-Server-Objects-and-Versions.md)   
 [Deploy a Data-tier Application](../../Topics\TopicNameContainA/Deploy-a-Data-tier-Application.md)   
 [Monitor Data-tier Applications](../../Topics\TopicNameNotContainA/Monitor-Data-tier-Applications.md)   
 [Extended Events Dynamic Management Views](../Topic/Extended%20Events%20Dynamic%20Management%20Views.md)   
 [Extended Events Catalog Views &#40;Transact-SQL&#41;](../Topic/Extended%20Events%20Catalog%20Views%20\(Transact-SQL\).md)  
  
  