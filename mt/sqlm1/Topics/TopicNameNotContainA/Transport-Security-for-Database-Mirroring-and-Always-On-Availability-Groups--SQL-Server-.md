---
title: Transport Security for Database Mirroring and Always On Availability Groups (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 49239d02-964e-47c0-9b7f-2b539151ee1b
---
# Transport Security for Database Mirroring and Always On Availability Groups (SQL Server)
  Transport security involves authentication and, optionally, encryption of messages exchanged between the databases. For database mirroring and [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)], authentication and encryption are configured on the database mirroring endpoint. For an introduction to database mirroring endpoints, see [The Database Mirroring Endpoint &#40;SQL Server&#41;](../Topic/The%20Database%20Mirroring%20Endpoint%20\(SQL%20Server\).md).  
  
 **In this Topic:**  
  
-   [Authentication](#Authentication)  
  
-   [Data Encryption](#DataEncryption)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="Authentication"></a> Authentication  
 Authentication is the process of verifying that a user is who the user claims to be. Connections between database mirroring endpoints require authentication. Connection requests from a partner or witness, if any, must be authenticated.  
  
 The type of authentication used by a server instance for database mirroring or [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] is a property of the database mirroring endpoint. Two types of transport security are available for database mirroring endpoints: Windows Authentication \(the Security Support Provider Interface \(SSPI\)\) and certificate\-based authentication.  
  
### Windows Authentication  
 Under Windows Authentication, each server instance logs in to the other side using the Windows credentials of the Windows user account under which the process is running. Windows Authentication might require some manual configuration of login accounts, as follows:  
  
-   If the instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] run as services under the same domain account, no extra configuration is required.  
  
-   If the instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] run as services under different domain accounts \(in the same or trusted domains\), the login of each account must be created in **master** on each of the other server instances, and that login must be granted CONNECT permissions on the endpoint.  
  
-   If the instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] run as the Network Service account, the login of the each host computer account \(*DomainName***\\***ComputerName$*\) must be created in **master** on each of the other servers, and that login must be granted CONNECT permissions on the endpoint. This is because a server instance running under the Network Service account authenticates using the domain account of the host computer.  
  
> [!NOTE]  
>  For an example of setting up a database mirroring session using Windows Authentication, see [Example: Setting Up Database Mirroring Using Windows Authentication &#40;Transact-SQL&#41;](../Topic/Example:%20Setting%20Up%20Database%20Mirroring%20Using%20Windows%20Authentication%20\(Transact-SQL\).md).  
  
### Certificates  
 In some situations, such as when server instances are not in trusted domains or when [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is running as a local service, Windows Authentication is unavailable. In such cases, instead of user credentials, certificates are required to authenticate connection requests. The mirroring endpoint of each server instance must be configured with its own locally created certificate.  
  
 The encryption method is established when the certificate is created. For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](../Topic/Allow%20a%20Database%20Mirroring%20Endpoint%20to%20Use%20Certificates%20for%20Outbound%20Connections%20\(Transact-SQL\).md). Carefully manage the certificates that you use.  
  
 A server instance uses the private key of its own certificate to establish its identity when setting up a connection. The server instance that receives the connection request uses the public key of the sender's certificate to authenticate the sender's identity. For example, consider two server instances, Server\_A and Server\_B. Server\_A uses its private key to encrypt the connection header before sending a connection request to Server\_B. Server\_B uses the public key of Server\_A's certificate to decrypt the connection header. If the decrypted header is correct, Server\_B knows that the header was encrypted by Server\_A, and the connection is authenticated. If the decrypted header is incorrect, Server\_B knows that the connection request is inauthentic and refuses the connection.  
  
##  <a name="DataEncryption"></a> Data Encryption  
 By default, a database mirroring endpoint requires encryption of data sent over mirroring connections. In this case, the endpoint can connect only to endpoints that also use encryption. Unless you can guarantee that your network is secure, we recommend that you require encryption for your database mirroring connections. However, you can disable encryption or make it supported, but not required. If encryption is disabled, data is never encrypted and the endpoint cannot connect to an endpoint that requires encryption. If encryption is supported, data is encrypted only if the opposite endpoint either supports or requires encryption.  
  
> [!NOTE]  
>  Mirroring endpoints created by [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] are created with encryption either required or disabled. To change the encryption setting to SUPPORTED, use the ALTER ENDPOINT [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement. For more information, see [ALTER ENDPOINT &#40;Transact-SQL&#41;](../Topic/ALTER%20ENDPOINT%20\(Transact-SQL\).md).  
  
 Optionally, you can control the encryption algorithms that can be used by an endpoint, by specifying one of the following values for the ALGORITHM option in a CREATE ENDPOINT statement or ALTER ENDPOINT statement:  
  
|ALGORITHM value|Description|  
|---------------------|-----------------|  
|RC4|Specifies that the endpoint must use the RC4 algorithm. This is the default.<br /><br /> **\*\* Warning \*\*** The RC4 algorithm is deprecated. [!INCLUDE[ssNoteDepFutureDontUse](../../Token\Appliesto/ssNoteDepFutureDontUse_md.md)] We recommend that you use AES.|  
|AES|Specifies that the endpoint must use the AES algorithm.|  
|AES RC4|Specifies that the two endpoints will negotiate for an encryption algorithm with this endpoint giving preference to the AES algorithm.|  
|RC4 AES|Specifies that the two endpoints will negotiate for an encryption algorithm with this endpoint giving preference to the RC4 algorithm.|  
  
 If connecting endpoints specify both algorithms but in different orders, the endpoint accepting the connection wins.  
  
> [!NOTE]  
>  The RC4 algorithm is only supported for backward compatibility. New material can only be encrypted using RC4 or RC4\_128 when the database is in compatibility level 90 or 100. \(Not recommended.\) Use a newer algorithm such as one of the AES algorithms instead. In [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)]and higher versions,  material encrypted using RC4 or RC4\_128 can be decrypted in any compatibility level.  
>   
>  Though considerably faster than AES, RC4 is a relatively weak algorithm, while AES is a relatively strong algorithm. Therefore, we recommend that you use the AES algorithm.  
  
 For information about the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] syntax for specifying encryption, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](../Topic/CREATE%20ENDPOINT%20\(Transact-SQL\).md).  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To configure transport security for a database mirroring endpoint**  
  
