---
title: Example: Setting Up Database Mirroring Using Certificates (Transact-SQL)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: df489ecd-deee-465c-a26a-6d1bef6d7b66
---
# Example: Setting Up Database Mirroring Using Certificates (Transact-SQL)
  This example shows all the stages required to create a database mirroring session using certificate\-based authentication. The examples in this topic use [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. Unless you can guarantee that your network is secure, we recommend that you use encryption for database mirroring connections.  
  
 When copying a certificate to another system, use a secure copy method. Be extremely careful to keep all of your certificates secure.  
  
##  <a name="ExampleH2"></a> Example  
 The following example demonstrates what must be done on one partner that resides on HOST\_A. In this example, the two partners are the default server instances on three computer systems. The two server instances run in nontrusted Windows domains, so certificate\-based authentication is required.  
  
 The initial principal role is taken by HOST\_A, and the mirror role is taken by HOST\_B.  
  
 Setting up database mirroring using certificates involves four general stages, of which three stages—1, 2, and 4—are demonstrated by this example. These stages are as follows:  
  
1.  [Configuring Outbound Connections](#ConfiguringOutboundConnections)  
  
     This example shows the steps for:  
  
    1.  Configuring Host\_A for outbound connections.  
  
    2.  Configuring Host\_B for outbound connections.  
  
     For information about this stage of setting up database mirroring, see [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](../Topic/Allow%20a%20Database%20Mirroring%20Endpoint%20to%20Use%20Certificates%20for%20Outbound%20Connections%20\(Transact-SQL\).md).  
  
2.  [Configuring Inbound Connections](#ConfigureInboundConnections)  
  
     This example shows the steps for:  
  
    1.  Configuring Host\_A for inbound connections.  
  
    2.  Configuring Host\_B for inbound connections.  
  
     For information about this stage of setting up database mirroring, see [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;](../Topic/Allow%20a%20Database%20Mirroring%20Endpoint%20to%20Use%20Certificates%20for%20Inbound%20Connections%20\(Transact-SQL\).md).  
  
3.  Creating the Mirror Database  
  
     For information on how to create a mirror database, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](../Topic/Prepare%20a%20Mirror%20Database%20for%20Mirroring%20\(SQL%20Server\).md).  
  
4.  [Configuring the Mirroring Partners](#ConfigureMirroringPartners)  
  
###  <a name="ConfiguringOutboundConnections"></a> Configuring Outbound Connections  
 **To configure Host\_A for outbound connections**  
  
1.  On the master database, create the database master key, if needed.  
  
    ```  
    USE master;  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<1_Strong_Password!>';  
    GO  
    ```  
  
2.  Make a certificate for this server instance.  
  
    ```  
    USE master;  
    CREATE CERTIFICATE HOST_A_cert   
       WITH SUBJECT = 'HOST_A certificate';  
    GO  
    ```  
  
3.  Create a mirroring endpoint for server instance using the certificate.  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
       STATE = STARTED  
       AS TCP (  
          LISTENER_PORT=7024  
          , LISTENER_IP = ALL  
       )   
       FOR DATABASE_MIRRORING (   
          AUTHENTICATION = CERTIFICATE HOST_A_cert  
          , ENCRYPTION = REQUIRED ALGORITHM AES  
          , ROLE = ALL  
       );  
    GO  
    ```  
  
4.  Back up the HOST\_A certificate, and copy it to other system, HOST\_B.  
  
    ```  
    BACKUP CERTIFICATE HOST_A_cert TO FILE = 'C:\HOST_A_cert.cer';  
    GO  
    ```  
  
5.  Using any secure copy method, copy C:\\HOST\_A\_cert.cer to HOST\_B.  
  
 **To configure Host\_B for outbound connections**  
  
1.  On the master database, create the database master key, if needed.  
  
    ```  
    USE master;  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<Strong_Password_#2>';  
    GO  
    ```  
  
2.  Make a certificate on the HOST\_B server instance.  
  
    ```  
    CREATE CERTIFICATE HOST_B_cert   
       WITH SUBJECT = 'HOST_B certificate for database mirroring';  
    GO  
    ```  
  
3.  Create a mirroring endpoint for the server instance on HOST\_B.  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
       STATE = STARTED  
       AS TCP (  
          LISTENER_PORT=7024  
          , LISTENER_IP = ALL  
       )   
       FOR DATABASE_MIRRORING (   
          AUTHENTICATION = CERTIFICATE HOST_B_cert  
          , ENCRYPTION = REQUIRED ALGORITHM AES  
          , ROLE = ALL  
       );  
    GO  
    ```  
  
4.  Back up HOST\_B certificate.  
  
    ```  
    BACKUP CERTIFICATE HOST_B_cert TO FILE = 'C:\HOST_B_cert.cer';  
    GO   
    ```  
  
5.  Using any secure copy method, copy C:\\HOST\_B\_cert.cer to HOST\_A.  
  
 For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](../Topic/Allow%20a%20Database%20Mirroring%20Endpoint%20to%20Use%20Certificates%20for%20Outbound%20Connections%20\(Transact-SQL\).md).  
  
 [&#91;Top of Example&#93;](#ExampleH2)  
  
###  <a name="ConfigureInboundConnections"></a> Configuring Inbound Connections  
 **To configure Host\_A for inbound connections**  
  
1.  Create a login on HOST\_A for HOST\_B.  
  
    ```  
    USE master;  
    CREATE LOGIN HOST_B_login WITH PASSWORD = '1Sample_Strong_Password!@#';  
    GO  
    ```  
  
2.  \-\-Create a user for that login.  
  
    ```  
    CREATE USER HOST_B_user FOR LOGIN HOST_B_login;  
    GO  
    ```  
  
3.  \-\-Associate the certificate with the user.  
  
    ```  
    CREATE CERTIFICATE HOST_B_cert  
       AUTHORIZATION HOST_B_user  
       FROM FILE = 'C:\HOST_B_cert.cer'  
    GO  
    ```  
  
4.  Grant CONNECT permission on the login for the remote mirroring endpoint.  
  
    ```  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [HOST_B_login];  
    GO  
    ```  
  
 **To configure Host\_B for inbound connections**  
  
1.  Create a login on HOST\_B for HOST\_A.  
  
    ```  
    USE master;  
    CREATE LOGIN HOST_A_login WITH PASSWORD = '=Sample#2_Strong_Password2';  
    GO  
    ```  
  
2.  Create a user for that login.  
  
    ```  
    CREATE USER HOST_A_user FOR LOGIN HOST_A_login;  
    GO  
    ```  
  
3.  Associate the certificate with the user.  
  
    ```  
    CREATE CERTIFICATE HOST_A_cert  
       AUTHORIZATION HOST_A_user  
       FROM FILE = 'C:\HOST_A_cert.cer'  
    GO  
    ```  
  
4.  Grant CONNECT permission on the login for the remote mirroring endpoint.  
  
    ```  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [HOST_A_login];  
    GO  
    ```  
  
> [!IMPORTANT]  
>  If you intend to run in high\-safety mode with automatic failover, you must repeat the same setup steps to configure the witness for outbound and inbound connections. Setting up the inbound connections when a witness is involved requires that you set up logins and users for the witness on both of the partners and for both partners on the witness.  
  
 For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;](../Topic/Allow%20a%20Database%20Mirroring%20Endpoint%20to%20Use%20Certificates%20for%20Inbound%20Connections%20\(Transact-SQL\).md).  
  
 [&#91;Top of Example&#93;](#ExampleH2)  
  
### Creating the Mirror Database  
 For information on how to create a mirror database, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](../Topic/Prepare%20a%20Mirror%20Database%20for%20Mirroring%20\(SQL%20Server\).md).  
  
###  <a name="ConfigureMirroringPartners"></a> Configuring the Mirroring Partners  
  
1.  On the mirror server instance on HOST\_B, set the server instance on HOST\_A as the partner \(making it the initial principal server instance\). Substitute a valid network address for `TCP://HOST_A.Mydomain.Corp.Adventure-Works``.com:7024`. For more information, see [Specify a Server Network Address &#40;Database Mirroring&#41;](../Topic/Specify%20a%20Server%20Network%20Address%20\(Database%20Mirroring\).md).  
  
    ```  
    --At HOST_B, set server instance on HOST_A as partner (principal server):  
    ALTER DATABASE AdventureWorks   
        SET PARTNER = 'TCP://HOST_A.Mydomain.Corp.Adventure-Works.com:7024';  
    GO  
    ```  
  
2.  On the principal server instance on HOST\_A, set the server instance on HOST\_B as the partner \(making it the initial mirror server instance\). Substitute a valid network address for `TCP://HOST_B.Mydomain.Corp.Adventure-Works.com:7024`.  
  
    ```  
    --At HOST_A, set server instance on HOST_B as partner (mirror server).  
    ALTER DATABASE AdventureWorks   
        SET PARTNER = 'TCP://HOST_B.Mydomain.Corp.Adventure-Works.com:7024';  
    GO  
    ```  
  
3.  This example assumes that the session will be running in high\-performance mode. To configure this session for high\-performance mode, on the principal server instance \(on HOST\_A\), set transaction safety to OFF.  
  
    ```  
    --Change to high-performance mode by turning off transacton safety.  
    ALTER DATABASE AdventureWorks   
        SET PARTNER SAFETY OFF  
    GO  
    ```  
  
    > [!NOTE]  
    >  If you intend to run in high\-safety mode with automatic failover, leave transaction safety set to FULL \(the default setting\) and add the witness as soon as possible after executing the second SET PARTNER **'***partner\_server***'** statement. Note that the witness must first be configured for outbound and inbound connections.  
  
 [&#91;Top of Example&#93;](#ExampleH2)  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](../Topic/Prepare%20a%20Mirror%20Database%20for%20Mirroring%20\(SQL%20Server\).md)  
  
-   [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;](../Topic/Allow%20a%20Database%20Mirroring%20Endpoint%20to%20Use%20Certificates%20for%20Inbound%20Connections%20\(Transact-SQL\).md)  
  
-   [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](../Topic/Allow%20a%20Database%20Mirroring%20Endpoint%20to%20Use%20Certificates%20for%20Outbound%20Connections%20\(Transact-SQL\).md)  
  
-   [Management of Logins and Jobs After Role Switching &#40;SQL Server&#41;](../Topic/Management%20of%20Logins%20and%20Jobs%20After%20Role%20Switching%20\(SQL%20Server\).md)  
  
-   [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../Topic/Manage%20Metadata%20When%20Making%20a%20Database%20Available%20on%20Another%20Server%20Instance%20\(SQL%20Server\).md) \(SQL Server\)  
  
-   [Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;](../Topic/Troubleshoot%20Database%20Mirroring%20Configuration%20\(SQL%20Server\).md)  
  
## See Also  
 [Transport Security for Database Mirroring and Always On Availability Groups &#40;SQL Server&#41;](../Topic/Transport%20Security%20for%20Database%20Mirroring%20and%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Specify a Server Network Address &#40;Database Mirroring&#41;](../Topic/Specify%20a%20Server%20Network%20Address%20\(Database%20Mirroring\).md)   
 [The Database Mirroring Endpoint &#40;SQL Server&#41;](../Topic/The%20Database%20Mirroring%20Endpoint%20\(SQL%20Server\).md)   
 [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](../Topic/Use%20Certificates%20for%20a%20Database%20Mirroring%20Endpoint%20\(Transact-SQL\).md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20\(Transact-SQL\).md)   
 [Security Center for SQL Server Database Engine and Azure SQL Database](../../Topics\TopicNameNotContainA/Security-Center-for-SQL-Server-Database-Engine-and-Azure-SQL-Database.md)  
  
  