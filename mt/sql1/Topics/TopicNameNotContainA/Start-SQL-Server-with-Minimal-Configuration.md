---
title: "Start SQL Server with Minimal Configuration"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d733c99-28b3-42d8-b7f6-7b943b548173
caps.latest.revision: 27
caps.handback.revision: 0
manager: jhubbard
---
# Start SQL Server with Minimal Configuration
If you have configuration problems that prevent the server from starting, you can start an instance of [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] by using the minimal configuration startup option. This is the startup option **-f**. Starting an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] with minimal configuration automatically puts the server in single-user mode.  
  
 When you start an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] in minimal configuration mode, note the following:  
  
-   Only a single user can connect, and the CHECKPOINT process is not executed.  
  
-   Remote access and read-ahead are disabled.  
  
-   Startup stored procedures do not run.  
  
 After the server has been started with minimal configuration, you should change the appropriate server option value or values, stop, and then restart the server.  
  
> [!IMPORTANT]  
>  Use the **sqlcmd** utility and the dedicated administrator connection (DAC) to connect to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. If you use a typical connection, stop the SQL Server Agent service before connecting to an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] in minimal configuration mode. Otherwise, the SQL Server Agent service uses the connection, thereby blocking it.  
  
## See Also  
 [Start, Stop, or Pause the SQL Server Agent Service](assetId:///c95a9759-dd30-4ab6-9ab0-087bb3bfb97c)   
 [Diagnostic Connection for Database Administrators](../../Topics/TopicNameNotContainA/Diagnostic-Connection-for-Database-Administrators.md)   
 [sqlcmd Utility](../../Topics/TopicNameNotContainA/sqlcmd-Utility.md)   
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)   
 [Database Engine Service Startup Options](../../Topics/TopicNameNotContainA/Database-Engine-Service-Startup-Options.md)