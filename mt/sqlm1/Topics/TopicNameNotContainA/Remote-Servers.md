---
title: Remote Servers
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: abf0fa24-f199-4273-9a1a-e8787ac9bee1
---
# Remote Servers
  Remote servers are supported in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] for backward compatibility only. New applications should use linked servers instead. For more information, see [Linked Servers &#40;Database Engine&#41;](../Topic/Linked%20Servers%20\(Database%20Engine\).md).  
  
 A remote server configuration allows for a client connected to one instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to execute a stored procedure on another instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] without establishing a separate connection. Instead, the server to which the client is connected accepts the client request and sends the request to the remote server on behalf of the client. The remote server processes the request and returns any results to the original server. This server in turn passes those results to the client. When you set up a remote server configuration, you should also consider how to establish security.  
  
 If you want to set up a server configuration to execute stored procedures on another server and do not have existing remote server configurations, use linked servers instead of remote servers. Both stored procedures and distributed queries are allowed against linked servers; however, only stored procedures are allowed against remote servers.  
  
## Remote Server Details  
 Remote servers are set up in pairs. To set up a pair of remote servers, configure both servers to recognize each other as remote servers.  
  
 Most of the time, you should not have to set configuration options for remote servers. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Set sets the defaults on both the local and remote computers to allow for remote server connections.  
  
 For remote server access to work, the **remote access** configuration option must be set to 1 on both the local and remote computers. \(This is the default setting.\)  **remote access** controls logins from remote servers. You can reset this configuration option by using either the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] **sp\_configure** stored procedure or [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. To set the option in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], on the **Server Properties Connections** page, use **Allow remote connections to this server**. To reach the **Server Properties Connections** page, in Object Explorer, right\-click the server name, and then click **Properties**. On the **Server Properties** page, click the **Connections** page.  
  
 From the local server, you can disable a remote server configuration to prevent access to that local server by users on the remote server with which it is paired.  
  
## Security for Remote Servers  
 To enable remote procedure calls \(RPC\) against a remote server, you must set up login mappings on the remote server and possibly on the local server that is running an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. RPC is disabled by default in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. This configuration enhances the security of your server by reducing its attackable surface area. Before using RPC you must enable this feature. For more information see [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md).  
  
### Setting Up the Remote Server  
 Remote login mappings must be set up on the remote server. Using these mappings, the remote server maps the incoming login for an RPC connection from a specified server to a local login. Remote login mappings can be set up by using the **sp\_addremotelogin** stored procedure on the remote server.  
  
> [!NOTE]  
>  The **trusted** option of  **sp\_remoteoption** is not supported in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
### Setting Up the Local Server  
 For [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] authenticated local logins, you do not have to set up a login mapping on the local server. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] uses the local login and password to connect to the remote server. For Windows authenticated logins, set up a local login mapping on a local server that defines what login and password are used by an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] when it makes an RPC connection to a remote server.  
  
 For logins created by Windows Authentication, you must create a mapping to a login name and password by using the **sp\_addlinkedservlogin** stored procedure. This login name and password must match the incoming login and password expected by the remote server, as created by **sp\_addremotelogin**.  
  
> [!NOTE]  
>  When possible, use Windows Authentication.  
  
### Remote Server Security Example  
 Consider these [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installations: **serverSend** and **serverReceive**. **serverReceive** is configured to map an incoming login from **serverSend**, called **Sales\_Mary**, to a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] authenticated login in **serverReceive**, called **Alice**. Another incoming login from **serverSend**, called **Joe**, is mapped to a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] authenticated login in **serverReceive***,* called **Joe**.  
  
 The following Transact\-SQL code example configures `serverSend` to perform RPCs against `serverReceive`.  
  
```  
--Create remote server entry for RPCs   
--from serverSend in serverReceive.  
EXEC sp_addserver 'serverSend';  
GO  
  
--Create remote login mapping for login 'Sales_Mary' from serverSend  
--to Alice.  
EXEC sp_addremotelogin 'serverSend', 'Alice', 'Sales_Mary';  
GO  
--Create remote login mapping for login Joe from serverReceive   
--to same login.  
--Assumes same password for Joe in both servers.  
EXEC sp_addremotelogin 'serverSend', 'Joe', 'Joe';  
GO  
```  
  
 On `serverSend`, a local login mapping is created for a Windows authenticated login `Sales\Mary` to a login `Sales_Mary`. No local mapping is required for `Joe`, because the default is to use the same login name and password, and `serverReceive` has a mapping for `Joe`.  
  
```  
--Create a remote server entry for RPCs from serverReceive.  
EXEC sp_addserver 'serverReceive';  
GO  
--Create a local login mapping for the Windows authenticated login.  
--Sales\Mary to Sales_Mary. The password should match the  
--password for the login Sales_Mary in serverReceive.  
EXEC sp_addlinkedsrvlogin 'serverReceive', false, 'Sales\Mary',  
   'Sales_Mary', '430[fj%dk';  
GO  
```  
  
## Viewing Local or Remote Server Properties  
 You can use the **xp\_msver** extended stored procedure to review server attributes for local or remote servers. These attributes include the version number of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], the type and number of processors in the computer, and the version of the operating system. From the local server, you can view databases, files, logins, and tools for a remote server. For more information, see [xp_msver &#40;Transact-SQL&#41;](../Topic/xp_msver%20\(Transact-SQL\).md).  
  
## Related Tasks  
 [Linked Servers &#40;Database Engine&#41;](../Topic/Linked%20Servers%20\(Database%20Engine\).md)  
  
## Related Content  
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)  
  
 [Configure the remote access Server Configuration Option](../../Topics\TopicNameNotContainA/Configure-the-remote-access-Server-Configuration-Option.md)  
  
 [RECONFIGURE &#40;Transact-SQL&#41;](../Topic/RECONFIGURE%20\(Transact-SQL\).md)  
  
  