---
title: Get Information About Event Notifications
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8bc10867-66d6-4f57-ac32-a6c29f3327cd
---
# Get Information About Event Notifications
  The following catalog views are available to query metadata about event notifications.  
  
 **To get information about nonserver\-level event notifications**  
  
-   [sys.event_notifications &#40;Transact-SQL&#41;](../Topic/sys.event_notifications%20\(Transact-SQL\).md)  
  
> [!NOTE]  
>  To view metadata about any event notification in **sys.event\_notifications** created at the database level, at the minimum you must have the following: CONTROL, ALTER, TAKE OWNERSHIP, or VIEW DEFINITION permission on the database, be the owner of the event notification, or have ALTER ANY DATABASE EVENT NOTIFICATION permission. For event notifications created on a specific queue, at the minimum you must have the following: CONTROL, ALTER, TAKE OWNERSHIP, or VIEW DEFINITION permission on the object, be the owner of the event notification, or have ALTER ANY DATABASE EVENT NOTIFICATION permission.  
  
 **To get information about server\-level event notifications**  
  
-   [sys.server_event_notifications &#40;Transact-SQL&#41;](../Topic/sys.server_event_notifications%20\(Transact-SQL\).md)  
  
> [!NOTE]  
>  At the minimum, you must have the following: CONTROL or VIEW ANY DEFINITION permission on the server, be the logon or owner of the event notification, or have ALTER ANY EVENT NOTIFICATION permission to view metadata about any event notification in **sys.server\_event\_notifications**.  
  
 **To get information about all events that can fire event notifications**  
  
-   [sys.event_notification_event_types &#40;Transact-SQL&#41;](../Topic/sys.event_notification_event_types%20\(Transact-SQL\).md)  
  
> [!NOTE]  
>  This catalog view does not return event groups.  
  
## See Also  
 [Event Notifications](../../Topics\TopicNameNotContainA/Event-Notifications.md)  
  
  