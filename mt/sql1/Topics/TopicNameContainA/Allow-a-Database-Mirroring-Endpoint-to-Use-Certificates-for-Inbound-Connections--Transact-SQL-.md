---
title: Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections (Transact-SQL)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5d48bb98-61f0-4b99-8f1a-b53f831d63d0
---
# Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections (Transact-SQL)
This topic describes the steps for configuring server instances to use certificates to authenticate inbound connections for database mirroring. Before you can set up inbound connections, you must configure outbound connections on each server instance. For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections (Transact-SQL)](../../Topics/TopicNameContainA/Allow-a-Database-Mirroring-Endpoint-to-Use-Certificates-for-Outbound-Connections--Transact-SQL-.md).  
  
 The process of configuring inbound connections, involves the following general steps:  
  
1.  Create a login for other system.  
  
2.  Create a user for that login.  
  
3.  Obtain the certificate for the mirroring endpoint of the other server instance.  
  
4.  Associate the certificate with the user created in step 2.  
  
5.  Grant CONNECT permission on the login for that mirroring endpoint.  
  
 If there is a witness, you must also set up inbound connections for it. This requires setting up logins, users, and certificates for the witness on both of the partners, and vice versa.  
  
 The following procedure describes these steps in detail. For each step, the procedure provides an example for configuring a server instance on a system named HOST_A. The accompanying Example section demonstrates the same steps for another server instance on a system named HOST_B.  
  
### To configure server instances for inbound mirroring connections (on HOST_A)  
  
