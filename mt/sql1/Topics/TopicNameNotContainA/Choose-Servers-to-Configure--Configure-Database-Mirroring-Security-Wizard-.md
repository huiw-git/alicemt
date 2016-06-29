---
title: Choose Servers to Configure (Configure Database Mirroring Security Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 59e23ff3-d7ee-4e32-9629-0b54d3a258f7
---
# Choose Servers to Configure (Configure Database Mirroring Security Wizard)
  Use this page to specify which server instances you want to configure now. You must select at least one server instance before continuing the wizard.  
  
 If you clear the check box for a server instance, the wizard will not make any changes to it. The wizard, however, will ask you to enter information about that instance and save this information as part of the configuration of the other server instances. For example, if you clear the check box for the witness server instance, the wizard will ask you to enter the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] service account of the witness because a login for that account must be created as part of the security configuration saved at the principal and mirror server instances.  
  
 **To configure database mirroring by using SQL Server Management Studio**  
  
-   [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](../../Topics/TopicNameContainA/Establish-a-Database-Mirroring-Session-Using-Windows-Authentication--SQL-Server-Management-Studio-.md)  
  
-   [Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;](../../Topics/TopicNameNotContainA/Start-the-Configuring-Database-Mirroring-Security-Wizard--SQL-Server-Management-Studio-.md)  
  
## Options  
 **Principal server instance**  
 Select to configure security for the principal server.  
  
 **Mirror server instance**  
 Select to configure security for the mirror server.  
  
 **Witness server instance**  
 Select to configure security for the witness server (if present).  
  
## See Also  
 [Database Properties &#40;Mirroring Page&#41;](../../Topics/TopicNameNotContainA/Database-Properties--Mirroring-Page-.md)   
 [Database Mirroring &#40;SQL Server&#41;](../../Topics/TopicNameNotContainA/Database-Mirroring--SQL-Server-.md)  
  
  