---
title: Mirror Server Instance (Configure Database Mirroring Security Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 53223432-615e-440f-904d-925d33ec2144
---
# Mirror Server Instance (Configure Database Mirroring Security Wizard)
  Use this page to specify information about the server instance with the mirror database.  
  
> [!IMPORTANT]  
>  The mirror server instance must be running the same edition of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], either Standard or Enterprise, as the principal server instance. Also, we strongly recommend that they run on comparable systems that can handle identical workloads.  
  
 **To configure database mirroring by using SQL Server Management Studio**  
  
-   [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](../Topic/Establish%20a%20Database%20Mirroring%20Session%20Using%20Windows%20Authentication%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;](../Topic/Start%20the%20Configuring%20Database%20Mirroring%20Security%20Wizard%20\(SQL%20Server%20Management%20Studio\).md)  
  
## Options  
 **Mirror server instance**  
 If a mirror server instance is already specified \(on the **Mirroring** page of the **Database Properties** dialog box\), that instance is displayed; for more information, see [Database Properties &#40;Mirroring Page&#41;](../Topic/Database%20Properties%20\(Mirroring%20Page\).md).  
  
 Otherwise, enter the name of the mirror server instance. Note that the mirror server instance cannot be the same as the principal server instance.  
  
 **Connect**  
 If a mirror server instance has not been specified, click **Connect**. This displays the **Connect to Server** dialog box in which you can specify the server instance and establish a connection.  
  
 If the instance has been specified, but the wizard lacks a connection with sufficient permission to check for the existence of the endpoint, click **Connect**. This displays the **Connect to Server** dialog box with the server instance pre\-selected and unchangeable. Specify a domain account with sufficient permission, and connect to the server instance.  
  
> [!NOTE]  
>  When connecting to the server instance, the Configure Database Mirroring Security Wizard uses the credentials provided in the **Connect to Server** dialog box. These are different from the credentials of a mirroring session, which uses the credentials of the startup account where the server instance is running as a service.  
  
 **Listener Port**  
 The behavior of this option depends on whether the mirroring endpoint exists for this server instance, as follows:  
  
-   If a listener port does not exist for the server instance, port number 5022 is displayed in the **Port** text box. You can use any available port number, such as 7022.  
  
-   When the mirroring endpoint already exists, the port number from that endpoint is displayed. If you need to change the port, use an ALTER ENDPOINT command. For more information, see [ALTER ENDPOINT &#40;Transact-SQL&#41;](../Topic/ALTER%20ENDPOINT%20\(Transact-SQL\).md).  
  
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
  
  