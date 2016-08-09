---
title: "Transport Security for Database Mirroring and Always On Availability Groups (SQL Server)"
ms.custom: na
ms.date: 2016-05-17
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 49239d02-964e-47c0-9b7f-2b539151ee1b
caps.latest.revision: 60
caps.handback.revision: 0
manager: jhubbard
---
# Transport Security for Database Mirroring and Always On Availability Groups (SQL Server)
Transport security involves authentication and, optionally, encryption of messages exchanged between the databases. For database mirroring and [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/tokens/ssHADR_md.md)], authentication and encryption are configured on the database mirroring endpoint. For an introduction to database mirroring endpoints, see [The Database Mirroring Endpoint (SQL Server)](../../Topics/TopicNameNotContainA/The-Database-Mirroring-Endpoint--SQL-Server-.md).  
  
 **In this Topic:**  
  
-   [Authentication](#Authentication)  
  
-   [Data Encryption](#DataEncryption)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="Authentication"></a> Authentication  
 Authentication is the process of verifying that a user is who the user claims to be. Connections between database mirroring endpoints require authentication. Connection requests from a partner or witness, if any, must be authenticated.  
  
 The type of authentication used by a server instance for database mirroring or [!INCLUDE[ssHADR](../../Topics/TopicNameContainA/tokens/ssHADR_md.md)] is a property of the database mirroring endpoint. Two types of transport security are available for database mirroring endpoints: Windows Authentication (the Security Support Provider Interface (SSPI)) and certificate-based authentication.  
  
### Windows Authentication  
 Under Windows Authentication, each server instance logs in to the other side using the Windows credentials of the Windows user account under which the process is running. Windows Authentication might require some manual configuration of login accounts, as follows:  
  
-   If the instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] run as services under the same domain account, no extra configuration is required.  
  
-   If the instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] run as services under different domain accounts (in the same or trusted domains), the login of each account must be created in **master** on each of the other server instances, and that login must be granted CONNECT permissions on the endpoint.  
  
-   If the instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] run as the Network Service account, the login of the each host computer account (*DomainName***\\***ComputerName$*) must be created in **master** on each of the other servers, and that login must be granted CONNECT permissions on the endpoint. This is because a server instance running under the Network Service account authenticates using the domain account of the host computer.  
  
> [!NOTE]  
>  For an example of setting up a database mirroring session using Windows Authentication, see [Example: Setting Up Database Mirroring Using Windows Authentication (Transact-SQL)](../Topic/Example:%20Setting%20Up%20Database%20Mirroring%20Using%20Windows%20Authentication%20\(Transact-SQL\).md).  
  
### Certificates  
 In some situations, such as when server instances are not in trusted domains or when [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is running as a local service, Windows Authentication is unavailable. In such cases, instead of user credentials, certificates are required to authenticate connection requests. The mirroring endpoint of each server instance must be configured with its own locally created certificate.  
  
 The encryption method is established when the certificate is created. For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections (Transact-SQL)](../../Topics/TopicNameContainA/Allow-a-Database-Mirroring-Endpoint-to-Use-Certificates-for-Outbound-Connections--Transact-SQL-.md). Carefully manage the certificates that you use.  
  
 A server instance uses the private key of its own certificate to establish its identity when setting up a connection. The server instance that receives the connection request uses the public key of the sender's certificate to authenticate the sender's identity. For example, consider two server instances, Server_A and Server_B. Server_A uses its private key to encrypt the connection header before sending a connection request to Server_B. Server_B uses the public key of Server_A's certificate to decrypt the connection header. If the decrypted header is correct, Server_B knows that the header was encrypted by Server_A, and the connection is authenticated. If the decrypted header is incorrect, Server_B knows that the connection request is inauthentic and refuses the connection.  
  
##  <a name="DataEncryption"></a> Data Encryption  
 By default, a database mirroring endpoint requires encryption of data sent over mirroring connections. In this case, the endpoint can connect only to endpoints that also use encryption. Unless you can guarantee that your network is secure, we recommend that you require encryption for your database mirroring connections. However, you can disable encryption or make it supported, but not required. If encryption is disabled, data is never encrypted and the endpoint cannot connect to an endpoint that requires encryption. If encryption is supported, data is encrypted only if the opposite endpoint either supports or requires encryption.  
  
