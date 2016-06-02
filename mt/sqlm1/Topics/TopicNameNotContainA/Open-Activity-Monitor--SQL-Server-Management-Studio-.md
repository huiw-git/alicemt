---
title: Open Activity Monitor (SQL Server Management Studio)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0a6eeb16-f02b-479d-9a60-543e40ebf46b
---
# Open Activity Monitor (SQL Server Management Studio)
  This topic describes how to open the Activity Monitor to obtain information about [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] processes and how these processes affect the current instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. It also describes how to set the refresh interval of the Activity Monitor.  
  
   
 Activity Monitor runs queries on the monitored instance to obtain information for the Activity Monitor display panes. When the refresh interval is set to less than 10 seconds, the time that is used to run these queries can affect server performance  
  

  
##  <a name="Permissions"></a> Check your permissions  
 To view the Activity Monitor, you must have VIEW SERVER STATE permission. To view the Data File I\/O section of Activity Monitor, you must have CREATE DATABASE, ALTER ANY DATABASE, or VIEW ANY DEFINITION permission in addition to VIEW SERVER STATE.  
  
 To KILL a process, a user must be a member of the sysadmin or processadmin fixed server roles.  
  
  
## Open Activity Monitor 
#### In SQL Server Management Studio  
  
1.  On the [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] standard toolbar, click **Activity Monitor**.  
  
2.  In the **Connect to Server** dialog box, select the server name and authentication mode, and then click **Connect**.  
  
 You can also open Activity Monitor at any time by pressing **CTRL\+ALT A**.  
  
#### In Object Explorer  
  
-   In Object Explorer, right\-click the instance name, and then select **Activity Monitor**.  
  
#### When opening SQL Server Management Studio  
  
1.  On the **Tools** menu, click **Options**.  
  
2.  In the **Options** dialog box, expand **Environment**, and then select **General**.  
  
3.  In the **At startup** box, select **Open Object Explorer and Activity Monitor**.  
  
4.  To activate the changes, close and reopen [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
## Set the Activity Monitor refresh interval  
  
-   Open the Activity Monitor.  
  
-   Right\-click **Overview**, select **Refresh Interval**, and then select the interval in which Activity Monitor should obtain new instance information.  
  
  