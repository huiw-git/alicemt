---
title: "SQL Server Configuration Manager"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 2016-02-25
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e6beaea4-164c-4078-95ae-b9e28b0aefe8
caps.latest.revision: 58
caps.handback.revision: 0
manager: jhubbard
---
# SQL Server Configuration Manager
[!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager is a tool to manage the services associated with [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], to configure the network protocols used by [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], and to manage the network connectivity configuration from [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] client computers. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager is a [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Management Console snap-in that is available from the Start menu, or can be added to any other [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Management Console display. [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Management Console (**mmc.exe**) uses the **SQLServerManager<version\>.msc** file (such as **SQLServerManager13.msc** for [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)]) to open Configuration Manager. Here are the paths to the last four versions when Windows in installed on the C drive.  
  
|||  
|-|-|  
|[!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] 2016|C:\Windows\SysWOW64\SQLServerManager13.msc|  
|[!INCLUDE[ssSQL14](../../Topics/TopicNameContainA/tokens/ssSQL14_md.md)]|C:\Windows\SysWOW64\SQLServerManager12.msc|  
|[!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)]|C:\Windows\SysWOW64\SQLServerManager11.msc|  
|[!INCLUDE[ssKatmai](../../Topics/TopicNameContainA/tokens/ssKatmai_md.md)]|C:\Windows\SysWOW64\SQLServerManager10.msc|  
  
> [!NOTE]  
>  Because [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager is a snap-in for the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Management Console program and not a stand-alone program, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager does not appear as an application in newer versions of Windows.  
>   
>  -   **Windows 10**:  
>          To open [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager, on the **Start Page**, type SQLServerManager13.msc (for [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)]). For previous versions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] replace 13 with a smaller number. Clicking SQLServerManager13.msc opens the Configuration Manager. To pin the Configuration Manager to the Start Page or Task Bar, right-click SQLServerManager13.msc, and then click **Open file location**. In the Windows File Explorer, right-click SQLServerManager13.msc, and then click **Pin to Start** or **Pin to taskbar**.  
> -   **Windows 8**:  
>          To open [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager, in the **Search** charm, under **Apps**, type **SQLServerManager<version\>.msc** such as **SQLServerManager13.msc**, and then press **Enter**.  
  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager and SQL Server Management Studio use Window Management Instrumentation (WMI) to view and change some server settings. WMI provides a unified way for interfacing with the API calls that manage the registry operations requested by the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] tools and to provide enhanced control and manipulation over the selected SQL services of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager snap-in component. For information about configuring permissions related to WMI, see [How to: Configure WMI to Show Server Status in SQL Server Tools](assetId:///7e97197b-ed4d-40d1-9a52-9ab1d92401d7).  
  
 To start, stop, pause, resume, or configure services on another computer by using [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager, see [Connect to Another Computer (SQL Server Configuration Manager)](../../Topics/TopicNameNotContainA/Connect-to-Another-Computer--SQL-Server-Configuration-Manager-.md).  
  
## Managing Services  
 Use [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager to start, pause, resume, or stop the services, to view service properties, or to change service properties.  
  
 Use [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager to start the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] using startup parameters.  For more information, see [Configure Server Startup Options (SQL Server Configuration Manager)](../../Topics/TopicNameNotContainA/Configure-Server-Startup-Options--SQL-Server-Configuration-Manager-.md).  
  
## Changing the Accounts Used by the Services  
 Manage the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] services using [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager.  
  
> [!IMPORTANT]  
>  Always use [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] tools such as [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager to change the account used by the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] or [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent services, or to change the password for the account. In addition to changing the account name, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager performs additional configuration such as setting permissions in the Windows Registry so that the new account can read the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] settings. Other tools such as the Windows Services Control Manager can change the account name but do not change associated settings. If the service cannot access the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] portion of the registry the service may not start properly.  
  
 As an additional benefit, passwords changed using [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager, SMO, or WMI take affect immediately without restarting the service.  
  
## Manage Server & Client Network Protocols  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager allows you to configure server and client network protocols, and connectivity options. After the correct protocols are enabled, you usually do not need to change the server network connections. However, you can use [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager if you need to reconfigure the server connections so [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] listens on a particular network protocol, port, or pipe. For more information about enabling protocols, see [Enable or Disable a Server Network Protocol](../../Topics/TopicNameContainA/Enable-or-Disable-a-Server-Network-Protocol.md). For information about enabling access to protocols through a firewall, see [Configure the Windows Firewall to Allow SQL Server Access](../../Topics/TopicNameNotContainA/Configure-the-Windows-Firewall-to-Allow-SQL-Server-Access.md).  
  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager allows you to manage server and client network protocols, including the ability to force protocol encryption, view alias properties, or enable/disable a protocol.  
  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager allows you to create or remove an alias, change the order in which protocols are uses, or view properties for a server alias, including:  
  
-   Server Alias — The server alias used for the computer to which the client is connecting.  
  
-   Protocol — The network protocol used for the configuration entry.  
  
-   Connection Parameters — The parameters associated with the connection address for the network protocol configuration.  
  
 The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager also allows you to view information about failover cluster instances, though Cluster Administrator should be used for some actions such as starting and stopping the services.  
  
### Available Network Protocols  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] supports Shared Memory, TCP/IP, and Named Pipes protocols. For information about choosing a network protocols, see [Configure Client Protocols](../../Topics/TopicNameNotContainA/Configure-Client-Protocols.md). [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] does not support the VIA, Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk, or NWLink IPX/SPX network protocols. Clients previously connecting with these protocols must select a different protocol to connect to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. You cannot use [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager to configure the WinSock proxy. To configure the WinSock proxy, see your ISA Server documentation.  
  
## Related Tasks  
 [Managing Services How-to Topics (SQL Server Configuration Manager)](../../Topics/TopicNameNotContainA/Managing-Services-How-to-Topics--SQL-Server-Configuration-Manager-.md)  
  
 [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../Topics/TopicNameNotContainA/Start--Stop--Pause--Resume--Restart-the-Database-Engine--SQL-Server-Agent--or-SQL-Server-Browser-Service.md)  
  
 [Start, Stop, or Pause the SQL Server Agent Service](assetId:///c95a9759-dd30-4ab6-9ab0-087bb3bfb97c)  
  
 [Set an Instance of SQL Server to Start Automatically (SQL Server Configuration Manager)](../../Topics/TopicNameNotContainA/Set-an-Instance-of-SQL-Server-to-Start-Automatically--SQL-Server-Configuration-Manager-.md)  
  
 [Prevent Automatic Startup of an Instance of SQL Server (SQL Server Configuration Manager)](../../Topics/TopicNameNotContainA/Prevent-Automatic-Startup-of-an-Instance-of-SQL-Server--SQL-Server-Configuration-Manager-.md)