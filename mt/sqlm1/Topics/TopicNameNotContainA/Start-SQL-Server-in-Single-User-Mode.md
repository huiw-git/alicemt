---
title: Start SQL Server in Single-User Mode
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 72eb4fc1-7af4-4ec6-9e02-11a69e02748e
---
# Start SQL Server in Single-User Mode
  Under certain circumstances, you may have to start an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in single\-user mode by using the **startup option \-m.** For example, you may want to change server configuration options or recover a damaged master database or other system database. Both actions require starting an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in single\-user mode.  
  
 Starting [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in single\-user mode enables any member of the computer's local Administrators group to connect to the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] as a member of the sysadmin fixed server role. For more information, see [Connect to SQL Server When System Administrators Are Locked Out](../../Topics\TopicNameNotContainA/Connect-to-SQL-Server-When-System-Administrators-Are-Locked-Out.md).  
  
 When you start an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in single\-user mode, note the following:  
  
-   Only one user can connect to the server.  
  
-   The CHECKPOINT process is not executed. By default, it is executed automatically at startup.  
  
> [!NOTE]  
>  Stop the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent service before connecting to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in single\-user mode; otherwise, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent service uses the connection, thereby blocking it.  
  
 When you start an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in single\-user mode, [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] can connect to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Object Explorer in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] might fail because it requires more than one connection for some operations. To manage [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in single\-user mode, execute [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements by connecting only through the Query Editor in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)], or use the [sqlcmd utility](../../Topics\TopicNameNotContainA/sqlcmd-Utility.md).  
  
 When you use the **\-m** option with **sqlcmd** or [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)], you can limit the connections to a specified client application. For example, **\-m"sqlcmd"** limits connections to a single connection and that connection must identify itself as the **sqlcmd** client program. Use this option when you are starting [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in single\-user mode and an unknown client application is taking the only available connection. To connect through the Query Editor in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)], use **\-m"Microsoft SQL Server Management Studio \- Query"**.  
  
> [!IMPORTANT]  
>  Do not use this option as a security feature. The client application provides the client application name, and can provide a false name as part of the connection string.  
  
## Note for Clustered installations  
 For [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installation in a clustered environment, when [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is started in single user mode, the cluster resource dll uses up the available connection thereby blocking any other connections to the server. When [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is in this state, if you try to bring [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent resource online, it may fail over the SQL resource to a different node if the resource is configured to affect the group.  
  
 To get around the problem use the following procedure:  
  
1.  Remove the –m startup parameter from the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] advanced Properties.  
  
2.  Take the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] resource offline.  
  
3.  From the current owner node of this group, issue the following command from the command prompt:  
    net start MSSQLSERVER \/m.  
  
4.  Verify from the cluster administrator or failover cluster management console that the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] resource is still offline.  
  
5.  Connect to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] now using the following command and do the necessary operation: SQLCMD \-E \-S\<servername\>.  
  
6.  Once the operation is complete, close the command prompt and bring back the SQL and other resources online through cluster administrator.  
  
## See Also  
 [Start, Stop, or Pause the SQL Server Agent Service](../Topic/Start,%20Stop,%20or%20Pause%20the%20SQL%20Server%20Agent%20Service.md)   
 [Diagnostic Connection for Database Administrators](../../Topics\TopicNameNotContainA/Diagnostic-Connection-for-Database-Administrators.md)   
 [sqlcmd Utility](../../Topics\TopicNameNotContainA/sqlcmd-Utility.md)   
 [CHECKPOINT &#40;Transact-SQL&#41;](../Topic/CHECKPOINT%20\(Transact-SQL\).md)   
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)   
 [Database Engine Service Startup Options](../../Topics\TopicNameNotContainA/Database-Engine-Service-Startup-Options.md)  
  
  