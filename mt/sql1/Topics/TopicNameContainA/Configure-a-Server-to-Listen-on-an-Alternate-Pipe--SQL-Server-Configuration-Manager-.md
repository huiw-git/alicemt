---
title: "Configure a Server to Listen on an Alternate Pipe (SQL Server Configuration Manager)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 914f7491-e2be-4b0d-b3aa-fe5409cdbafa
caps.latest.revision: 29
caps.handback.revision: 0
manager: jhubbard
---
# Configure a Server to Listen on an Alternate Pipe (SQL Server Configuration Manager)
This topic describes how to configure a server to listen on an alternate pipe in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] by using SQL Server Configuration Manager. By default, the default instance of [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)] listens on named pipe \\\\.\pipe\sql\query. Named instances of [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)] and [!INCLUDE[ssEW](../../Topics/TopicNameContainA/tokens/ssEW_md.md)] listen on other pipes.  
  
 There are three ways to connect to a specific named pipe with a client application:  
  
-   Run the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Browser service on the server.  
  
-   Create an alias on the client, specifying the named pipe.  
  
-   Program the client to connect using a custom connection string.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Configuration Manager  
  
#### To configure the named pipe used by the SQL Server Database Engine  
  
1.  In SQL Server Configuration Manager, in the console pane, expand **SQL Server Network Configuration**, and then click expand **Protocols for** *<instance name\>*.  
  
2.  In the details pane, right-click **Named Pipes**, and then click **Properties**.  
  
3.  On the **Protocol** tab, in the **Pipe Name** box, type the pipe you want the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] to listen on, and then click **OK**.  
  
4.  In the console pane, click **SQL Server Services**.  
  
5.  In the details pane, right-click **SQL Server (**<instance name\>**)** and then click **Restart**, to stop and restart [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
 When [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is listening on an alternate pipe, there are three ways to connect to a specific named pipe with a client application:  
  
-   Run the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Browser service on the server.  
  
-   Create an alias on the client, specifying the named pipe.  
  
-   Program the client to connect using a custom connection string.  
  
## See Also  
 [Create or Delete a Server Alias for Use by a Client (SQL Server Configuration Manager)](../../Topics/TopicNameContainA/Create-or-Delete-a-Server-Alias-for-Use-by-a-Client--SQL-Server-Configuration-Manager-.md)   
 [Server Network Configuration](../../Topics/TopicNameNotContainA/Server-Network-Configuration.md)