---
title: Witness Server Instance (Configure Database Mirroring Security Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b5763663-984a-473b-93a3-6cd3322ad41c
---
# Witness Server Instance (Configure Database Mirroring Security Wizard)
  Use this page to specify information about the server instance that is to serve as the witness for the session.  
  
> [!NOTE]  
>  A witness server instance is not available in every edition of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md).  
  
 **To configure database mirroring by using SQL Server Management Studio**  
  
-   [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](../Topic/Establish%20a%20Database%20Mirroring%20Session%20Using%20Windows%20Authentication%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;](../Topic/Start%20the%20Configuring%20Database%20Mirroring%20Security%20Wizard%20\(SQL%20Server%20Management%20Studio\).md)  
  
## Options  
 **Witness server instance**  
 If a witness server instance is already specified \(on the **Mirroring** page of the **Database Properties** dialog box\), that instance is displayed \(for more information, see [Database Properties &#40;Mirroring Page&#41;](../Topic/Database%20Properties%20\(Mirroring%20Page\).md)\).  
  
 Otherwise, this list box displays the name of the current server. Be aware that the witness server instance cannot be the same as the principal or mirror server instances.  
  
 **Connect**  
 If a witness server instance has not been specified, click **Connect**. This displays the **Connect to Server** dialog box in which you can specify the server instance and establish a connection.  
  
 If the instance has been specified, but the wizard lacks a connection with sufficient permission to check for the existence of the endpoint, click **Connect**. This displays the **Connect to Server** dialog box with the server instance pre\-selected and unchangeable. Specify a domain account with sufficient permission, and connect to the server instance.  
  
> [!NOTE]  
>  When connecting to the server instance, the Configure Database Mirroring Security Wizard uses the credentials provided in the **Connect to Server** dialog box. These are different from the credentials of a mirroring session, which uses the credentials of the startup account where the server instance is running as a service.  
  
 **Listener Port**  
 The behavior of this option depends on whether the mirroring endpoint exists for this server instance, as follows:  
  
-   If the listener port does not exist for the server instance, port number 5022 is displayed in the **Port** text box. You can enter any available port number, such as, 7022.  
  
-   When the mirroring endpoint already exists, the port number from the endpoint is displayed. If you need to change that port, use an ALTER ENDPOINT statement. For more information, see [ALTER ENDPOINT &#40;Transact-SQL&#41;](../Topic/ALTER%20ENDPOINT%20\(Transact-SQL\).md).  
  
    > [!NOTE]  
    >  A port number is required.  
  
 **Endpoint name**  
 If the mirroring endpoint exists for this server instance, the endpoint name is displayed here. If the endpoint does not exist, you can specify the name of the endpoint.  
  
 **Encrypt data sent through this endpoint**  
 By default, encryption is enabled. When enabled, encryption is required \(not merely supported\) and uses the default values for all of the encryption options. For more information, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](../Topic/CREATE%20ENDPOINT%20\(Transact-SQL\).md).  
  
 To disable encryption, clear the check box. To re\-enable encryption, select the check box.  
  
## See Also  
 [The Database Mirroring Endpoint &#40;SQL Server&#41;](../Topic/The%20Database%20Mirroring%20Endpoint%20\(SQL%20Server\).md)   
 [Database Properties &#40;Mirroring Page&#41;](../Topic/Database%20Properties%20\(Mirroring%20Page\).md)   
 [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](../Topic/Create%20a%20Database%20Mirroring%20Endpoint%20for%20Windows%20Authentication%20\(Transact-SQL\).md)   
 [Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../Topic/Start%20Database%20Mirroring%20Monitor%20\(SQL%20Server%20Management%20Studio\).md)   
 [Database Mirroring &#40;SQL Server&#41;](../Topic/Database%20Mirroring%20\(SQL%20Server\).md)   
 [Database Mirroring Witness](../../Topics\TopicNameNotContainA/Database-Mirroring-Witness.md)  
  
  