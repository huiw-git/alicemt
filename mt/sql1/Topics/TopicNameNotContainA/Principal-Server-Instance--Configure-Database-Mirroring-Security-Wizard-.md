---
title: "Principal Server Instance (Configure Database Mirroring Security Wizard)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 58af27d7-c5dd-4669-be6b-b472bc2c8ef4
caps.latest.revision: 37
caps.handback.revision: 0
manager: jhubbard
---
# Principal Server Instance (Configure Database Mirroring Security Wizard)
Use this page to specify information about the server instance of the principal database. The principal database is the copy of the database that begins the mirroring session. After the session has begun, the principal database is the copy of the database that accepts user changes. (When a failover occurs, the principal and mirroring roles are swapped; therefore, the initial principal database might not remain the principal database.)  
  
 **To configure database mirroring by using SQL Server Management Studio**  
  
-   [Establish a Database Mirroring Session Using Windows Authentication (SQL Server Management Studio)](../../Topics/TopicNameContainA/Establish-a-Database-Mirroring-Session-Using-Windows-Authentication--SQL-Server-Management-Studio-.md)  
  
-   [Start the Configuring Database Mirroring Security Wizard (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Start-the-Configuring-Database-Mirroring-Security-Wizard--SQL-Server-Management-Studio-.md)  
  
## Options  
 **Principal server instance**  
 Because database mirroring in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] is always configured from the principal server, the current server instance is always the principal server instance.  
  
 **Listener Port**  
 The behavior of this option depends on whether the mirroring endpoint exists for this server instance, as follows:  
  
-   If the listener port does not exist for this server instance, port number 5022 is displayed in the **Port** text box. You can use any available port number, such as, 7022.  
  
-   When the mirroring endpoint already exists, the port number from the endpoint is displayed. If you need to change the port, use an ALTER ENDPOINT command. For more information, see [ALTER ENDPOINT (Transact-SQL)](assetId:///70f35566-30cf-47c6-8394-dfe5d71629d3).  
  
> [!NOTE]  
>  A port number is required.  
  
 **Endpoint name**  
 If the mirroring endpoint exists for this server instance, the endpoint name is displayed here. If the endpoint does not exist, you can specify the name of the endpoint.  
  
 **Encrypt data sent through this endpoint**  
 By default, encryption is enabled. When enabled, encryption is required (not merely supported) and uses the default values for all of the encryption options. For more information, see [CREATE ENDPOINT (Transact-SQL)](assetId:///6405e7ec-0b5b-4afd-9792-1bfa5a2491f6).  
  
 To disable encryption, clear the check box. To re-enable encryption, select the check box.  
  
## See Also  
 [The Database Mirroring Endpoint (SQL Server)](../../Topics/TopicNameNotContainA/The-Database-Mirroring-Endpoint--SQL-Server-.md)   
 [Database Properties (Mirroring Page)](../../Topics/TopicNameNotContainA/Database-Properties--Mirroring-Page-.md)   
 [Create a Database Mirroring Endpoint for Windows Authentication (Transact-SQL)](../../Topics/TopicNameContainA/Create-a-Database-Mirroring-Endpoint-for-Windows-Authentication--Transact-SQL-.md)   
 [Start Database Mirroring Monitor (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Start-Database-Mirroring-Monitor--SQL-Server-Management-Studio-.md)   
 [Database Mirroring (SQL Server)](../../Topics/TopicNameNotContainA/Database-Mirroring--SQL-Server-.md)