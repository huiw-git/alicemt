---
title: SQL Server Agent Properties (Advanced Page)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a4d798ee-4c18-40d4-b6af-63d17503738c
manager: jhubbard
translation.priority.mt: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# SQL Server Agent Properties (Advanced Page)
Use this page to view and modify advanced properties of the [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service.  
  
## Options  
**SQL Server event forwarding**  
The options in this category activate and configure event forwarding.  
  
**Forward events to a different server**  
Forwards [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent events to a different server.  
  
**Server**  
Select the name of the server to forward events to.  
  
**Unhandled events**  
Forwards only unhandled events to the specified server. [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent forwards only events that no alert responds to.  
  
**All events**  
Forwards all events. When an alert in the local instance responds to the event, [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] agent will both forward the event and process the alert.  
  
**If event has severity at or above**  
Forwards only events with a severity level at or above the level specified.  
  
**Idle CPU Condition**  
The options in this category define the conditions under which [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent runs jobs scheduled to run on the Idle CPU schedule.  
  
**Define idle CPU condition**  
Defines the conditions under which [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent considers the CPU to be idle.  
  
**Average CPU usage falls below**  
Percentage of CPU usage below which the CPU is considered to be idle.  
  
**And remains below this level for**  
Amount of time that the average CPU must below the level specified before [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent runs jobs on the Idle CPU schedule.  
  
## See Also  
[Create and Attach Schedules to Jobs](../content/Create-and-Attach-Schedules-to-Jobs.md)  
[Manage Events](../content/Manage-Events.md)  
  
