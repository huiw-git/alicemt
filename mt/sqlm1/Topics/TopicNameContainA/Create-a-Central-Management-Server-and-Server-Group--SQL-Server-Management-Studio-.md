---
title: Create a Central Management Server and Server Group (SQL Server Management Studio)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: da265482-3953-440a-ac23-0ab7e42a55eb
---
# Create a Central Management Server and Server Group (SQL Server Management Studio)
  This topic describes how to designate an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] as a central management server in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. Central management servers store a list of instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that is organized into one or more central management server groups. Actions that are taken by using a central management server group act on all servers in the server group. This includes connecting to servers by using Object Explorer and executing [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements and Policy\-Based Management policies on multiple servers at the same time.  
  
> [!NOTE]  
>  Versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that are earlier than [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] cannot be designated as a central management server.  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To create a Central Management Server and Server Group, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Two database roles in the msdb database grant access to central management servers. Only members of the ServerGroupAdministratorRole role can manage the central management server. Membership in the ServerGroupReaderRole role is required to connect to a central management server.  
  
 Because the connections that are maintained by a central management server execute in the context of the user, by using Windows Authentication, the effective permissions on the registered servers might vary. For example, the user might be a member of the sysadmin fixed server role on the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] A, but have limited permissions on the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] B.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 The following procedures describe how to perform the following steps.  
  
1.  Create a central management server.  
  
2.  Add one or more server groups to the central management server and add one or more registered servers to the server groups.  
  
#### Create a central management server  
  
1.  In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], on the **View** menu, click **Registered Servers**.  
  
2.  In Registered Servers, expand **Database Engine**, right\-click **Central Management Servers**, and then  click **Register Central Management Server**.  
  
3.  In the **New Server Registration** dialog box, select the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that you want to become the central management server from the drop\-down list of servers. You must use Windows Authentication for the central management server.  
  
4.  In **Registered Server**, enter a server name and optional description.  
  
5.  From the **Connection Properties** tab, review or modifiy the network  and connection properties. For more information, see [Connect to Server &#40;Connection Properties Page&#41; Database Engine](../Topic/Connect%20to%20Server%20\(Connection%20Properties%20Page\)%20Database%20Engine.md)  
  
6.  Click **Test**, to test the connection.  
  
7.  Click **Save**. The instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] will appear under the **Central Management Servers** folder.  
  
#### Create a new server group and add servers to the group  
  
1.  From **Registered Servers**, expand **Central Management Servers**. Right\-click the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] added in the procedure above and select **New Server Group**.  
  
2.  In **New Server Group Properties**, enter a group name and optional description.  
  
3.  From **Registered Servers**, right\-click the server group and click **New Server Registration**.  
  
4.  From New Server Registration, select an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. For more information, see [Create a New Registered Server &#40;SQL Server Management Studio&#41;](../Topic/Create%20a%20New%20Registered%20Server%20\(SQL%20Server%20Management%20Studio\).md). Add more servers as appropriate.  
  
#### To execute queries against several configuration targets at the same time  
  
-   After you create a central management server, one or more server groups, and one or more registered servers, you can execute queries against a whole group at the same time. For more information about how to execute [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements on the servers in a server group at the same time, see [Execute Statements Against Multiple Servers Simultaneously &#40;SQL Server Management Studio&#41;](../Topic/Execute%20Statements%20Against%20Multiple%20Servers%20Simultaneously%20\(SQL%20Server%20Management%20Studio\).md).  
  
## See Also  
 [Administer Multiple Servers Using Central Management Servers](../../Topics\TopicNameNotContainA/Administer-Multiple-Servers-Using-Central-Management-Servers.md)  
  
  