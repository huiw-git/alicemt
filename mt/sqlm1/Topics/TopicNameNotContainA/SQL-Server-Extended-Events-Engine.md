---
title: SQL Server Extended Events Engine
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d74642a5-42b9-4a15-aa3d-f98bfe695050
---
# SQL Server Extended Events Engine
  The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Extended Events engine is a collection of services and objects that:  
  
-   Enable the definition of events.  
  
-   Enable processing event data.  
  
-   Manage Extended Events services and objects in the system.  
  
-   Maintain a list of Extended Events sessions and manage access to that list.  
  
 The Extended Events engine itself does not provide any events or actions to take when an event fires. The processes that use the Extended Events engine define interaction with the engine. These processes add event points and supply the actions to take in response to event firing.  
  
 The following illustration shows a simplified view of an Extended Events session. For more information, see [SQL Server Extended Events Sessions](../../Topics\TopicNameNotContainA/SQL-Server-Extended-Events-Sessions.md).  
  
 ![Detailed extended events architecture](../../Images\Image\ImageNotContaina/xeArchitectureDetailed.gif "xeArchitectureDetailed")  
  
 Note the following:  
  
-   Each Windows process can have one or more modules \(**Win32 process**, **Win32 module**\). These are also known as *binaries* or *executable modules*.  
  
-   Each of the Windows process modules can contain one or more Extended Events packages \(**Package**\), which contain one or more Extended Events objects \(**Type**, **Target**, **Action**, **Map**, **Predicate**, and **Event**\).  
  
-   Inside a host process there can only be one instance of the Extended Events engine \(**Extended event engine**\), which:  
  
    -   Manages some aspects of the session \(for example, enumerating sessions\).  
  
    -   Handles dispatching \(**Dispatcher**\). This is similar to a thread pool.  
  
    -   Handles memory buffers \(**Buffer**\) for events. When buffers are filled, the buffers are dispatched to targets.  
  
-   After a session is created and events are optionally bound to the session \(**Session context**\):  
  
    -   Instances of targets \(**Target instance**\) may be also be created and added to the session.  
  
    -   When buffers are filled, those buffers are dispatched to targets.  
  
## See Also  
 [Extended Events](../../Topics\TopicNameNotContainA/Extended-Events.md)  
  
  