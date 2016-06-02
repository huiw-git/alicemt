---
title: Service Accounts (Configure Database Mirroring Security Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d58d8f93-7888-4d66-af4d-969ef6a2dbee
---
# Service Accounts (Configure Database Mirroring Security Wizard)
  When using Windows Authentication, if the server instances use different accounts, specify the service accounts for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. These service accounts must all be domain accounts \(in the same or trusted domains\).  
  
 If all the server instances use the same domain account or use certificate\-based authentication, leave the fields blank. Simply click **Finish**, and the wizard automatically configures the accounts based on the account of the current wizard.  
  
> [!IMPORTANT]  
>  If the database mirroring endpoints of the server instances are configured to use certificates, you must leave the service account fields empty.  
  
 **To configure database mirroring by using SQL Server Management Studio**  
  
-   [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](../Topic/Establish%20a%20Database%20Mirroring%20Session%20Using%20Windows%20Authentication%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;](../Topic/Start%20the%20Configuring%20Database%20Mirroring%20Security%20Wizard%20\(SQL%20Server%20Management%20Studio\).md)  
  
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
 [Database Properties &#40;Mirroring Page&#41;](../Topic/Database%20Properties%20\(Mirroring%20Page\).md)   
 [Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../Topic/Start%20Database%20Mirroring%20Monitor%20\(SQL%20Server%20Management%20Studio\).md)   
 [Database Mirroring &#40;SQL Server&#41;](../Topic/Database%20Mirroring%20\(SQL%20Server\).md)   
 [Set Up Login Accounts for Database Mirroring or Always On Availability Groups &#40;SQL Server&#41;](../Topic/Set%20Up%20Login%20Accounts%20for%20Database%20Mirroring%20or%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)  
  
  