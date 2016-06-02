---
title: Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections (Transact-SQL)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 464c9096-10d6-4c5e-8bb1-19acba27ad9e
---
# Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections (Transact-SQL)
  This topic describes the steps for configuring server instances to use certificates to authenticate outbound connections for database mirroring. Outbound connection configuration must be done before you can set up inbound connections.  
  
> [!NOTE]  
>  All mirroring connections on a server instance use a single database mirroring endpoint, and you must specify the authentication method of the server instance when you create the endpoint.  
  
 The process of configuring outbound connections, involves the following general steps:  
  
1.  In the **master** database, create a database Master Key.  
  
2.  In the **master** database, create an encrypted certificate on the server instance.  
  
3.  Create an endpoint for the server instance using its certificate.  
  
4.  Back up the certificate to a file and securely copy it to the other system or systems.  
  
 You must complete these steps for each partner and the witness, if there is one.  
  
 The following procedure describes these steps in detail. For each step, the procedure provides an example for configuring a server instance on a system named HOST\_A. The accompanying Example section demonstrates the same steps for another server instance on a system named HOST\_B.  
  
## Procedure  
  
#### To configure server instances for outbound mirroring connections \(On HOST\_A\)  
  
1.  On the **master** database, create the database Master Key, if none exists. To view the existing keys for a database, use the [sys.symmetric\_keys](../Topic/sys.symmetric_keys%20\(Transact-SQL\).md) catalog view.  
  
     To create the database Master Key, use the following [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] command:  
  
    ```  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<1_Strong_Password!>';  
    GO  
    ```  
  
     Use a unique, strong password, and record it in a safe place.  
  
     For more information, see [CREATE MASTER KEY &#40;Transact-SQL&#41;](../Topic/CREATE%20MASTER%20KEY%20\(Transact-SQL\).md) and [Create a Database Master Key](../../Topics\TopicNameContainA/Create-a-Database-Master-Key.md).  
  
2.  In the **master** database, create an encrypted certificate on the server instance to use for its outbound connections for database mirroring.  
  
     For example, to create a certificate for the HOST\_A system.  
  
    > [!IMPORTANT]  
    >  If you intend to use the certificate for more than one year, specify the expiry date in UTC time by using the EXPIRY\_DATE option in your CREATE CERTIFICATE statement. Also, we recommend that you use SQL Server Management Studio to create a Policy\-Based Management rule to alert you when your certificates are expiring. Using the Policy Management **Create New Condition** dialog box, create this rule on the **@ExpirationDate** field of the **Certificate** facet. For more information, see [Administer Servers by Using Policy-Based Management](../../Topics\TopicNameNotContainA/Administer-Servers-by-Using-Policy-Based-Management.md) and [Securing SQL Server](../../Topics\TopicNameNotContainA/Securing-SQL-Server.md).  
  
    ```  
    USE master;  
    CREATE CERTIFICATE HOST_A_cert   
       WITH SUBJECT = 'HOST_A certificate for database mirroring',   
       EXPIRY_DATE = '11/30/2013';  
    GO  
    ```  
  
     For more information, see [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../Topic/CREATE%20CERTIFICATE%20\(Transact-SQL\).md).  
  
     To view the certificates in the **master** database, you can use the following [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements:  
  
    ```  
    USE master;  
    SELECT * FROM sys.certificates;  
    ```  
  
     For more information, see [sys.certificates &#40;Transact-SQL&#41;](../Topic/sys.certificates%20\(Transact-SQL\).md).  
  
3.  Ensure that the database mirroring endpoint exist on each of the server instances.  
  
     If a database mirroring endpoint already exists for the server instance, you should reuse that endpoint for any other sessions you establish on the server instance. To determine whether a database mirroring endpoint exists on a server instance and to view its configuration, use the following statement:  
  
    ```  
    SELECT name, role_desc, state_desc, connection_auth_desc, encryption_algorithm_desc   
       FROM sys.database_mirroring_endpoints;  
    ```  
  
     If no endpoint exists, create an endpoint that uses this certificate for outbound connections and that uses the certificate's credentials for verification on the other system. This is a server\-wide endpoint that is used by all mirroring sessions in which the server instance participates.  
  
     For example, to create a mirroring endpoint for the example server instance on HOST\_A.  
  
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
  
     For more information, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](../Topic/CREATE%20ENDPOINT%20\(Transact-SQL\).md).  
  
4.  Back up the certificate and copy it to the other system or systems. This is necessary in order to configure inbound connections on the other system.  
  
    ```  
    BACKUP CERTIFICATE HOST_A_cert TO FILE = 'C:\HOST_A_cert.cer';  
    GO  
    ```  
  
     For more information, see [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../Topic/BACKUP%20CERTIFICATE%20\(Transact-SQL\).md).  
  
     Copy this certificate using any secure method you choose. Be extremely careful to keep all of your certificates secure.  
  
 The example code in the preceding steps configure outbound connections on HOST\_A.  
  
 You now need to perform the equivalent outbound steps for HOST\_B. These steps are illustrated in the following Example section.  
  
## Example  
 The following example demonstrates configuring HOST\_B for outbound connections.  
  
```  
USE master;  
--Create the database Master Key, if needed.  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<Strong_Password_#2>';  
GO  
-- Make a certifcate on HOST_B server instance.  
CREATE CERTIFICATE HOST_B_cert   
   WITH SUBJECT = 'HOST_B certificate for database mirroring',   
   EXPIRY_DATE = '11/30/2013';  
GO  
--Create a mirroring endpoint for the server instance on HOST_B.  
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
--Backup HOST_B certificate.  
BACKUP CERTIFICATE HOST_B_cert TO FILE = 'C:\HOST_B_cert.cer';  
GO   
--Using any secure copy method, copy C:\HOST_B_cert.cer to HOST_A.  
```  
  
 Copy the certificate to the other system using any secure method you choose. Be extremely careful to keep all of your certificates secure.  
  
> [!IMPORTANT]  
>  After you set up outbound connections, you must configure inbound connections on each server instance for the other server instance or instances. For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;](../Topic/Allow%20a%20Database%20Mirroring%20Endpoint%20to%20Use%20Certificates%20for%20Inbound%20Connections%20\(Transact-SQL\).md).  
  
 For information on creating a mirror database, including a Transact\-SQL example, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](../Topic/Prepare%20a%20Mirror%20Database%20for%20Mirroring%20\(SQL%20Server\).md).  
  
 For a Transact\-SQL example of establishing a high\-performance mode session, see [Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;](../Topic/Example:%20Setting%20Up%20Database%20Mirroring%20Using%20Certificates%20\(Transact-SQL\).md).  
  
## .NET Framework Security  
 Unless you can guarantee that your network is secure, we recommend that you use encryption for database mirroring connections.  
  
 When copying a certificate to another system, use a secure copy method.  
  
## See Also  
 [Choose an Encryption Algorithm](../../Topics\TopicNameNotContainA/Choose-an-Encryption-Algorithm.md)   
 [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](../Topic/Prepare%20a%20Mirror%20Database%20for%20Mirroring%20\(SQL%20Server\).md)   
 [ALTER ENDPOINT &#40;Transact-SQL&#41;](../Topic/ALTER%20ENDPOINT%20\(Transact-SQL\).md)   
 [Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;](../Topic/Example:%20Setting%20Up%20Database%20Mirroring%20Using%20Certificates%20\(Transact-SQL\).md)   
 [The Database Mirroring Endpoint &#40;SQL Server&#41;](../Topic/The%20Database%20Mirroring%20Endpoint%20\(SQL%20Server\).md)   
 [Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;](../Topic/Troubleshoot%20Database%20Mirroring%20Configuration%20\(SQL%20Server\).md)   
 [Set Up an Encrypted Mirror Database](../../Topics\TopicNameNotContainA/Set-Up-an-Encrypted-Mirror-Database.md)  
  
  