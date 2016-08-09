---
title: "Remote Servers"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: abf0fa24-f199-4273-9a1a-e8787ac9bee1
caps.latest.revision: 30
caps.handback.revision: 0
manager: jhubbard
---
# Remote Servers
Remote servers are supported in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] for backward compatibility only. New applications should use linked servers instead. For more information, see [Linked Servers (Database Engine)](../../Topics/TopicNameNotContainA/Linked-Servers--Database-Engine-.md).  
  
 A remote server configuration allows for a client connected to one instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] to execute a stored procedure on another instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] without establishing a separate connection. Instead, the server to which the client is connected accepts the client request and sends the request to the remote server on behalf of the client. The remote server processes the request and returns any results to the original server. This server in turn passes those results to the client. When you set up a remote server configuration, you should also consider how to establish security.  
  
 If you want to set up a server configuration to execute stored procedures on another server and do not have existing remote server configurations, use linked servers instead of remote servers. Both stored procedures and distributed queries are allowed against linked servers; however, only stored procedures are allowed against remote servers.  
  
## Remote Server Details  
 Remote servers are set up in pairs. To set up a pair of remote servers, configure both servers to recognize each other as remote servers.  
  
 Most of the time, you should not have to set configuration options for remote servers. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Set sets the defaults on both the local and remote computers to allow for remote server connections.  
  
 For remote server access to work, the **remote access** configuration option must be set to 1 on both the local and remote computers. (This is the default setting.)  **remote access** controls logins from remote servers. You can reset this configuration option by using either the [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] **sp_configure** stored procedure or [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)]. To set the option in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], on the **Server Properties Connections** page, use **Allow remote connections to this server**. To reach the **Server Properties Connections** page, in Object Explorer, right-click the server name, and then click **Properties**. On the **Server Properties** page, click the **Connections** page.  
  
 From the local server, you can disable a remote server configuration to prevent access to that local server by users on the remote server with which it is paired.  
  
## Security for Remote Servers  
 To enable remote procedure calls (RPC) against a remote server, you must set up login mappings on the remote server and possibly on the local server that is running an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. RPC is disabled by default in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. This configuration enhances the security of your server by reducing its attackable surface area. Before using RPC you must enable this feature. For more information see [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8).  
  
### Setting Up the Remote Server  
 Remote login mappings must be set up on the remote server. Using these mappings, the remote server maps the incoming login for an RPC connection from a specified server to a local login. Remote login mappings can be set up by using the **sp_addremotelogin** stored procedure on the remote server.  
  
> [!NOTE]  
>  The **trusted** option of  **sp_remoteoption** is not supported in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
### Setting Up the Local Server  
 For [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] authenticated local logins, you do not have to set up a login mapping on the local server. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] uses the local login and password to connect to the remote server. For Windows authenticated logins, set up a local login mapping on a local server that defines what login and password are used by an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] when it makes an RPC connection to a remote server.  
  
 For logins created by Windows Authentication, you must create a mapping to a login name and password by using the **sp_addlinkedservlogin** stored procedure. This login name and password must match the incoming login and password expected by the remote server, as created by **sp_addremotelogin**.  
  
> [!NOTE]  
>  When possible, use Windows Authentication.  
  
### Remote Server Security Example  
 Consider these [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] installations: **serverSend** and **serverReceive**. **serverReceive** is configured to map an incoming login from **serverSend**, called **Sales_Mary**, to a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] authenticated login in **serverReceive**, called **Alice**. Another incoming login from **serverSend**, called **Joe**, is mapped to a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] authenticated login in **serverReceive***,* called **Joe**.  
  
 The following Transact-SQL code example configures `serverSend` to perform RPCs against `serverReceive`.  
  
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
 You can use the **xp_msver** extended stored procedure to review server attributes for local or remote servers. These attributes include the version number of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], the type and number of processors in the computer, and the version of the operating system. From the local server, you can view databases, files, logins, and tools for a remote server. For more information, see [xp_msver (Transact-SQL)](assetId:///9264cf8c-92ba-45ad-b2d6-15d26d805a16).  
  
## Related Tasks  
 [Linked Servers (Database Engine)](../../Topics/TopicNameNotContainA/Linked-Servers--Database-Engine-.md)  
  
## Related Content  
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)  
  
 [Configure the remote access Server Configuration Option](../../Topics/TopicNameNotContainA/Configure-the-remote-access-Server-Configuration-Option.md)  
  
 [RECONFIGURE (Transact-SQL)](assetId:///2e6e4eeb-b70b-4f45-a253-28ac4e595d75)