---
title: SQL Server Configuration Manager
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e6beaea4-164c-4078-95ae-b9e28b0aefe8
---
# SQL Server Configuration Manager
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager is a tool to manage the services associated with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], to configure the network protocols used by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], and to manage the network connectivity configuration from [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] client computers. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager is a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Management Console snap\-in that is available from the Start menu, or can be added to any other [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Management Console display. [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Management Console \(**mmc.exe**\) uses the **SQLServerManager\<version\>.msc** file \(such as **SQLServerManager13.msc** for [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)]\) to open Configuration Manager. Here are the paths to the last four versions when Windows in installed on the C drive.  
  
|||  
|-|-|  
|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] 2016|C:\\Windows\\SysWOW64\\SQLServerManager13.msc|  
|[!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)]|C:\\Windows\\SysWOW64\\SQLServerManager12.msc|  
|[!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)]|C:\\Windows\\SysWOW64\\SQLServerManager11.msc|  
|[!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)]|C:\\Windows\\SysWOW64\\SQLServerManager10.msc|  
  
> [!NOTE]  
>  Because [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager is a snap\-in for the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Management Console program and not a stand\-alone program, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager does not appear as an application in newer versions of Windows.  
>   
>  -   **Windows 10**:  
>          To open [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager, on the **Start Page**, type SQLServerManager13.msc \(for [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)]\). For previous versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] replace 13 with a smaller number. Clicking SQLServerManager13.msc opens the Configuration Manager. To pin the Configuration Manager to the Start Page or Task Bar, right\-click SQLServerManager13.msc, and then click **Open file location**. In the Windows File Explorer, right\-click SQLServerManager13.msc, and then click **Pin to Start** or **Pin to taskbar**.  
> -   **Windows 8**:  
>          To open [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager, in the **Search** charm, under **Apps**, type **SQLServerManager\<version\>.msc** such as **SQLServerManager13.msc**, and then press **Enter**.  
  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager and SQL Server Management Studio use Window Management Instrumentation \(WMI\) to view and change some server settings. WMI provides a unified way for interfacing with the API calls that manage the registry operations requested by the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] tools and to provide enhanced control and manipulation over the selected SQL services of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager snap\-in component. For information about configuring permissions related to WMI, see [Configure WMI to Show Server Status in SQL Server Tools](../Topic/Configure%20WMI%20to%20Show%20Server%20Status%20in%20SQL%20Server%20Tools.md).  
  
 To start, stop, pause, resume, or configure services on another computer by using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager, see [Connect to Another Computer &#40;SQL Server Configuration Manager&#41;](../Topic/Connect%20to%20Another%20Computer%20\(SQL%20Server%20Configuration%20Manager\).md).  
  
## Managing Services  
 Use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager to start, pause, resume, or stop the services, to view service properties, or to change service properties.  
  
 Use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager to start the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] using startup parameters.  For more information, see [Configure Server Startup Options &#40;SQL Server Configuration Manager&#41;](../Topic/Configure%20Server%20Startup%20Options%20\(SQL%20Server%20Configuration%20Manager\).md).  
  
## Changing the Accounts Used by the Services  
 Manage the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] services using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager.  
  
> [!IMPORTANT]  
>  Always use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] tools such as [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager to change the account used by the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent services, or to change the password for the account. In addition to changing the account name, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager performs additional configuration such as setting permissions in the Windows Registry so that the new account can read the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] settings. Other tools such as the Windows Services Control Manager can change the account name but do not change associated settings. If the service cannot access the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] portion of the registry the service may not start properly.  
  
 As an additional benefit, passwords changed using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager, SMO, or WMI take affect immediately without restarting the service.  
  
## Manage Server & Client Network Protocols  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager allows you to configure server and client network protocols, and connectivity options. After the correct protocols are enabled, you usually do not need to change the server network connections. However, you can use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager if you need to reconfigure the server connections so [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] listens on a particular network protocol, port, or pipe. For more information about enabling protocols, see [Enable or Disable a Server Network Protocol](../../Topics\TopicNameContainA/Enable-or-Disable-a-Server-Network-Protocol.md). For information about enabling access to protocols through a firewall, see [Configure the Windows Firewall to Allow SQL Server Access](../../Topics\TopicNameNotContainA/Configure-the-Windows-Firewall-to-Allow-SQL-Server-Access.md).  
  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager allows you to manage server and client network protocols, including the ability to force protocol encryption, view alias properties, or enable\/disable a protocol.  
  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager allows you to create or remove an alias, change the order in which protocols are uses, or view properties for a server alias, including:  
  
-   Server Alias — The server alias used for the computer to which the client is connecting.  
  
-   Protocol — The network protocol used for the configuration entry.  
  
-   Connection Parameters — The parameters associated with the connection address for the network protocol configuration.  
  
 The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager also allows you to view information about failover cluster instances, though Cluster Administrator should be used for some actions such as starting and stopping the services.  
  
### Available Network Protocols  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] supports Shared Memory, TCP\/IP, and Named Pipes protocols. For information about choosing a network protocols, see [Configure Client Protocols](../../Topics\TopicNameNotContainA/Configure-Client-Protocols.md). [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] does not support the VIA, Banyan VINES Sequenced Packet Protocol \(SPP\), Multiprotocol, AppleTalk, or NWLink IPX\/SPX network protocols. Clients previously connecting with these protocols must select a different protocol to connect to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. You cannot use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager to configure the WinSock proxy. To configure the WinSock proxy, see your ISA Server documentation.  
  
## Related Tasks  
 [Managing Services How-to Topics &#40;SQL Server Configuration Manager&#41;](../Topic/Managing%20Services%20How-to%20Topics%20\(SQL%20Server%20Configuration%20Manager\).md)  
  
 [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../Topics\TopicNameNotContainA/Start,-Stop,-Pause,-Resume,-Restart-the-Database-Engine,-SQL-Server-Agent,-or-SQL-Server-Browser-Service.md)  
  
 [Start, Stop, or Pause the SQL Server Agent Service](../Topic/Start,%20Stop,%20or%20Pause%20the%20SQL%20Server%20Agent%20Service.md)  
  
 [Set an Instance of SQL Server to Start Automatically &#40;SQL Server Configuration Manager&#41;](../Topic/Set%20an%20Instance%20of%20SQL%20Server%20to%20Start%20Automatically%20\(SQL%20Server%20Configuration%20Manager\).md)  
  
 [Prevent Automatic Startup of an Instance of SQL Server &#40;SQL Server Configuration Manager&#41;](../Topic/Prevent%20Automatic%20Startup%20of%20an%20Instance%20of%20SQL%20Server%20\(SQL%20Server%20Configuration%20Manager\).md)  
  
  