---
title: "Witness Server Instance (Configure Database Mirroring Security Wizard)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b5763663-984a-473b-93a3-6cd3322ad41c
caps.latest.revision: 42
caps.handback.revision: 0
manager: jhubbard
---
# Witness Server Instance (Configure Database Mirroring Security Wizard)
Use this page to specify information about the server instance that is to serve as the witness for the session.  
  
> [!NOTE]  
>  A witness server instance is not available in every edition of [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], see [Features Supported by the Editions of SQL Server 2016](../../Topics/TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md).  
  
 **To configure database mirroring by using SQL Server Management Studio**  
  
-   [Establish a Database Mirroring Session Using Windows Authentication (SQL Server Management Studio)](../../Topics/TopicNameContainA/Establish-a-Database-Mirroring-Session-Using-Windows-Authentication--SQL-Server-Management-Studio-.md)  
  
-   [Start the Configuring Database Mirroring Security Wizard (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Start-the-Configuring-Database-Mirroring-Security-Wizard--SQL-Server-Management-Studio-.md)  
  
## Options  
 **Witness server instance**  
 If a witness server instance is already specified (on the **Mirroring** page of the **Database Properties** dialog box), that instance is displayed (for more information, see [Database Properties (Mirroring Page)](../../Topics/TopicNameNotContainA/Database-Properties--Mirroring-Page-.md)).  
  
 Otherwise, this list box displays the name of the current server. Be aware that the witness server instance cannot be the same as the principal or mirror server instances.  
  
 **Connect**  
 If a witness server instance has not been specified, click **Connect**. This displays the **Connect to Server** dialog box in which you can specify the server instance and establish a connection.  
  
 If the instance has been specified, but the wizard lacks a connection with sufficient permission to check for the existence of the endpoint, click **Connect**. This displays the **Connect to Server** dialog box with the server instance pre-selected and unchangeable. Specify a domain account with sufficient permission, and connect to the server instance.  
  
> [!NOTE]  
>  When connecting to the server instance, the Configure Database Mirroring Security Wizard uses the credentials provided in the **Connect to Server** dialog box. These are different from the credentials of a mirroring session, which uses the credentials of the startup account where the server instance is running as a service.  
  
 **Listener Port**  
 The behavior of this option depends on whether the mirroring endpoint exists for this server instance, as follows:  
  
-   If the listener port does not exist for the server instance, port number 5022 is displayed in the **Port** text box. You can enter any available port number, such as, 7022.  
  
-   When the mirroring endpoint already exists, the port number from the endpoint is displayed. If you need to change that port, use an ALTER ENDPOINT statement. For more information, see [ALTER ENDPOINT (Transact-SQL)](assetId:///70f35566-30cf-47c6-8394-dfe5d71629d3).  
  
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
 [Database Mirroring Witness](../../Topics/TopicNameNotContainA/Database-Mirroring-Witness.md)