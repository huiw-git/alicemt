---
title: Network Protocols and Network Libraries
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8cd437f6-9af1-44ce-9cb0-4d10c83da9ce
---
# Network Protocols and Network Libraries
  A server can listen on, or monitor, multiple network protocols at one time. However, each protocol must be configured. If a particular protocol is not configured, the server cannot listen on that protocol. After installation, you can change the protocol configurations using the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager.  
  
## Default SQL Server Network Configuration  
 A default instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is configured for TCP\/IP port 1433, and named pipe \\\\.\\pipe\\sql\\query. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] named instances are configured for TCP dynamic ports, with a port number assigned by the operating system.  
  
 If you cannot use dynamic port addresses \(for example, when [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] connections must pass through a firewall server configured to pass through specific port addresses\). Select an unassigned port number. Port number assignments are managed by the Internet Assigned Numbers Authority and are listed at [http:\/\/www.iana.org](http://go.microsoft.com/fwlink/?LinkId=48844).  
  
 To enhance security, network connectivity is not fully enabled when [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is installed. To enable, disable, and configure network protocols after Setup is complete, use the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Network Configuration area of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager.  
  
## Server Message Block Protocol  
 Servers in the perimeter network should have all unnecessary protocols disabled, including server message block \(SMB\). Web servers and Domain Name System \(DNS\) servers do not require SMB. This protocol should be disabled to counter the threat of user enumeration.  
  
> [!WARNING]  
>  Disabling Server Message Block will block the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or Windows Cluster service from accessing the remote file share. Do not disable SMB if you do or plan to do one of the following:  
>   
>  -   Use Windows Cluster Node and File Share Majority Quorum mode  
> -   Specify an SMB file share as the data directory during [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installation  
> -   Create a database file on an SMB file share  
  
#### To disable SMB  
  
1.  On the **Start** menu, point to **Settings**, and then click **Network and Dial\-up Connections**.  
  
     Right\-click the Internet\-facing connection, and then click **Properties**.  
  
2.  Select the **Client for Microsoft Networks** check box, and then click **Uninstall**.  
  
3.  Follow the uninstall steps.  
  
4.  Select **File and Printer Sharing for Microsoft Networks**, and then click **Uninstall**.  
  
5.  Follow the uninstall steps.  
  
#### To disable SMB on servers accessible from the Internet  
  
-   In the Local Area Connection properties, use the **Transmission Control Protocol\/Internet Protocol \(TCP\/IP\) properties** dialog box to remove **File and Printer Sharing for Microsoft Networks** and **Client for Microsoft Networks**.  
  
## Endpoints  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] introduces a new concept for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] connections; the connection is represented on the server end by a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]*endpoint*. Permissions can be granted, revoked, and denied for [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] endpoints. By default, all users have permissions to access an endpoint unless the permissions are denied or revoked by a member of the sysadmin group or by the endpoint owner. The GRANT, REVOKE, and DENY ENDPOINT syntax uses an endpoint ID that the administrator must get from the endpoint's catalog view.  
  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup creates [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] endpoints for all supported network protocols, as well as for the dedicated administrator connection.  
  
 [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] endpoints created by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup are as follows:  
  
-   [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] local machine  
  
-   [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] named pipes  
  
-   [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] default TCP  
  
 For more information about endpoints, see [Configure the Database Engine to Listen on Multiple TCP Ports](../../Topics\TopicNameNotContainA/Configure-the-Database-Engine-to-Listen-on-Multiple-TCP-Ports.md) and [Endpoints Catalog Views &#40;Transact-SQL&#41;](../Topic/Endpoints%20Catalog%20Views%20\(Transact-SQL\).md).  
  
 For more information about [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] network configurations, see the following topics in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Books Online:  
  
-   [Server Network Configuration](../../Topics\TopicNameNotContainA/Server-Network-Configuration.md)  
  
## See Also  
 [Surface Area Configuration](../../Topics\TopicNameNotContainA/Surface-Area-Configuration.md)   
 [Security Considerations for a SQL Server Installation](../../Topics\TopicNameContainA/Security-Considerations-for-a-SQL-Server-Installation.md)   
 [Planning a SQL Server Installation](../../Topics\TopicNameContainA/Planning-a-SQL-Server-Installation.md)  
  
  