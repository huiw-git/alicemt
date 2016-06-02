---
title: Service Broker with Always On Availability Groups (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 881c20e5-1c99-44eb-b393-09fc5ea0f122
---
# Service Broker with Always On Availability Groups (SQL Server)
  This topic contains information about configuring Service Broker to work with [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
 **In This Topic:**  
  
-   [Requirements for a Service in an Availability Group to Receive Remote Messages](#ReceiveRemoteMessages)  
  
-   [Requirements for Sending Messages to a Remote Service in an Availability Group](#SendRemoteMessages)  
  
##  <a name="ReceiveRemoteMessages"></a> Requirements for a Service in an Availability Group to Receive Remote Messages  
  
1.  **Ensure that the availability group possesses a listener.**  
  
     For more information, see [Create or Configure an Availability Group Listener &#40;SQL Server&#41;](../Topic/Create%20or%20Configure%20an%20Availability%20Group%20Listener%20\(SQL%20Server\).md).  
  
2.  **Ensure that the Service Broker endpoint exists and is correctly configured.**  
  
     On every instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that hosts an availability replica for the availability group, configure the Service Broker endpoint, as follows:  
  
    -   Set LISTENER\_IP to 'ALL'. This setting enables connections on any valid IP address that is bound to the availability group listener.  
  
    -   Set the Service Broker PORT to the same port number on all the host server instances.  
  
        > [!TIP]  
        >  To view the port number of the Service Broker endpoint on a given server instance, query the **port** column of the [sys.tcp\_endpoints](../Topic/sys.tcp_endpoints%20\(Transact-SQL\).md) catalog view, where **type\_desc** \= 'SERVICE\_BROKER'.  
  
     The following example creates a Windows authenticated Service Broker endpoint that uses the default Service Broker port \(4022\) and listens to all valid IP addresses.  
  
    ```  
    CREATE ENDPOINT [SSBEndpoint]  
        STATE = STARTED  
        AS TCP  (LISTENER_PORT = 4022, LISTENER_IP = ALL )  
        FOR SERVICE_BROKER (AUTHENTICATION = WINDOWS)  
    ```  
  
     For more information, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](../Topic/CREATE%20ENDPOINT%20\(Transact-SQL\).md).  
  
3.  **Grant CONNECT permission on the endpoint.**  
  
     Grant CONNECT permission on the Service Broker endpoint either to PUBLIC or to a login.  
  
     The following example grants the connection on a Service Broker endpoint named `broker_endpoint` to PUBLIC.  
  
    ```  
    GRANT CONNECT ON ENDPOINT::[broker_endpoint] TO [PUBLIC]  
    ```  
  
     For more information, see [GRANT &#40;Transact-SQL&#41;](../Topic/GRANT%20\(Transact-SQL\).md).  
  
4.  **Ensure that msdb contains either an AutoCreatedLocal route or a route to the specific service.**  
  
    > [!NOTE]  
    >  By default, each user database, including **msdb**, contains the route **AutoCreatedLocal**. This route matches any service name and broker instance and specifies that the message should be delivered within the current instance. **AutoCreatedLocal** has lower priority than routes that explicitly specify a specific service that communicates with a remote instance.  
  
     For information about creating routes, see [Service Broker Routing Examples](http://msdn.microsoft.com/library/ms166090\(SQL.105\).aspx) \(in the [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] version of Books Online\) and [CREATE ROUTE &#40;Transact-SQL&#41;](../Topic/CREATE%20ROUTE%20\(Transact-SQL\).md).  
  
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
  
     For more information, see [CREATE ROUTE &#40;Transact-SQL&#41;](../Topic/CREATE%20ROUTE%20\(Transact-SQL\).md).  
  
2.  **Ensure that msdb contains either an AutoCreatedLocal route or a route to the specific service.** \(For more information, see [Requirements for a Service in an Availability Group to Receive Remote Messages](#ReceiveRemoteMessages), earlier in this topic.\)  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [CREATE ENDPOINT &#40;Transact-SQL&#41;](../Topic/CREATE%20ENDPOINT%20\(Transact-SQL\).md)  
  
-   [CREATE ROUTE &#40;Transact-SQL&#41;](../Topic/CREATE%20ROUTE%20\(Transact-SQL\).md)  
  
-   [GRANT &#40;Transact-SQL&#41;](../Topic/GRANT%20\(Transact-SQL\).md)  
  
-   [Create or Configure an Availability Group Listener &#40;SQL Server&#41;](../Topic/Create%20or%20Configure%20an%20Availability%20Group%20Listener%20\(SQL%20Server\).md).  
  
-   [Creation and Configuration of Availability Groups &#40;SQL Server&#41;](../Topic/Creation%20and%20Configuration%20of%20Availability%20Groups%20\(SQL%20Server\).md)  
  
-   [Set Up Login Accounts for Database Mirroring or Always On Availability Groups &#40;SQL Server&#41;](../Topic/Set%20Up%20Login%20Accounts%20for%20Database%20Mirroring%20or%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../Topic/Availability%20Group%20Listeners,%20Client%20Connectivity,%20and%20Application%20Failover%20\(SQL%20Server\).md)   
 [SQL Server Service Broker](../../Topics\TopicNameNotContainA/SQL-Server-Service-Broker.md)  
  
  