1.  Create a login for the other system.  
  
     The following example creates a login for the system, HOST_B, in the **master** database of the server instance on HOST_A; in this example, the login is named `HOST_B_login`. Substitute a password of your own for the sample password.  
  
    ```  
    USE master;  
    CREATE LOGIN HOST_B_login   
       WITH PASSWORD = '1Sample_Strong_Password!@#';  
    GO  
    ```  
  
     For more information, see [CREATE LOGIN (Transact-SQL)](assetId:///eb737149-7c92-4552-946b-91085d8b1b01).  
  
     To view the logins on this server instance, you can use the following [!INCLUDE[tsql](../../Topics/TopicNameContainA/includes/tsql_md.md)] statement:  
  
    ```  
    SELECT * FROM sys.server_principals  
    ```  
  
     For more information, see [sys.server_principals (Transact-SQL)](assetId:///c5dbe0d8-a1c8-4dc4-b9b1-22af20effd37).  
  
2.  Create a user for that login.  
  
     The following example creates a user, `HOST_B_user`, for the login created in the preceding step.  
  
    ```  
    USE master;  
    CREATE USER HOST_B_user FOR LOGIN HOST_B_login;  
    GO  
    ```  
  
     For more information, see [CREATE USER (Transact-SQL)](assetId:///01de7476-4b25-4d58-85b7-1118fe64aa80).  
  
     To view the users on this server instance, you can use the following [!INCLUDE[tsql](../../Topics/TopicNameContainA/includes/tsql_md.md)] statement:  
  
    ```  
    SELECT * FROM sys.sysusers;  
    ```  
  
     For more information, see [sys.sysusers (Transact-SQL)](assetId:///5f0e6a8d-c983-44f6-97e9-aab5bff67d18).  
  
3.  Obtain the certificate for the mirroring endpoint of the other server instance.  
  
     If you have not already done so when configuring outbound connections, obtain a copy of the certificate for the mirroring endpoint of the remote server instance. To do this, back up the certificate on that server instance as described in [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections (Transact-SQL)](../../Topics/TopicNameContainA/Allow-a-Database-Mirroring-Endpoint-to-Use-Certificates-for-Outbound-Connections--Transact-SQL-.md). When copying a certificate to another system, use a secure copy method. Be extremely careful to keep all of your certificates secure.  
  
     For more information, see [BACKUP CERTIFICATE (Transact-SQL)](assetId:///509b9462-819b-4c45-baae-3d2d90d14a1c).  
  
4.  Associate the certificate with the user created in step 2.  
  
     The following example, associates the certificate of HOST_B with its user on HOST_A.  
  
    ```  
    USE master;  
    CREATE CERTIFICATE HOST_B_cert  
       AUTHORIZATION HOST_B_user  
       FROM FILE = 'C:\HOST_B_cert.cer'  
    GO  
    ```  
  
     For more information, see [CREATE CERTIFICATE (Transact-SQL)](assetId:///a4274b2b-4cb0-446a-a956-1c8e6587515d).  
  
     To view the certificates on this server instance, use the following [!INCLUDE[tsql](../../Topics/TopicNameContainA/includes/tsql_md.md)] statement:  
  
    ```  
    SELECT * FROM sys.certificates  
    ```  
  
     For more information, see [sys.certificates (Transact-SQL)](assetId:///e5046102-a65c-401e-b80d-05636884dec9).  
  
5.  Grant CONNECT permission on the login for the remote mirroring endpoint.  
  
     For example, to grant permission on HOST_A to the remote server instance on HOST_B to connect to its local login—that is, to connect to `HOST_B_login`—use the following [!INCLUDE[tsql](../../Topics/TopicNameContainA/includes/tsql_md.md)] statements:  
  
    ```  
    USE master;  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [HOST_B_login];  
    GO  
    ```  
  
     For more information, see [GRANT Endpoint Permissions (Transact-SQL)](assetId:///9eda885c-fc3a-4c9d-8de6-ce07fb35a934).  
  
 This completes setting up certificate authentication for HOST_B to log in to HOST_A.  
  
 You now need to perform the equivalent inbound steps for HOST_A on HOST_B. These steps are illustrated in the inbound portion of the example in the Example section, below.  
  
## Example  
 The following example demonstrates configuring HOST_B for inbound connections.  
  
> [!NOTE]  
>  This example uses a certificate file containing the HOST_A certificate that is created by a code snippet in [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections (Transact-SQL)](../../Topics/TopicNameContainA/Allow-a-Database-Mirroring-Endpoint-to-Use-Certificates-for-Outbound-Connections--Transact-SQL-.md).  
  
```  
USE master;  
--On HOST_B, create a login for HOST_A.  
CREATE LOGIN HOST_A_login WITH PASSWORD = 'AStrongPassword!@#';  
GO  
--Create a user, HOST_A_user, for that login.  
CREATE USER HOST_A_user FOR LOGIN HOST_A_login  
GO  
--Obtain HOST_A certificate. (See the note   
--   preceding this example.)  
--Asscociate this certificate with the user, HOST_A_user.  
CREATE CERTIFICATE HOST_A_cert  
   AUTHORIZATION HOST_A_user  
   FROM FILE = 'C:\HOST_A_cert.cer';  
GO  
--Grant CONNECT permission for the server instance on HOST_A.  
GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO HOST_A_login  
GO  
```  
  
 If you intend to run in high-safety mode with automatic failover, you must repeat the same set up steps to configure the witness for outbound and inbound connections.  
  
 For information on creating a mirror database, including a Transact-SQL example, see [Prepare a Mirror Database for Mirroring (SQL Server)](../../Topics/TopicNameContainA/Prepare-a-Mirror-Database-for-Mirroring--SQL-Server-.md).  
  
 For a Transact-SQL example of establishing a high-performance mode session, see [Example: Setting Up Database Mirroring Using Certificates (Transact-SQL)](../Topic/Example:%20Setting%20Up%20Database%20Mirroring%20Using%20Certificates%20\(Transact-SQL\).md).  
  
## .NET Framework Security  
 When copying a certificate to another system, use a secure copy method. Be extremely careful to keep all of your certificates secure.  
  
## See Also  
 [Transport Security for Database Mirroring and Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Transport-Security-for-Database-Mirroring-and-Always-On-Availability-Groups--SQL-Server-.md)   
 [GRANT Endpoint Permissions (Transact-SQL)](assetId:///9eda885c-fc3a-4c9d-8de6-ce07fb35a934)   
 [Set Up an Encrypted Mirror Database](../../Topics/TopicNameNotContainA/Set-Up-an-Encrypted-Mirror-Database.md)   
 [The Database Mirroring Endpoint (SQL Server)](../../Topics/TopicNameNotContainA/The-Database-Mirroring-Endpoint--SQL-Server-.md)   
 [Troubleshoot Database Mirroring Configuration (SQL Server)](../../Topics/TopicNameNotContainA/Troubleshoot-Database-Mirroring-Configuration--SQL-Server-.md)