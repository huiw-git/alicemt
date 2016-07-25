---
title: "Monitor and Respond to Events"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7fbe155-5b68-4777-bc71-a47637471f32
caps.latest.revision: 5
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
# Monitor and Respond to Events
[!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent can monitor and automatically respond to *events*, such as messages from [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)], specific performance conditions, and Windows Management Instrumentation (WMI) events.  
  
## In This Section  
[Alerts](../content/Alerts.md)  
Contains information about naming an alert and selecting the events or performance conditions to which alerts respond.  
  
[Create a User-Defined Event](../content/Create-a-User-Defined-Event.md)  
Contains information about how to create events other than those that are predefined by [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].  
  
[Operators](../content/Operators.md)  
Contains information about creating aliases for administrators that [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent can use to send notifications when jobs fail or succeed.  
  
## About Monitoring and Responding to Events  
Automated responses to events are called *alerts*. You can define an alert on one or more events to specify how you want [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent to respond to their occurrence. An alert can respond to an event by notifying an administrator or running a job, or both. An alert can also forward an event to the Microsoft Windows application log on a different computer. For example, you can specify that an operator be notified immediately if an event of severity 19 occurs. By defining alerts, database administrators can more effectively monitor and manage [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].  
  
[!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent only responds to events for which an alert is defined. The method that [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent uses to monitor events depends on the type of event.  
  
When a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent alert is defined for a performance counter, [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent directly monitors the performance counter. For a WMI event, [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent registers an event query for the WMI event.  
  
To respond to messages from [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)], [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent monitors the Windows application log. [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent can only respond to messages that appear in this log. By default, SQL Server logs the following messages in the Windows application log:  
  
-   Severity 19 or higher sysmessages errors.  
  
    If you also want to log specific sysmessages errors that have a severity lower than 19, use the sp_altermessage stored procedure to designate such errors as "always logged".  
  
-   Any RAISERROR statement invoked by using the WITH LOG syntax.  
  
    Using RAISERROR WITH LOG is the recommended way to write to the Windows application log from an instance of SQL Server.  
  
-   Any application event that is logged by using xp_logevent.  
  
    > [!NOTE]  
    > Logging application events consumes log space and can cause the Windows application log to exceed its maximum size. Make sure that the maximum Windows application log size is large enough to avoid loss of SQL Server event information.  
  
When [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] logs a message, the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service compares the message against the alerts defined by the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] administrator.  
  
Regardless of the source of the event, the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Agent service responds to the event by performing the tasks specified in the alert for the event.  
  
## See Also  
[sp_altermessage](assetId:///1b28f280-8ef9-48e9-bd99-ec14d79abaca)  
  
