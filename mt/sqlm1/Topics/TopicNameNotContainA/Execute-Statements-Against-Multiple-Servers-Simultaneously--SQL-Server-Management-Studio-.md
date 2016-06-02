---
title: Execute Statements Against Multiple Servers Simultaneously (SQL Server Management Studio)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 197760f3-0a06-43de-8162-69c27d3fbe56
---
# Execute Statements Against Multiple Servers Simultaneously (SQL Server Management Studio)
  This topic describes how to query multiple servers at the same time in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], by creating a local server group, or a Central Management Server and one or more server groups, and one or more registered servers within the groups, and then querying the complete group. The results that are returned by the query can be combined into a single results pane, or can be returned in separate results panes. The results set can include additional columns for the server name and the login that is used by the query on each server. Central Management Servers and subordinate servers can be registered by using only Windows Authentication. Servers in local server groups can be registered by using Windows Authentication or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication.  
  
> [!NOTE]  
>  Before you execute the following procedures, create a Central Management Server and server groups. For more information, see [Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;](../Topic/Create%20a%20Central%20Management%20Server%20and%20Server%20Group%20\(SQL%20Server%20Management%20Studio\).md).  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Security](#Security)  
  
-   **To execute statements against multiple servers, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 Because the connections maintained by a Central Management Server execute in the context of the user, by using Windows Authentication, the effective permissions on the registered servers might vary. For example, the user might be a member of the sysadmin fixed server role on the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] A, but have limited permissions on the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] B.  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### To execute statements against multiple configuration targets simultaneously  
  
1.  In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], on the **View** menu, click **Registered Servers**.  
  
2.  Expand a Central Management Server, right\-click a server group, point to **Connect**, and then click **New Query**.  
  
3.  In Query Editor, type and execute a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement, such as the following:  
  
    ```  
    USE master  
    GO  
    SELECT * FROM sysdatabases;  
    GO  
    ```  
  
     By default, the results pane will combine the query results from all the servers in the server group.  
  
#### To change the multiserver results options  
  
1.  In [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)], on the **Tools** menu, click **Options**.  
  
2.  Expand **Query Results**, expand **SQL Server**, and then click **Multiserver Results**.  
  
3.  On the **Multiserver Results** page, specify the option settings that you want, and then click **OK**.  
  
## See Also  
 [Administer Multiple Servers Using Central Management Servers](../../Topics\TopicNameNotContainA/Administer-Multiple-Servers-Using-Central-Management-Servers.md)  
  
  