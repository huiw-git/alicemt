---
title: "Create a New Registered Server (SQL Server Management Studio)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 716ea070-a3b5-4514-9de2-82ce8a96514b
caps.latest.revision: 31
caps.handback.revision: 0
manager: jhubbard
---
# Create a New Registered Server (SQL Server Management Studio)
This topic describes how to save the connection information for servers that you access frequently, by registering the server in the Registered Servers component of [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)]. A server can be registered before connecting, or when connecting from Object Explorer. There is a special menu option to register the server instances on the local computer.  
  
 There are two kinds of registered servers:  
  
-   Local server groups  
  
     Use local server groups to easily connect to servers that you frequently manage. Both local and non-local servers are registered into local server groups. Local server groups are unique to each user. For information about how to share registered server information, see [Export Registered Server Information (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Export-Registered-Server-Information--SQL-Server-Management-Studio-.md) and [Import Registered Server Information (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Import-Registered-Server-Information--SQL-Server-Management-Studio-.md).  
  
    > [!NOTE]  
    >  We recommend that you use Windows Authentication whenever possible.  
  
-   Central Management Servers  
  
     Central Management Servers store server registrations in the Central Management Server instead of on the file system. Central Management Servers and subordinate registered servers can be registered only by using Windows Authentication. After a Central Management Server has been registered, its associated registered servers will be automatically displayed. For more information about Central Management Servers, see [Administer Multiple Servers Using Central Management Servers](../../Topics/TopicNameNotContainA/Administer-Multiple-Servers-Using-Central-Management-Servers.md). Versions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] that are earlier than [!INCLUDE[ssKatmai](../../Topics/TopicNameContainA/tokens/ssKatmai_md.md)] cannot be designated as a Central Management Server.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To automatically register the local server instances  
  
-   In Registered Servers, right-click any node in the Registered Servers tree, and then click **Update Local Server Registration**.  
  
#### To create a new registered server  
  
1.  If Registered Servers is not visible in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], on the **View** menu, click **Registered Servers**.  
  
     **Server type**  
     When a server is registered from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers pane. To register a different type of server, click **Database Engine**, **Analysis Server**, **Reporting Services**, or **Integration Services** on the **Registered Servers** toolbar before starting to register a new server.  
  
     **Server name**  
     Select the server instance to register in the format: *<servername\>*[\\*<instancename\>*].  
  
     **Authentication**  
     Two authentication modes are available when connecting to an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
     **Windows Authentication**  
     Windows Authentication mode allows a user to connect through a [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows user account.  
  
     **SQL Server Authentication**  
     When a user connects with a specified login name and password from a nontrusted connection, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] performs the authentication itself by checking whether a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login account has been set up and whether the specified password matches the one previously recorded. If [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] does not have a login account set, authentication fails, and the user receives an error message.  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoteWinAuthentication](../../Topics/TopicNameContainA/tokens/ssNoteWinAuthentication_md.md)] For more information, see [Choose an Authentication Mode](../../Topics/TopicNameNotContainA/Choose-an-Authentication-Mode.md).  
  
     **User name**  
     Shows the current user name you are connecting with. This read-only option is only available if you have selected to connect using Windows Authentication. To change **User names**, log in to the computer as a different user.  
  
     **Login**  
     Enter the login to connect with. This option is available only if you have selected to connect using [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Authentication.  
  
     **Password**  
     Enter the password for the login. This option can be edited only if you have selected to connect by using [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Authentication.  
  
     **Remember password**  
     Select to have [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] encrypt and store the password you have entered. This option is displayed only if you have selected to connect using [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Authentication.  
  
    > [!NOTE]  
    >  If you have stored the password and want to stop storing it, clear this check box, and then click **Save**.  
  
     **Registered server name**  
     The name you want to appear in Registered Servers. This name does not have to match the **Server name** box.  
  
     **Registered server description**  
     Enter an optional description of the server.  
  
     **Test**  
     Click to test the connection to the server selected in **Server name**.  
  
     **Save**  
     Click to save the registered server settings.  
  
## Multiserver Queries  
 The Query Editor window in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] can connect to and query multiple instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] at the same time. The results that are returned by the query can be merged into a single results pane, or they can be returned in separate results panes. As an option, Query Editor can include columns that provide the name of the server that produced each row, and also the login that was used to connect to the server that provided each row. For more information about how to execute multiserver queries, see [Execute Statements Against Multiple Servers Simultaneously (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Execute-Statements-Against-Multiple-Servers-Simultaneously--SQL-Server-Management-Studio-.md).  
  
 To execute queries against all the servers in a local server group, right-click the server group, point to click **Connect**, and then click **New Query**. When queries are executed in the new Query Editor window, they will execute against all servers in the group, using the stored connection information including the user authentication context. Servers registered by using [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Authentication but not saving the password will fail to connect.  
  
 To execute queries against all the servers that are registered with a Central Management Server, expand the Central Management Server, right-click the server group, point to click **Connect**, and then click **New Query**. When queries are executed in the new Query Editor window, they will execute against all of the servers in the server group, using the stored connection information and using the Windows Authentication context of the user.  
  
## See Also  
 [How to: Hide System Objects in Object Explorer](assetId:///c01d8804-838c-4f75-b78c-80e41e4fffdc)   
 [Export Registered Server Information (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Export-Registered-Server-Information--SQL-Server-Management-Studio-.md)   
 [Import Registered Server Information (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Import-Registered-Server-Information--SQL-Server-Management-Studio-.md)