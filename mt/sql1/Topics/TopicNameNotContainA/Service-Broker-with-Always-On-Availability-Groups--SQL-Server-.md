---
title: "Service Broker with Always On Availability Groups (SQL Server)"
ms.custom: na
ms.date: 2016-05-17
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 881c20e5-1c99-44eb-b393-09fc5ea0f122
caps.latest.revision: 14
caps.handback.revision: 0
manager: jhubbard
---
# Service Broker with Always On Availability Groups (SQL Server)
This topic contains information about configuring Service Broker to work with [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/tokens/ssHADR_md.md)] in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)].  
  
 **In This Topic:**  
  
-   [Requirements for a Service in an Availability Group to Receive Remote Messages](#ReceiveRemoteMessages)  
  
-   [Requirements for Sending Messages to a Remote Service in an Availability Group](#SendRemoteMessages)  
  
##  <a name="ReceiveRemoteMessages"></a> Requirements for a Service in an Availability Group to Receive Remote Messages  
  
1.  **Ensure that the availability group possesses a listener.**  
  
     For more information, see [Create or Configure an Availability Group Listener (SQL Server)](../../Topics/TopicNameNotContainA/Create-or-Configure-an-Availability-Group-Listener--SQL-Server-.md).  
  
2.  **Ensure that the Service Broker endpoint exists and is correctly configured.**  
  
     On every instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] that hosts an availability replica for the availability group, configure the Service Broker endpoint, as follows:  
  
    -   Set LISTENER_IP to 'ALL'. This setting enables connections on any valid IP address that is bound to the availability group listener.  
  
    -   Set the Service Broker PORT to the same port number on all the host server instances.  
  
        > [!TIP]  
        >  To view the port number of the Service Broker endpoint on a given server instance, query the **port** column of the [sys.tcp_endpoints](assetId:///43cc3afa-cced-4463-8e97-fbfdaf2e4fa8) catalog view, where **type_desc** = 'SERVICE_BROKER'.  
  
     The following example creates a Windows authenticated Service Broker endpoint that uses the default Service Broker port (4022) and listens to all valid IP addresses.  
  
    ```  
    CREATE ENDPOINT [SSBEndpoint]  
        STATE = STARTED  
        AS TCP  (LISTENER_PORT = 4022, LISTENER_IP = ALL )  
        FOR SERVICE_BROKER (AUTHENTICATION = WINDOWS)  
    ```  
  
     For more information, see [CREATE ENDPOINT (Transact-SQL)](assetId:///6405e7ec-0b5b-4afd-9792-1bfa5a2491f6).  
  
3.  **Grant CONNECT permission on the endpoint.**  
  
     Grant CONNECT permission on the Service Broker endpoint either to PUBLIC or to a login.  
  
     The following example grants the connection on a Service Broker endpoint named `broker_endpoint` to PUBLIC.  
  
    ```  
    GRANT CONNECT ON ENDPOINT::[broker_endpoint] TO [PUBLIC]  
    ```  
  
     For more information, see [GRANT (Transact-SQL)](assetId:///a760c16a-4d2d-43f2-be81-ae9315f38185).  
  
4.  **Ensure that msdb contains either an AutoCreatedLocal route or a route to the specific service.**  
  
    > [!NOTE]  
    >  By default, each user database, including **msdb**, contains the route **AutoCreatedLocal**. This route matches any service name and broker instance and specifies that the message should be delivered within the current instance. **AutoCreatedLocal** has lower priority than routes that explicitly specify a specific service that communicates with a remote instance.  
  
     For information about creating routes, see [Service Broker Routing Examples](http://msdn.microsoft.com/library/ms166090\(SQL.105\).aspx) (in the [!INCLUDE[ssKilimanjaro](../../Topics/TopicNameContainA/tokens/ssKilimanjaro_md.md)] version of Books Online) and [CREATE ROUTE (Transact-SQL)](assetId:///7e695364-1a98-4cfd-8ebd-137ac5a425b3).  
  
##  <a name="SendRemoteMessages"></a> Requirements for Sending Messages to a Remote Service in an Availability Group  
  
1.  **Create a route to the target service.**  
  
     Configure the route as follows:  
  
    -   Set ADDRESS to the listener IP address of availability group that hosts the service database.  
  
    -   Set PORT to the port that you specified in the Service Broker endpoint of each of the remote SQL Server instances.  
  
     The following example creates a route named `RouteToTargetService` for the `ISBNLookupRequestService` service. The route targets the availability group listener, `MyAgListener`, which uses port 4022.  
  
    ```  
    CREATE ROUTE [RouteToTargetService] WITH   
    SERVICE_NAME = 'ISBNLookupRequestService',   
    ADDRESS = 'TCP://MyAgListener:4022';  
  
    ```  
  
     For more information, see [CREATE ROUTE (Transact-SQL)](assetId:///7e695364-1a98-4cfd-8ebd-137ac5a425b3).  
  
2.  **Ensure that msdb contains either an AutoCreatedLocal route or a route to the specific service.** (For more information, see [Requirements for a Service in an Availability Group to Receive Remote Messages](#ReceiveRemoteMessages), earlier in this topic.)  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [CREATE ENDPOINT (Transact-SQL)](assetId:///6405e7ec-0b5b-4afd-9792-1bfa5a2491f6)  
  
-   [CREATE ROUTE (Transact-SQL)](assetId:///7e695364-1a98-4cfd-8ebd-137ac5a425b3)  
  
-   [GRANT (Transact-SQL)](assetId:///a760c16a-4d2d-43f2-be81-ae9315f38185)  
  
-   [Create or Configure an Availability Group Listener (SQL Server)](../../Topics/TopicNameNotContainA/Create-or-Configure-an-Availability-Group-Listener--SQL-Server-.md).  
  
-   [Creation and Configuration of Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Creation-and-Configuration-of-Availability-Groups--SQL-Server-.md)  
  
-   [Set Up Login Accounts for Database Mirroring or Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Set-Up-Login-Accounts-for-Database-Mirroring-or-Always-On-Availability-Groups--SQL-Server-.md)  
  
## See Also  
 [Overview of Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Overview-of-Always-On-Availability-Groups--SQL-Server-.md)   
 [Availability Group Listeners, Client Connectivity, and Application Failover (SQL Server)](../../Topics/TopicNameNotContainA/Availability-Group-Listeners--Client-Connectivity--and-Application-Failover--SQL-Server-.md)   
 [SQL Server Service Broker](../../Topics/TopicNameNotContainA/SQL-Server-Service-Broker.md)