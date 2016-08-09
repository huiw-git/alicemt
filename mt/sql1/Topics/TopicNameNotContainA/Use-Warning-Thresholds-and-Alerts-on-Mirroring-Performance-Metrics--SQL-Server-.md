---
title: "Use Warning Thresholds and Alerts on Mirroring Performance Metrics (SQL Server)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8cdd1515-0bd7-4f8c-a7fc-a33b575e20f6
caps.latest.revision: 41
caps.handback.revision: 0
manager: jhubbard
---
# Use Warning Thresholds and Alerts on Mirroring Performance Metrics (SQL Server)
This topic contains information about the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] events for which warning thresholds can be configured and managed for database mirroring. You can use the  Database Mirroring Monitor or the **sp_dbmmonitorchangealert**, **sp_dbmmonitorhelpalert**, and **sp_dbmmonitordropalert** stored procedures. This topic also contains information about configuring alerts on database mirroring events.  
  
 After monitoring is established for a mirrored database, a system administrator can configure warning thresholds on several key performance metrics. Also, an administrator can configure alerts on these and other database mirroring events.  
  
 **In This Topic:**  
  
-   [Performance Metrics and Warning Thresholds](#PerfMetricsAndWarningThresholds)  
  
-   [Setting Up and Managing Warning Thresholds](#SetUpManageWarningThresholds)  
  
-   [Using Alerts for a Mirrored Database](#UseAlerts)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="PerfMetricsAndWarningThresholds"></a> Performance Metrics and Warning Thresholds  
 The following table lists the performance metrics for which warnings can be configured, describes the corresponding warning threshold, and lists the corresponding Database Mirroring Monitor label.  
  
|Performance metric|Warning threshold|Database Mirroring Monitor label|  
|------------------------|-----------------------|--------------------------------------|  
|Unsent log|Specifies how many kilobytes (KB) of unsent log generate a warning on the principal server instance. This warning helps measure the potential for data loss in terms of KB and is especially relevant for high-performance mode. However, the warning is also relevant for high-safety mode when mirroring is paused or suspended because the partners become disconnected.|**Warn if the unsent log exceeds the threshold**|  
|Unrestored log|Specifies how many KB of unrestored log generate a warning on the mirror server instance. This warning helps measure failover time. *Failover time* consists mainly of the time that the former mirror server requires to roll forward any log remaining in its redo queue, plus a short additional time.<br /><br /> Note: For an automatic failover, the time for the system to notice the error is independent of the failover time.<br /><br /> For more information, see [Estimate the Interruption of Service During Role Switching (Database Mirroring)](../../Topics/TopicNameNotContainA/Estimate-the-Interruption-of-Service-During-Role-Switching--Database-Mirroring-.md).|**Warn if the unrestored log exceeds the threshold**|  
|Oldest unsent transaction|Specifies the number of minutes worth of transactions that can accumulate in the send queue before a warning is generated on the principal server instance. This warning helps measure the potential for data loss in terms of time and is especially relevant for high-performance mode. However, the warning is also relevant for high-safety mode when mirroring is paused or suspended because the partners become disconnected.|**Warn if the age of the oldest unsent transaction exceeds the threshold**|  
|Mirror commit overhead|Specifies the number of milliseconds of average delay per transaction that are tolerated before a warning is generated on the principal server. This delay is the amount of overhead incurred while the principal server instance waits for the mirror server instance to write the transaction's log record into the redo queue. This value is relevant only in high-safety mode.|**Warn if the mirror commit overhead exceeds the threshold**|  
  
 For any one of these performance metrics, a system administrator can specify a threshold on a mirrored database. For more information, see [Setting Up and Managing Warning Thresholds](#SetUpManageWarningThresholds), later in this topic.  
  
##  <a name="SetUpManageWarningThresholds"></a> Setting Up and Managing Warning Thresholds  
 A system administrator can configure one or more warning thresholds for the key mirroring performance metrics. We recommend setting a threshold for a given warning on both partners to make sure that the warning persists if the database fails over. The appropriate threshold on each partner depends on the performance capabilities of that partner's system.  
  
 Warning thresholds can be configured and managed by using either of the following:  
  
-   Database Mirroring Monitor  
  
     In Database Mirroring Monitor, the administrator can view the current configuration of warnings for a selected database at both the principal and mirror server instances at the same time by selecting the **Warnings** tabbed page. From there, the administrator can open the **Set Warning Thresholds** dialog box to enable and configure one or more warning thresholds.  
  
     For an introduction to the Database Mirroring Monitor interface, see [Database Mirroring Monitor Overview](../../Topics/TopicNameNotContainA/Database-Mirroring-Monitor-Overview.md). For information about launching Database Mirroring Monitor, see [Start Database Mirroring Monitor (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Start-Database-Mirroring-Monitor--SQL-Server-Management-Studio-.md).  
  
-   System stored procedures  
  
     The following set of system stored procedures enable an administrator to set up and manage warning thresholds on mirrored databases of one partner at a time.  
  
    |Procedure|Description|  
    |---------------|-----------------|  
    |[sp_dbmmonitorchangealert](assetId:///1b29f82b-9cf8-4539-8d5c-9a1024db8a50)|Adds or changes warning threshold for a specified mirroring performance metric.|  
    |[sp_dbmmonitorhelpalert](assetId:///43911660-b4e4-4934-8c02-35221160aaec)|Returns information about warning thresholds on one or all of several key database mirroring monitor performance metrics.|  
    |[sp_dbmmonitordropalert](assetId:///fe4a134b-25bf-464e-a5c4-358de215b65a)|Drops the warning for a specified performance metric.|  
  
## Performance-Threshold Events Sent to the Windows Event Log  
 If warning thresholdis defined for a performance metric, when the status table is updated, the latest value is evaluated against the threshold. If the threshold has been reached, the update procedure, **sp_dbmmonitorupdate**, generates an informational event—a *performance-threshold event*— for the metric and writes the event to the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows event log. The following table lists the event IDs of the performance-threshold events.  
  
|Performance metric|Event ID|  
|------------------------|--------------|  
|Unsent log|32042|  
|Unrestored log|32043|  
|Oldest unsent transaction|32040|  
|Mirror commit overhead|32044|  
  
> [!NOTE]  
>  An administrator can define alerts on any one or more of these events. For more information, see [Using Alerts for a Mirrored Database](#UseAlerts), later in this  
>   
>  topic.  
  
##  <a name="UseAlerts"></a> Using Alerts for a Mirrored Database  
 An important part of monitoring a mirrored database is configuring alerts on significant database mirro events. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] generates the following types of database mirroring events:  
  
-   Performance threshold events  
  
     For more information, see "Performance-Threshold Events Sent to the Windows Event Log" earlier in this topic.  
  
-   State-change events  
  
     These are Windows Management Instrumentation (WMI) events that are generated when changes occur in the internal state of a database mirroring session.  
  
    > [!NOTE]  
    >  For more information, see [WMI Provider for Server Events](assetId:///80767fe0-32ac-406a-81a0-8212cd6ce7e4).  
  
 A system administrator can configure alerts on these by using [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent or other applications, such as [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Operations Manager.  
  
 When you define alerts on database mirroring events, we recommend that you define warning thresholds and alerts at both partner server instances. Individual events are generated at either the principal server or the mirror server, but each partner can perform either role at any time. To make sure that an alert continues to operate after a failover, the alert must be defined at both partners.  
  
 For more information, see the white paper about alerting on database mirroring events at this [SQL Server Web site](http://go.microsoft.com/fwlink/?linkid=62373). This white paper contains information about how to configure alerts using [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent, the database mirroring WMI events, and sample scripts.  
  
> [!IMPORTANT]  
>  For all mirroring sessions, we strongly recommend that you configure the database to send an alert on any state-change events. Unless a state change is expected as the result of a manual configuration change, something has occurred that could compromise your data. To help protect your data, identify and fix the cause of an unexpected state change.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To create an alert using SQL Server Management Studio**  
  
-   [How to: Create an Alert Using an Error Number (SQL Server Management Studio)](assetId:///03dd7fac-5073-4f86-babd-37e45a86023c)  
  
-   [How to: Create a WMI Event Alert (SQL Server Management Studio)](assetId:///b8c46db6-408b-484e-98f0-a8af3e7ec763)  
  
 **To monitor database mirroring**  
  
-   [Start Database Mirroring Monitor (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Start-Database-Mirroring-Monitor--SQL-Server-Management-Studio-.md)  
  
-   [sp_dbmmonitoraddmonitoring](assetId:///9489dc30-af29-4363-a172-4645947fc95e)  
  
-   [sp_dbmmonitorchangealert (Transact-SQL)](assetId:///1b29f82b-9cf8-4539-8d5c-9a1024db8a50)  
  
-   [sp_dbmmonitorchangemonitoring](assetId:///17be755b-673d-4cd4-9544-6ecb4220bed3)  
  
-   [sp_dbmmonitordropalert](assetId:///fe4a134b-25bf-464e-a5c4-358de215b65a)  
  
-   [sp_dbmmonitordropmonitoring](assetId:///6f2d552d-bfd7-47a5-8dcb-05560aa1a32d)  
  
-   [sp_dbmmonitorhelpalert](assetId:///43911660-b4e4-4934-8c02-35221160aaec)  
  
-   [sp_dbmmonitorhelpmonitoring](assetId:///a085cf87-269f-454a-a146-21f80a113b72)  
  
-   [sp_dbmmonitorresults](assetId:///d575e624-7d30-4eae-b94f-5a7b9fa5427e)  
  
-   [sp_dbmmonitorupdate](assetId:///9ceb9611-4929-44ee-a406-c39ba2720fd5)  
  
## See Also  
 [Database Mirroring (SQL Server)](../../Topics/TopicNameNotContainA/Database-Mirroring--SQL-Server-.md)   
 [Monitoring Database Mirroring (SQL Server)](../../Topics/TopicNameNotContainA/Monitoring-Database-Mirroring--SQL-Server-.md)