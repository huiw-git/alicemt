---
title: "Service Accounts (Configure Database Mirroring Security Wizard)"
ms.custom: na
ms.date: 2016-05-17
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d58d8f93-7888-4d66-af4d-969ef6a2dbee
caps.latest.revision: 37
caps.handback.revision: 0
manager: jhubbard
---
# Service Accounts (Configure Database Mirroring Security Wizard)
When using Windows Authentication, if the server instances use different accounts, specify the service accounts for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. These service accounts must all be domain accounts (in the same or trusted domains).  
  
 If all the server instances use the same domain account or use certificate-based authentication, leave the fields blank. Simply click **Finish**, and the wizard automatically configures the accounts based on the account of the current wizard.  
  
> [!IMPORTANT]  
>  If the database mirroring endpoints of the server instances are configured to use certificates, you must leave the service account fields empty.  
  
 **To configure database mirroring by using SQL Server Management Studio**  
  
-   [Establish a Database Mirroring Session Using Windows Authentication (SQL Server Management Studio)](../../Topics/TopicNameContainA/Establish-a-Database-Mirroring-Session-Using-Windows-Authentication--SQL-Server-Management-Studio-.md)  
  
-   [Start the Configuring Database Mirroring Security Wizard (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Start-the-Configuring-Database-Mirroring-Security-Wizard--SQL-Server-Management-Studio-.md)  
  
## Options  
 **Principal**  
 Specify the service account of the principal server instance. Enter the domain name in upper case:  
  
 *DOMAINNAME*\\*username*  
  
 **Mirror**  
 Specify the service account of the mirror server instance. Enter the domain name in upper case:  
  
 *DOMAINNAME*\\*username*  
  
 **Witness**  
 Specify the service account of the witness server instance. Enter the domain name in upper case:  
  
 *DOMAINNAME*\\*username*  
  
## See Also  
 [Database Properties (Mirroring Page)](../../Topics/TopicNameNotContainA/Database-Properties--Mirroring-Page-.md)   
 [Start Database Mirroring Monitor (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Start-Database-Mirroring-Monitor--SQL-Server-Management-Studio-.md)   
 [Database Mirroring (SQL Server)](../../Topics/TopicNameNotContainA/Database-Mirroring--SQL-Server-.md)   
 [Set Up Login Accounts for Database Mirroring or Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Set-Up-Login-Accounts-for-Database-Mirroring-or-Always-On-Availability-Groups--SQL-Server-.md)