---
title: Encrypted Databases with Always On Availability Groups (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 09eb6ebc-3051-4fff-86a5-93524507b1fc
---
# Encrypted Databases with Always On Availability Groups (SQL Server)
  This topic contains information about the using currently encrypted or recently decrypted databases with [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
 **In this Topic:**  
  
-   [Limitations and Restrictions](#Restrictions)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   If a database is encrypted or even contains a Database Encryption Key \(DEK\), you cannot use the [!INCLUDE[ssAoNewAgWiz](../../Token\Other/ssAoNewAgWiz_md.md)] or [!INCLUDE[ssAoAddDbWiz](../../Token\Other/ssAoAddDbWiz_md.md)] to add the database to an availability group. Even if an encrypted database has been decrypted, its log backups might contain encrypted data. In this case, full initial data synchronization could fail on the database. This is because the restore log operation might require the certificate that was used by the database encryption keys \(DEKs\), and that certificate might be unavailable.  
  
     To make a decrypted database eligible to add to an availability group using the wizard:  
  
    1.  Create a log backup of the primary database.  
  
    2.  Create a full database backup of the primary database.  
  
    3.  Restore the database backup on the server instance that hosts the secondary replica.  
  
    4.  Create a new log backup from primary database.  
  
    5.  Restore this log backup on the secondary database.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](../Topic/Manually%20Prepare%20a%20Secondary%20Database%20for%20an%20Availability%20Group%20\(SQL%20Server\).md)  
  
-   [Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Availability%20Group%20Wizard%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Add%20Database%20to%20Availability%20Group%20Wizard%20\(SQL%20Server%20Management%20Studio\).md)  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Transparent Data Encryption &#40;TDE&#41;](../Topic/Transparent%20Data%20Encryption%20\(TDE\).md)  
  
  