-   [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](../Topic/Create%20a%20Database%20Mirroring%20Endpoint%20for%20Windows%20Authentication%20\(Transact-SQL\).md)  
  
-   [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](../Topic/Establish%20a%20Database%20Mirroring%20Session%20Using%20Windows%20Authentication%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](../Topic/Create%20a%20Database%20Mirroring%20Endpoint%20for%20Windows%20Authentication%20\(Transact-SQL\).md)  
  
-   [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](../Topic/Allow%20a%20Database%20Mirroring%20Endpoint%20to%20Use%20Certificates%20for%20Outbound%20Connections%20\(Transact-SQL\).md)  
  
## See Also  
 [Choose an Encryption Algorithm](../../Topics\TopicNameNotContainA/Choose-an-Encryption-Algorithm.md)   
 [ALTER ENDPOINT &#40;Transact-SQL&#41;](../Topic/ALTER%20ENDPOINT%20\(Transact-SQL\).md)   
 [DROP ENDPOINT &#40;Transact-SQL&#41;](../Topic/DROP%20ENDPOINT%20\(Transact-SQL\).md)   
 [Security Center for SQL Server Database Engine and Azure SQL Database](../../Topics\TopicNameNotContainA/Security-Center-for-SQL-Server-Database-Engine-and-Azure-SQL-Database.md)   
 [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../Topic/Manage%20Metadata%20When%20Making%20a%20Database%20Available%20on%20Another%20Server%20Instance%20\(SQL%20Server\).md)   
 [The Database Mirroring Endpoint &#40;SQL Server&#41;](../Topic/The%20Database%20Mirroring%20Endpoint%20\(SQL%20Server\).md)   
 [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](../Topic/sys.database_mirroring_endpoints%20\(Transact-SQL\).md)   
 [sys.dm_db_mirroring_connections &#40;Transact-SQL&#41;](../Topic/sys.dm_db_mirroring_connections%20\(Transact-SQL\).md)   
 [Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;](../Topic/Troubleshoot%20Database%20Mirroring%20Configuration%20\(SQL%20Server\).md)   
 [Troubleshoot Always On Availability Groups Configuration &#40;SQL Server&#41;](../Topic/Troubleshoot%20Always%20On%20Availability%20Groups%20Configuration%20\(SQL%20Server\).md)  
  
  