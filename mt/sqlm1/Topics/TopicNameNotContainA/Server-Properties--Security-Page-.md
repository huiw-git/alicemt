---
title: Server Properties (Security Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b8a131c7-e7bd-4203-bf26-234f1ebfe622
---
# Server Properties (Security Page)
  Use this page to view or modify your server security options.  
  
## Server Authentication  
 **Windows Authentication mode**  
 Uses Windows Authentication to validate attempted connections. If the **sa** password is blank when the security mode is being changed, the user is prompted to enter an **sa** password.  
  
> [!IMPORTANT]  
>  Windows Authentication is much more secure than SQL Server Authentication. When possible, you should use Windows Authentication.  
  
 **SQL Server and Windows Authentication mode**  
 Uses mixed mode authentication to verify attempted connections, for backward compatibility with earlier versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. If the **sa** password is blank when the security mode is being changed, the user is prompted to enter an **sa** password.  
  
> [!NOTE]  
>  Changing the security configuration requires a restart of the service. When changing the Server Authentication to SQL Server and Windows Authentication mode the SA account is not automatically enabled. To use the SA account, execute [ALTER LOGIN](../Topic/ALTER%20LOGIN%20\(Transact-SQL\).md) with the ENABLE option.  
  
## Login Auditing  
 **None**  
 Turns off login auditing.  
  
 **Failed logins only**  
 Audits unsuccessful logins only.  
  
 **Successful logins only**  
 Audits successful logins only.  
  
 **Both failed and successful logins**  
 Audits all login attempts.  
  
> [!NOTE]  
>  Changing the audit level requires restarting the service.  
  
## Server Proxy Account  
 **Enable server proxy account**  
 Enables an account for use by **xp\_cmdshell**. Proxy accounts allow for the impersonation of logins, server roles, and database roles when an operating system command is being executed.  
  
> [!CAUTION]  
>  The login used by the server proxy account should have the least privileges required to perform the intended work. Excessive privileges for the proxy account could be used by a malicious user to compromise your system security.  
  
 **Proxy account**  
 Specify the proxy account used.  
  
 **Password**  
 Specify the password for the proxy account.  
  
## Options  
 **Enable C2 audit tracing**  
 Audits all attempts to access statements and objects and records them to a file in the \\MSSQL\\Data directory for default instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], or the \\MSSQL$*instancename*\\Data directory for named instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. For more information, see [c2 audit mode Server Configuration Option](../../Topics\TopicNameNotContainA/c2-audit-mode-Server-Configuration-Option.md).  
  
 **Cross database ownership chaining**  
 Select to allow the database to be the source or target of a cross\-database ownership chain. For more information, see [cross db ownership chaining Server Configuration Option](../../Topics\TopicNameNotContainA/cross-db-ownership-chaining-Server-Configuration-Option.md).  
  
## See Also  
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)  
  
  