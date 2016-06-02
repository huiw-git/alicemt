---
title: Viewing the SQL Server Error Log
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6908c21a-65e3-458f-a272-fee256d86448
---
# Viewing the SQL Server Error Log
  View the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] error log to ensure that processes have completed successfully \(for example, backup and restore operations, batch commands, or other scripts and processes\). This can be helpful to detect any current or potential problem areas, including automatic recovery messages \(particularly if an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] has been stopped and restarted\), kernel messages, or other server\-level error messages.  
  
 View the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] error log by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or any text editor. For more information about how to view the error log, see [Open Log File Viewer](../../Topics\TopicNameNotContainA/Open-Log-File-Viewer.md). By default, the error log is located at `Program Files\Microsoft SQL Server\MSSQL.`*n*`\MSSQL\LOG\ERRORLOG` and `ERRORLOG.`*n* files.  
  
 A new error log is created each time an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is started, although the [sp\_cycle\_errorlog](../Topic/sp_cycle_errorlog%20\(Transact-SQL\).md) system stored procedure can be used to cycle the error log files without having to restart the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Typically, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] retains backups of the previous six logs and gives the most recent log backup the extension .1, the second most recent the extension .2, and so on. The current error log has no extension.  
  
 Be aware that you can also view the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] error log on instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that are offline or cannot start. For more information, see [View Offline Log Files](../../Topics\TopicNameNotContainA/View-Offline-Log-Files.md).  
  
  