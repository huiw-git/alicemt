---
title: Configure the Database Engine to Listen on Multiple TCP Ports
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8e955033-06ef-403f-b813-3d8241b62f1f
---
# Configure the Database Engine to Listen on Multiple TCP Ports
  This topic describes how to configure the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] to listen on multiple TCP ports in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using SQL Server Configuration Manager. When TCP\/IP is enabled for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] will listen for incoming connections on a connection point consisting of an IP address and TCP port number.The following procedures create a tabular data stream \(TDS\) endpoint, so that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] will listen on an additional TCP port.  
  
 Possible reasons to create a second TDS endpoint include:  
  
-   Increase security by configuring the firewall to restrict access to the default endpoint to local client computers on a specific subnet. Maintain Internet access to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] for your support team by creating a new endpoint that the firewall exposes to the Internet, and restricting connection rights to this endpoint to your server support team.  
  
-   Affinitizing connections to specific processors when using Non\-Uniform Memory Access \(NUMA\).  
  
 Configuring a TDS endpoint consists of the following steps, which can be done in any order:  
  
-   Create the TDS endpoint for the TCP port, and restore access to the default endpoint if appropriate.  
  
-   Grant access to the endpoint to the desired server principals.  
  
-   Specify the TCP port number for the selected IP address.  
  
 For more information about the default Windows firewall settings, and a description of the TCP ports that affect the Database Engine, Analysis Services, Reporting Services, and Integration Services, see [Configure the Windows Firewall to Allow SQL Server Access](../../Topics\TopicNameNotContainA/Configure-the-Windows-Firewall-to-Allow-SQL-Server-Access.md).  
  
##  <a name="SSMSProcedure"></a>  
  
#### To create a TDS endpoint  
  
-   Issue the following statement to create an endpoint named **CustomConnection** for port 1500 for all available TCP addresses on the server.  
  
    ```  
    USE master;  
    GO  
    CREATE ENDPOINT [CustomConnection]  
    STATE = STARTED  
    AS TCP  
       (LISTENER_PORT = 1500, LISTENER_IP =ALL)  
    FOR TSQL() ;  
    GO  
    ```  
  
 When you create a new [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] endpoint, connect permissions for **public** are revoked for the default TDS endpoint. If access to the **public** group is needed for the default endpoint, reapply this permission by using the `GRANT CONNECT ON ENDPOINT::[TSQL Default TCP] to [public];` statement.  
  
#### To grant access to the endpoint  
  
-   Issue the following statement to grant access to the **CustomConnection** endpoint to the SQLSupport group in the corp domain.  
  
    ```  
    GRANT CONNECT ON ENDPOINT::[CustomConnection] to [corp\SQLSupport] ;  
    GO  
    ```  
  
#### To configure the SQL Server Database Engine to listen on an additional TCP port  
  
1.  In SQL Server Configuration Manager, expand **SQL Server Network Configuration**, and then click **Protocols for***\<instance\_name\>*.  
  
2.  Expand **Protocols for***\<instance\_name\>*, and then click **TCP\/IP**.  
  
3.  In the right pane, right\-click each disabled IP address that you want to enable, and then click **Enable**.  
  
4.  Right\-click **IPAll**, and then click **Properties**.  
  
5.  In the **TCP Port** box, type the ports that you want the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] to listen on, separated by commas. In our example, if the default port 1433 is listed, type **,1500** so the box reads **1433,1500**, and then click **OK**.  
  
    > [!NOTE]  
    >  If you are not enabling the port on all IP addresses, configure the additional port in the property box for only for the desired address. Then, in the console pane, right\-click **TCP\/IP**, click **Properties**, and in the **Listen All** box, select **No**.  
  
6.  In the left pane, click **SQL Server Services**.  
  
7.  In the right pane, right\-click **SQL Server***\<instance\_name\>*, and then click **Restart**.  
  
     When the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] restarts, the Error log will list the ports on which [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is listening.  
  
#### To connect to the new endpoint  
  
-   Issue the following statement to connect to the **CustomConnection** endpoint of the default instance of SQL Server on the server named ACCT, using a trusted connection, and assuming the user is a member of the \[corp\\SQLSupport\] group.  
  
    ```  
    sqlcmd -SACCT,1500  
    ```  
  
## See Also  
 [CREATE ENDPOINT &#40;Transact-SQL&#41;](../Topic/CREATE%20ENDPOINT%20\(Transact-SQL\).md)   
 [DROP ENDPOINT &#40;Transact-SQL&#41;](../Topic/DROP%20ENDPOINT%20\(Transact-SQL\).md)   
 [GRANT Endpoint Permissions &#40;Transact-SQL&#41;](../Topic/GRANT%20Endpoint%20Permissions%20\(Transact-SQL\).md)   
 [Map TCP IP Ports to NUMA Nodes &#40;SQL Server&#41;](../Topic/Map%20TCP%20IP%20Ports%20to%20NUMA%20Nodes%20\(SQL%20Server\).md)  
  
  