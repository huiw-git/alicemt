---
title: "Alter an Extended Events Session"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 114ec05b-7eca-4c87-b276-25e37b84be39
caps.latest.revision: 10
manager: jhubbard
---
# Alter an Extended Events Session
After you create an Extended Events session, you can alter it according to your needs using the **SQL Server Extended Events Wizard**.  
  
## Before you Begin  
 You cannot alter a target for active and inactive sessions, and you cannot change the advanced properties configurations for an active session.  
  
 You can make the following alterations to both active and inactive event sessions:  
  
-   Add or remove events from the session, and alter the event configurations such as event fields, filters and actions.  
  
-   Add or remove a target from the event session.  
  
-   Enable the **Start the event session on server startup** option.  
  
 You can make the following additional alterations to an inactive event session:  
  
-   Enable the **Track the relationship between events** option.  
  
-   Change the advanced properties configuration.  
  
> [!NOTE]  
>  The **SQL Server Extended Events Wizard** does not support event session modification.  
  
## How to alter an Extended Events session using the SQL Server Extended Events Wizard  
  
-   In Object Explorer, expand **Management**, expand **Extended Events**, and then expand **Sessions**.  
  
-   Right-click the session you want to alter, and then click **Properties**.  
  
-   In the **Properties** dialog box, make the appropriate changes, and then click **OK**.  
  
## See Also  
 [ALTER EVENT SESSION (Transact-SQL)](assetId:///da006ac9-f914-4995-a2fb-25b5d971cd90)   
 [Create an Extended Events Session Using Query Editor](../../Topics/TopicNameNotContainA/Create-an-Extended-Events-Session-Using-Query-Editor.md)