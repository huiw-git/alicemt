---
title: SQL Server Monitor Overview
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 048ae16d-31c3-489a-9f1e-1400a3bacd39
---
# SQL Server Monitor Overview
  SQL Server Monitor does not perform monitoring functions, but it hosts modules that do. The SQL Server Monitor modules include Replication Monitor and Database Mirroring Monitor.  
  
 To use one of these modules, select that module on the **Go** menu. The currently selected module owns the content of the navigation and detail panes, user interaction in the detail panes, and the queries for content and status.  
  
> [!NOTE]  
>  For more information about these monitors, see [Monitoring Replication](../../Topics\TopicNameNotContainA/Monitoring-Replication.md) and [Monitoring Database Mirroring &#40;SQL Server&#41;](../Topic/Monitoring%20Database%20Mirroring%20\(SQL%20Server\).md).  
  
## Permissions  
  
-   Replication Monitor  
  
     To monitor replication, you must be a member of the **sysadmin** fixed server role at the Distributor or a member of the **replmonitor** fixed database role in the distribution database. A system administrator can add any user to the **replmonitor** role, which allows that user to view replication activity in Replication Monitor; however, the user cannot administer replication.  
  
-   Database Mirroring Monitor  
  
     To monitor database mirroring, you must be a member of either the **sysadmin** fixed server role or the **dbm\_monitor** fixed database role on the server instance. If you are a member of **sysadmin** or **dbm\_monitor** on only one of the partner server instances, the monitor can connect only to that partner; the monitor cannot retrieve information from the other partner. For more information, see [Database Mirroring Monitor Overview](../../Topics\TopicNameNotContainA/Database-Mirroring-Monitor-Overview.md).  
  
## Menu Options  
 SQL Server Monitor has a menu that contains commands that pertain to SQL Server Monitor. This menu may also contain commands from the selected module.  
  
 The following menu options pertain to SQL Server Monitor.  
  
 **File**  
 This menu contains the **Exit** command.  
  
 **Action**  
 Contains the context menu of the node selected in the navigation tree.  
  
 **Go**  
 Contains a list of monitoring components:  
  
-   Database Mirroring  
  
-   Replication  
  
 **To use SQL Server Management Studio to monitor database mirroring**  
  
-   [Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../Topic/Start%20Database%20Mirroring%20Monitor%20\(SQL%20Server%20Management%20Studio\).md)  
  
## See Also  
 [Monitoring Database Mirroring &#40;SQL Server&#41;](../Topic/Monitoring%20Database%20Mirroring%20\(SQL%20Server\).md)  
  
  