> [!NOTE]  
>  Mirroring endpoints created by [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] are created with encryption either required or disabled. To change the encryption setting to SUPPORTED, use the ALTER ENDPOINT [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statement. For more information, see [ALTER ENDPOINT (Transact-SQL)](assetId:///70f35566-30cf-47c6-8394-dfe5d71629d3).  
  
 Optionally, you can control the encryption algorithms that can be used by an endpoint, by specifying one of the following values for the ALGORITHM option in a CREATE ENDPOINT statement or ALTER ENDPOINT statement:  
  
|ALGORITHM value|Description|  
|---------------------|-----------------|  
|RC4|Specifies that the endpoint must use the RC4 algorithm. This is the default.<br /><br /> **\*\* Warning \*\*** The RC4 algorithm is deprecated. [!INCLUDE[ssNoteDepFutureDontUse](../../Topics/TopicNameContainA/tokens/ssNoteDepFutureDontUse_md.md)] We recommend that you use AES.|  
|AES|Specifies that the endpoint must use the AES algorithm.|  
|AES RC4|Specifies that the two endpoints will negotiate for an encryption algorithm with this endpoint giving preference to the AES algorithm.|  
|RC4 AES|Specifies that the two endpoints will negotiate for an encryption algorithm with this endpoint giving preference to the RC4 algorithm.|  
  
 If connecting endpoints specify both algorithms but in different orders, the endpoint accepting the connection wins.  
  
> [!NOTE]  
>  The RC4 algorithm is only supported for backward compatibility. New material can only be encrypted using RC4 or RC4_128 when the database is in compatibility level 90 or 100. (Not recommended.) Use a newer algorithm such as one of the AES algorithms instead. In [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)]and higher versions,  material encrypted using RC4 or RC4_128 can be decrypted in any compatibility level.  
>   
>  Though considerably faster than AES, RC4 is a relatively weak algorithm, while AES is a relatively strong algorithm. Therefore, we recommend that you use the AES algorithm.  
  
 For information about the [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] syntax for specifying encryption, see [CREATE ENDPOINT (Transact-SQL)](assetId:///6405e7ec-0b5b-4afd-9792-1bfa5a2491f6).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To configure transport security for a database mirroring endpoint**  
  
-   [Create a Database Mirroring Endpoint for Windows Authentication (Transact-SQL)](../../Topics/TopicNameContainA/Create-a-Database-Mirroring-Endpoint-for-Windows-Authentication--Transact-SQL-.md)  
  
-   [Establish a Database Mirroring Session Using Windows Authentication (SQL Server Management Studio)](../../Topics/TopicNameContainA/Establish-a-Database-Mirroring-Session-Using-Windows-Authentication--SQL-Server-Management-Studio-.md)  
  
-   [Create a Database Mirroring Endpoint for Windows Authentication (Transact-SQL)](../../Topics/TopicNameContainA/Create-a-Database-Mirroring-Endpoint-for-Windows-Authentication--Transact-SQL-.md)  
  
-   [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections (Transact-SQL)](../../Topics/TopicNameContainA/Allow-a-Database-Mirroring-Endpoint-to-Use-Certificates-for-Outbound-Connections--Transact-SQL-.md)  
  
## See Also  
 [Choose an Encryption Algorithm](../../Topics/TopicNameNotContainA/Choose-an-Encryption-Algorithm.md)   
 [ALTER ENDPOINT (Transact-SQL)](assetId:///70f35566-30cf-47c6-8394-dfe5d71629d3)   
 [DROP ENDPOINT (Transact-SQL)](assetId:///6aca7412-66a5-4fa4-86b2-061512ff2080)   
 [Security Center for SQL Server Database Engine and Azure SQL Database](../../Topics/TopicNameNotContainA/Security-Center-for-SQL-Server-Database-Engine-and-Azure-SQL-Database.md)   
 [Manage Metadata When Making a Database Available on Another Server Instance (SQL Server)](../../Topics/TopicNameContainA/Manage-Metadata-When-Making-a-Database-Available-on-Another-Server-Instance--SQL-Server-.md)   
 [The Database Mirroring Endpoint (SQL Server)](../../Topics/TopicNameNotContainA/The-Database-Mirroring-Endpoint--SQL-Server-.md)   
 [sys.database_mirroring_endpoints (Transact-SQL)](assetId:///f2285199-97ad-473c-a52d-270044dd862b)   
 [sys.dm_database_mirroring_connections](assetId:///e4df91b6-0240-45d0-ae22-cb2c0d52e0b3)   
 [Troubleshoot Database Mirroring Configuration (SQL Server)](../../Topics/TopicNameNotContainA/Troubleshoot-Database-Mirroring-Configuration--SQL-Server-.md)   
 [Troubleshoot Always On Availability Groups Configuration (SQL Server)](../../Topics/TopicNameNotContainA/Troubleshoot-Always-On-Availability-Groups-Configuration--SQL-Server-.md)