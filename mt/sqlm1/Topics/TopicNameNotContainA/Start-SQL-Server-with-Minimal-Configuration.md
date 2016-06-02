---
title: Start SQL Server with Minimal Configuration
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d733c99-28b3-42d8-b7f6-7b943b548173
---
# Start SQL Server with Minimal Configuration
  If you have configuration problems that prevent the server from starting, you can start an instance of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] by using the minimal configuration startup option. This is the startup option **\-f**. Starting an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] with minimal configuration automatically puts the server in single\-user mode.  
  
 When you start an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in minimal configuration mode, note the following:  
  
-   Only a single user can connect, and the CHECKPOINT process is not executed.  
  
-   Remote access and read\-ahead are disabled.  
  
-   Startup stored procedures do not run.  
  
 After the server has been started with minimal configuration, you should change the appropriate server option value or values, stop, and then restart the server.  
  
> [!IMPORTANT]  
>  Use the **sqlcmd** utility and the dedicated administrator connection \(DAC\) to connect to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. If you use a typical connection, stop the SQL Server Agent service before connecting to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in minimal configuration mode. Otherwise, the SQL Server Agent service uses the connection, thereby blocking it.  
  
## See Also  
 [Start, Stop, or Pause the SQL Server Agent Service](../Topic/Start,%20Stop,%20or%20Pause%20the%20SQL%20Server%20Agent%20Service.md)   
 [Diagnostic Connection for Database Administrators](../../Topics\TopicNameNotContainA/Diagnostic-Connection-for-Database-Administrators.md)   
 [sqlcmd Utility](../../Topics\TopicNameNotContainA/sqlcmd-Utility.md)   
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)   
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)   
 [Database Engine Service Startup Options](../../Topics\TopicNameNotContainA/Database-Engine-Service-Startup-Options.md)  
  
  