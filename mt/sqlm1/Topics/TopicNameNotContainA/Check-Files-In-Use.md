---
title: Check Files In Use
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ccd65867-d4c0-43b2-8361-7fd41c6f79ac
---
# Check Files In Use
  To avoid restarting Windows after you install [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] updates, use the Check Files in Use page to identify processes that are locking files required by the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] update Setup program.  
  
 Stop all applications and services that make connections to the instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that are being updated. This includes stopping [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] and [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)].  
  
 If Setup determines that files are locked during installation, you might have to restart your computer after installation is completed. If necessary, Setup prompts you to restart your computer. If the Setup program must stop a service during installation, it will restart the service after installation is completed.  
  
 To eliminate the requirement to restart your computer after installation, Setup displays a list of processes that are locking files. Stop or end the processes and applications in the list. Then click **Refresh check** to rerun the check. Click **Stop check** to end a check that is running. If locked files are not found, the table is empty. When all locked processes have been closed or stopped, click **Next** to continue.  
  
 Setup logs the information in the log files. For more information about how to view the log files, see [View and Read SQL Server Setup Log Files](../../Topics\TopicNameNotContainA/View-and-Read-SQL-Server-Setup-Log-Files.md) and [How to: Read a SQL Server Setup Log File](http://go.microsoft.com/fwlink/?LinkID=134490).  
  
 The following information is included in the log file:  
  
-   Name of the process  
  
-   Name of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] feature  
  
-   Process type  
  
-   Account under which the process is running  
  
-   Process ID  
  
-   Name of the file that is locked  
  
## UIElement List  
  
|Name|Description|  
|----------|-----------------|  
|Process|Displays the full name of the process that is using the files to be updated.|  
|Type|Displays the type of process.|  
|Account|Displays the account under which the process is running.|  
|Process ID|Displays the process ID.|  
  
  