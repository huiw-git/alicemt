---
title: "Include Witness Server (Configure Database Mirroring Security Wizard)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f04b38a4-f4e2-4d4c-bdac-7cc70e5a5684
caps.latest.revision: 33
caps.handback.revision: 0
manager: jhubbard
---
# Include Witness Server (Configure Database Mirroring Security Wizard)
Use this page to specify whether you want to include a witness server in this security configuration for database mirroring.  
  
 **To configure database mirroring by using SQL Server Management Studio**  
  
-   [Establish a Database Mirroring Session Using Windows Authentication (SQL Server Management Studio)](../../Topics/TopicNameContainA/Establish-a-Database-Mirroring-Session-Using-Windows-Authentication--SQL-Server-Management-Studio-.md)  
  
-   [Start the Configuring Database Mirroring Security Wizard (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Start-the-Configuring-Database-Mirroring-Security-Wizard--SQL-Server-Management-Studio-.md)  
  
## Options  
 **Yes**  
 Click to include a witness server instance in the security configuration. The witness is necessary for high-safety mode with automatic failover, which supports automatic failover to the mirror server instance if the principal server instance fails.  
  
 **No**  
 Click to configure security without a witness.  
  
## See Also  
 [Database Properties (Mirroring Page)](../../Topics/TopicNameNotContainA/Database-Properties--Mirroring-Page-.md)   
 [Database Mirroring (SQL Server)](../../Topics/TopicNameNotContainA/Database-Mirroring--SQL-Server-.md)   
 [Database Mirroring Witness](../../Topics/TopicNameNotContainA/Database-Mirroring-Witness.md)