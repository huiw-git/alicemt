---
title: Setting Up Database Mirroring (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: da45efed-55eb-4c71-be34-ac2589dfce8d
---
# Setting Up Database Mirroring (SQL Server)
  This section describes the prerequisites, recommendations, and steps for setting up database mirroring. For an introduction to database mirroring, see [Database Mirroring &#40;SQL Server&#41;](../Topic/Database%20Mirroring%20\(SQL%20Server\).md).  
  
> [!IMPORTANT]  
>  We recommend that you configure database mirroring during off\-peak hours because configuration can impact performance.  
  
 **In this Topic:**  
  
-   [Preparing Server Instances to Participate in Database Mirroring](#PrepareInstances)  
  
-   [Overview: Establishing a Database Mirroring](#EstablishUsingWinAuthentication)  
  
-   [In This Section](#InThisSection)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="PrepareInstances"></a> Preparing a Server Instance to Host a Mirror Server  
 For each database mirroring session:  
  
1.  The principal server, mirror server, and witness, if any, must be hosted by separate server instances, which should be on separate host systems. Each of the server instances requires a database mirroring endpoint. If you need to create a database mirroring endpoint, ensure that it is accessible to the other server instances.  
  
     The form of authentication used for database mirroring by a server instance is a property of its database mirroring endpoint. Two types of transport security are available for database mirroring: Windows Authentication or certificate\-based authentication. For more information, see [Transport Security for Database Mirroring and Always On Availability Groups &#40;SQL Server&#41;](../Topic/Transport%20Security%20for%20Database%20Mirroring%20and%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md).  
  
     The requirements for network access are specific to the form of authentication, as follows:  
  
    -   **If using Windows Authentication**  
  
         If server instances are running under different domain user accounts, each requires a login in the **master** database of the others. If the login does not exist, you must create it. For more information, see [Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../Topic/Allow%20Network%20Access%20to%20a%20Database%20Mirroring%20Endpoint%20Using%20Windows%20Authentication%20\(SQL%20Server\).md).  
  
    -   **If using certificates**  
  
         To enable certificate authentication for database mirroring on a given server instance, the system administrator must configure each server instance to use certificates on both outbound and inbound connections. Outbound connections must be configured first. For more information, see [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](../Topic/Use%20Certificates%20for%20a%20Database%20Mirroring%20Endpoint%20\(Transact-SQL\).md).  
  
2.  Make sure that logins exist on the mirror server for all the database users. For more information, see [Set Up Login Accounts for Database Mirroring or Always On Availability Groups &#40;SQL Server&#41;](../Topic/Set%20Up%20Login%20Accounts%20for%20Database%20Mirroring%20or%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md).  
  
3.  On the server instance that will host the mirror database, set up the rest of the environment that is required for the mirrored database. For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../Topic/Manage%20Metadata%20When%20Making%20a%20Database%20Available%20on%20Another%20Server%20Instance%20\(SQL%20Server\).md).  
  
##  <a name="EstablishUsingWinAuthentication"></a> Overview: Establishing a Database Mirroring Session  
 The basic steps for establishing a mirroring session are as follows:  
  
1.  Create the mirror database by restoring the following backups, using RESTORE WITH NORECOVERY on every restore operation:  
  
    1.  Restore a recent full database backup of the principal database, after making sure that the principal database was already using the full recovery model when the backup was taken. The mirror database must have the same name as the principal database.  
  
    2.  If you have taken any differential backups of the database since the restored full backup, restore your most recent differential backup.  
  
    3.  Restore all the log backups done since the full or differential database backup.  
  
     For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](../Topic/Prepare%20a%20Mirror%20Database%20for%20Mirroring%20\(SQL%20Server\).md).  
  
    > [!IMPORTANT]  
    >  Complete the remaining setup steps as soon as you can after taking the backup of the principal database. Before you can start mirroring on the partners, you should create a current log backup on the original database and restore it to the future mirror database.  
  
2.  You can set up mirroring by using either [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] or the Database Mirroring Wizard. For more information, see one of the following:  
  
    -   [Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;](../Topic/Establish%20a%20Database%20Mirroring%20Session%20Using%20Windows%20Authentication%20\(Transact-SQL\).md)  
  
    -   [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](../Topic/Establish%20a%20Database%20Mirroring%20Session%20Using%20Windows%20Authentication%20\(SQL%20Server%20Management%20Studio\).md)  
  
3.  By default a session is set to full transaction safety \(SAFETY is set to FULL\), which starts the session in synchronous, high\-safety mode without automatic failover. You can reconfigure the session to run in high\-safety mode with automatic failover or in asynchronous, high\-performance mode, as follows:  
  
    -   **High\-safety mode with automatic failover**  
  
         If you want a high\-safety mode session to support automatic failover, add a witness server instance.  
  
         **To add a witness**  
  
        -   [Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;](../Topic/Add%20a%20Database%20Mirroring%20Witness%20Using%20Windows%20Authentication%20\(Transact-SQL\).md)  
  
        -   [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](../Topic/Establish%20a%20Database%20Mirroring%20Session%20Using%20Windows%20Authentication%20\(SQL%20Server%20Management%20Studio\).md)  
  
        > [!NOTE]  
        >  The database owner can turn off the witness for a database at any time. Turning off the witness is equivalent to having no witness, and automatic failover cannot occur.  
  
    -   **High\-performance mode**  
  
         Alternatively, if you do not want automatic failover and you prefer to emphasize performance over availability, turn off transaction safety. For more information, see [Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;](../Topic/Change%20Transaction%20Safety%20in%20a%20Database%20Mirroring%20Session%20\(Transact-SQL\).md).  
  
        > [!NOTE]  
        >  In high\-performance mode, WITNESS needs to be set to OFF. For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](../Topic/Quorum:%20How%20a%20Witness%20Affects%20Database%20Availability%20\(Database%20Mirroring\).md).  
  
> [!NOTE]  
>  For an example of using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] to set up database mirroring using Microsoft Windows Authentication, see [Example: Setting Up Database Mirroring Using Windows Authentication &#40;Transact-SQL&#41;](../Topic/Example:%20Setting%20Up%20Database%20Mirroring%20Using%20Windows%20Authentication%20\(Transact-SQL\).md).  
>   
>  For an example of using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] to set up database mirroring using certificate\-based security, see [Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;](../Topic/Example:%20Setting%20Up%20Database%20Mirroring%20Using%20Certificates%20\(Transact-SQL\).md).  
  
 [&#91;Top&#93;](#Top)  
  
##  <a name="InThisSection"></a> In This Section  
 [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](../Topic/Prepare%20a%20Mirror%20Database%20for%20Mirroring%20\(SQL%20Server\).md)  
 Summarizes the steps for creating a mirror database or preparing a mirror database before resuming a suspended session. Also provides links to how\-to topics.  
  
 [Specify a Server Network Address &#40;Database Mirroring&#41;](../Topic/Specify%20a%20Server%20Network%20Address%20\(Database%20Mirroring\).md)  
 Describes the syntax of a server network address, how the address identifies the database mirroring endpoint of the server instance, and how to find the fully\-qualified domain name of a system.  
  
 [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](../Topic/Establish%20a%20Database%20Mirroring%20Session%20Using%20Windows%20Authentication%20\(SQL%20Server%20Management%20Studio\).md)  
 Describes how to use the Configure Database Mirroring Security Wizard to start database mirroring on a database.  
  
 [Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;](../Topic/Establish%20a%20Database%20Mirroring%20Session%20Using%20Windows%20Authentication%20\(Transact-SQL\).md)  
 Describes the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] steps for setting up database mirroring.  
  
 [Example: Setting Up Database Mirroring Using Windows Authentication &#40;Transact-SQL&#41;](../Topic/Example:%20Setting%20Up%20Database%20Mirroring%20Using%20Windows%20Authentication%20\(Transact-SQL\).md)  
 Contains an example of all the stages required to create a database mirroring session with a witness, using Windows Authentication.  
  
 [Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;](../Topic/Example:%20Setting%20Up%20Database%20Mirroring%20Using%20Certificates%20\(Transact-SQL\).md)  
 Contains an example of all the stages required to create a database mirroring session with a witness, using certificate\-based authentication.  
  
 [Set Up Login Accounts for Database Mirroring or Always On Availability Groups &#40;SQL Server&#41;](../Topic/Set%20Up%20Login%20Accounts%20for%20Database%20Mirroring%20or%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)  
 Describes creating a login for a remote server instance that is using a different account than the local server instance.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **SQL Server Management Studio**  
  
-   [Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;](../Topic/Start%20the%20Configuring%20Database%20Mirroring%20Security%20Wizard%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](../Topic/Establish%20a%20Database%20Mirroring%20Session%20Using%20Windows%20Authentication%20\(SQL%20Server%20Management%20Studio\).md)  
  
 **Transact\-SQL**  
  
-   [Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../Topic/Allow%20Network%20Access%20to%20a%20Database%20Mirroring%20Endpoint%20Using%20Windows%20Authentication%20\(SQL%20Server\).md)  
  
-   [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](../Topic/Allow%20a%20Database%20Mirroring%20Endpoint%20to%20Use%20Certificates%20for%20Outbound%20Connections%20\(Transact-SQL\).md)  
  
-   [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;](../Topic/Allow%20a%20Database%20Mirroring%20Endpoint%20to%20Use%20Certificates%20for%20Inbound%20Connections%20\(Transact-SQL\).md)  
  
-   [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](../Topic/Create%20a%20Database%20Mirroring%20Endpoint%20for%20Windows%20Authentication%20\(Transact-SQL\).md)  
  
-   [Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;](../Topic/Establish%20a%20Database%20Mirroring%20Session%20Using%20Windows%20Authentication%20\(Transact-SQL\).md)  
  
-   [Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;](../Topic/Add%20a%20Database%20Mirroring%20Witness%20Using%20Windows%20Authentication%20\(Transact-SQL\).md)  
  
-   [Set Up a Mirror Database to Use the Trustworthy Property &#40;Transact-SQL&#41;](../Topic/Set%20Up%20a%20Mirror%20Database%20to%20Use%20the%20Trustworthy%20Property%20\(Transact-SQL\).md)  
  
 **Transact\-SQL\/SQL Server Management Studio**  
  
-   [Upgrading Mirrored Instances](../../Topics\TopicNameNotContainA/Upgrading-Mirrored-Instances.md)  
  
-   [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](../Topic/Prepare%20a%20Mirror%20Database%20for%20Mirroring%20\(SQL%20Server\).md)  
  
-   [Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;](../Topic/Troubleshoot%20Database%20Mirroring%20Configuration%20\(SQL%20Server\).md)  
  
 [&#91;Top&#93;](#Top)  
  
## See Also  
 [Database Mirroring &#40;SQL Server&#41;](../Topic/Database%20Mirroring%20\(SQL%20Server\).md)   
 [Database Mirroring: Interoperability and Coexistence &#40;SQL Server&#41;](../Topic/Database%20Mirroring:%20Interoperability%20and%20Coexistence%20\(SQL%20Server\).md)   
 [Transport Security for Database Mirroring and Always On Availability Groups &#40;SQL Server&#41;](../Topic/Transport%20Security%20for%20Database%20Mirroring%20and%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Specify a Server Network Address &#40;Database Mirroring&#41;](../Topic/Specify%20a%20Server%20Network%20Address%20\(Database%20Mirroring\).md)  
  
  