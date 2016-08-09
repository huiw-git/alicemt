---
title: "Get Information About Event Notifications"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8bc10867-66d6-4f57-ac32-a6c29f3327cd
caps.latest.revision: 23
caps.handback.revision: 0
manager: jhubbard
---
# Get Information About Event Notifications
The following catalog views are available to query metadata about event notifications.  
  
 **To get information about nonserver-level event notifications**  
  
-   [Event Notifications (Database Engine)](assetId:///136a76ee-2b35-4418-ab46-fda2d51f7d99)  
  
> [!NOTE]  
>  To view metadata about any event notification in **sys.event_notifications** created at the database level, at the minimum you must have the following: CONTROL, ALTER, TAKE OWNERSHIP, or VIEW DEFINITION permission on the database, be the owner of the event notification, or have ALTER ANY DATABASE EVENT NOTIFICATION permission. For event notifications created on a specific queue, at the minimum you must have the following: CONTROL, ALTER, TAKE OWNERSHIP, or VIEW DEFINITION permission on the object, be the owner of the event notification, or have ALTER ANY DATABASE EVENT NOTIFICATION permission.  
  
 **To get information about server-level event notifications**  
  
-   [sys.server_event_notifications](assetId:///1a83a044-3130-4551-95ca-162525846ff5)  
  
> [!NOTE]  
>  At the minimum, you must have the following: CONTROL or VIEW ANY DEFINITION permission on the server, be the logon or owner of the event notification, or have ALTER ANY EVENT NOTIFICATION permission to view metadata about any event notification in **sys.server_event_notifications**.  
  
 **To get information about all events that can fire event notifications**  
  
-   [sys.event_notification_event_types](assetId:///73dae456-7044-4b00-b0bd-990ef810b356)  
  
> [!NOTE]  
>  This catalog view does not return event groups.  
  
## See Also  
 [Event Notifications](../../Topics/TopicNameNotContainA/Event-Notifications.md)