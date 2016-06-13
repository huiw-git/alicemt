---
title: Manage the Database Engine Services
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aa732e43-53ba-4eea-bb9b-089da0766fc1
---
# Manage the Database Engine Services
  [!INCLUDE[msCoName](../../Token/Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] runs on the operating systems as a service. A service is a type of application that runs in the system background. Services usually provide core operating system features, such as Web serving, event logging, or file serving. Services can run without showing a user interface on the computer desktop. The [!INCLUDE[ssDEnoversion](../../Token/Other/ssDEnoversion_md.md)], [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] Agent, and several other [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] components run as services. These services typically are started when the operating system starts. This depends on what is specified during setup; some services are not started by default. This section describes the management of the various [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] services. Before you log in to an instance of [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)], you need to know how to start, stop, pause, resume, and restart an instance of [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)]. After you are logged in, you can perform tasks such as administering the server or querying a database.  
  
## Using the SQL Server Service  
 When you start an instance of [!INCLUDE[ssDEnoversion](../../Token/Other/ssDEnoversion_md.md)], you are starting the [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] service. After you start the [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] service, users can establish new connections to the server. The [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] service can be started and stopped as a service, either locally or remotely. The [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] service is referred to as [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] \(MSSQLSERVER\) if it is the default instance, or MSSQL$*\<instancename\>*if it is a named instance.  
  
## Using SQL Server Configuration Manager  
 [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] Configuration Manager allows you to stop, start, or pause various [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] services.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] Configuration Manager cannot manage [!INCLUDE[ssVersion2000](../../Token/Other/ssVersion2000_md.md)] services.  
  
 You can also use [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] Configuration Manager to view the properties of the selected service. [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] Configuration Manager is a [!INCLUDE[msCoName](../../Token/Other/msCoName_md.md)] Management Console \(MMC\) snap\-in. For more information about MMC and how a snap\-in works, see Windows Help.  
  
 **To access SQL Server Configuration Manager**  
  
-   On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../Token/Other/ssCurrentUI_md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.  
  
 **To access SQL Server Configuration Manager Using Windows 8**  
  
 Because [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] Configuration Manager is a snap\-in for the [!INCLUDE[msCoName](../../Token/Other/msCoName_md.md)] Management Console program and not a stand\-alone program, [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] Configuration Manager not does not appear as an application when running Windows 8.0. To open [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] Configuration Manager, in the **Search** charm, under **Apps**, type **SQLServerManager12.msc** \(for [!INCLUDE[ssSQL14](../../Token/Other/ssSQL14_md.md)]\), **SQLServerManager11.msc** \(for [!INCLUDE[ssSQL11](../../Token/Other/ssSQL11_md.md)]\), or **SQLServerManager10.msc** for \([!INCLUDE[ssKatmai](../../Token/Other/ssKatmai_md.md)]\), and then press **Enter**.  
  
## In this Section  
  
|||  
|-|-|  
|[Security Requirements for Managing Services](../../Topics/TopicNameNotContainA/Security-Requirements-for-Managing-Services.md)|[Prevent Automatic Startup of an Instance of SQL Server &#40;SQL Server Configuration Manager&#41;](../../Topics/TopicNameNotContainA/Prevent-Automatic-Startup-of-an-Instance-of-SQL-Server--SQL-Server-Configuration-Manager-.md)|  
|[Configure Windows Service Accounts and Permissions](../../Topics/TopicNameNotContainA/Configure-Windows-Service-Accounts-and-Permissions.md)|[Change the Service Startup Account for SQL Server &#40;SQL Server Configuration Manager&#41;](../../Topics/TopicNameNotContainA/Change-the-Service-Startup-Account-for-SQL-Server--SQL-Server-Configuration-Manager-.md)|  
|[Run SQL Server With or Without a Network](../../Topics/TopicNameContainA/Run-SQL-Server-With-or-Without-a-Network.md)|[Configure Server Startup Options &#40;SQL Server Configuration Manager&#41;](../../Topics/TopicNameNotContainA/Configure-Server-Startup-Options--SQL-Server-Configuration-Manager-.md)|  
|[SQL Server Browser Service &#40;Database Engine and SSAS&#41;](../../Topics/TopicNameNotContainA/SQL-Server-Browser-Service--Database-Engine-and-SSAS-.md)|[Change the Password of the Accounts Used by SQL Server &#40;SQL Server Configuration Manager&#41;](../../Topics/TopicNameNotContainA/Change-the-Password-of-the-Accounts-Used-by-SQL-Server--SQL-Server-Configuration-Manager-.md)|  
|[Database Engine Service Startup Options](../../Topics/TopicNameNotContainA/Database-Engine-Service-Startup-Options.md)|[Configure SQL Server Error Logs](../../Topics/TopicNameNotContainA/Configure-SQL-Server-Error-Logs.md)|  
|[Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../Topics/TopicNameNotContainA/Start--Stop--Pause--Resume--Restart-the-Database-Engine--SQL-Server-Agent--or-SQL-Server-Browser-Service.md)|[Change Server Authentication Mode](../../Topics/TopicNameNotContainA/Change-Server-Authentication-Mode.md)|  
|[Start SQL Server in Single-User Mode](../../Topics/TopicNameNotContainA/Start-SQL-Server-in-Single-User-Mode.md)|[SQL Writer Service](../../Topics/TopicNameNotContainA/SQL-Writer-Service.md)|  
|[Start SQL Server with Minimal Configuration](../../Topics/TopicNameNotContainA/Start-SQL-Server-with-Minimal-Configuration.md)|[Broadcast a Shutdown Message &#40;Command Prompt&#41;](../../Topics/TopicNameContainA/Broadcast-a-Shutdown-Message--Command-Prompt-.md)|  
|[Connect to Another Computer &#40;SQL Server Configuration Manager&#41;](../../Topics/TopicNameNotContainA/Connect-to-Another-Computer--SQL-Server-Configuration-Manager-.md)|[Log In to an Instance of SQL Server &#40;Command Prompt&#41;](../../Topics/TopicNameNotContainA/Log-In-to-an-Instance-of-SQL-Server--Command-Prompt-.md)|  
|[Set an Instance of SQL Server to Start Automatically &#40;SQL Server Configuration Manager&#41;](../../Topics/TopicNameNotContainA/Set-an-Instance-of-SQL-Server-to-Start-Automatically--SQL-Server-Configuration-Manager-.md)|[Configure File System Permissions for Database Engine Access](../../Topics/TopicNameNotContainA/Configure-File-System-Permissions-for-Database-Engine-Access.md)|  
  
## Related Content  
 [Configure SQL Server Agent](../Topic/Configure%20SQL%20Server%20Agent.md)  
  
 [Logging In to SQL Server](../../Topics/TopicNameNotContainA/Logging-In-to-SQL-Server.md)  
  
  