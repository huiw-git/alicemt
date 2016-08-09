---
title: "Viewing the SQL Server Error Log"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6908c21a-65e3-458f-a272-fee256d86448
caps.latest.revision: 25
caps.handback.revision: 0
manager: jhubbard
---
# Viewing the SQL Server Error Log
View the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] error log to ensure that processes have completed successfully (for example, backup and restore operations, batch commands, or other scripts and processes). This can be helpful to detect any current or potential problem areas, including automatic recovery messages (particularly if an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] has been stopped and restarted), kernel messages, or other server-level error messages.  
  
 View the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] error log by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or any text editor. For more information about how to view the error log, see [Open Log File Viewer](../../Topics/TopicNameNotContainA/Open-Log-File-Viewer.md). By default, the error log is located at `Program Files\Microsoft SQL Server\MSSQL.`*n*`\MSSQL\LOG\ERRORLOG` and `ERRORLOG.`*n* files.  
  
 A new error log is created each time an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is started, although the [sp_cycle_errorlog](assetId:///61a12cbf-78a3-4052-8604-3b29d07573fd) system stored procedure can be used to cycle the error log files without having to restart the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. Typically, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] retains backups of the previous six logs and gives the most recent log backup the extension .1, the second most recent the extension .2, and so on. The current error log has no extension.  
  
 Be aware that you can also view the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] error log on instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] that are offline or cannot start. For more information, see [View Offline Log Files](../../Topics/TopicNameNotContainA/View-Offline-Log-Files.md).