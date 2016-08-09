---
title: "Extensible Key Management (EKM)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9bfaf500-2d1e-4c02-b041-b8761a9e695b
caps.latest.revision: 47
caps.handback.revision: 0
manager: jhubbard
---
# Extensible Key Management (EKM)
[!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] provides data encryption capabilities together with *Extensible Key Management* (EKM), using the *Microsoft Cryptographic API* (MSCAPI) provider for encryption and key generation. Encryption keys for data and key encryption are created in transient key containers, and they must be exported from a provider before they are stored in the database. This approach enables key management that includes an encryption key hierarchy and key backup, to be handled by [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
 With the growing demand for regulatory compliance and concern for data privacy, organizations are taking advantage of encryption as a way to provide a "defense in depth" solution. This approach is often impractical using only database encryption management tools. Hardware vendors provide products that address enterprise key management by using *Hardware Security Modules* (HSM). HSM devices store encryption keys on hardware or software modules. This is a more secure solution because the encryption keys do not reside with encryption data.  
  
 A number of vendors offer HSM for both key management and encryption acceleration. HSM devices use hardware interfaces with a server process as an intermediary between an application and an HSM. Vendors also implement MSCAPI providers over their modules, which might be hardware or software. MSCAPI often offers only a subset of the functionality that is offered by an HSM. Vendors can also provide management software for HSM, key configuration, and key access.  
  
 HSM implementations vary from vendor to vendor, and to use them with [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] requires a common interface. Although the MSCAPI provides this interface, it supports only a subset of the HSM features. It also has other limitations, such as the inability to natively persist symmetric keys, and a lack of session-oriented support.  
  
 The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Extensible Key Management enables third-party EKM/HSM vendors to register their modules in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. When registered, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] users can use the encryption keys stored on EKM modules. This enables [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] to access the advanced encryption features these modules support such as bulk encryption and decryption, and key management functions such as key aging and key rotation.  
  
 When running [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] in an Azure VM, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] can use keys stored in the [Azure Key Vault](http://go.microsoft.com/fwlink/?LinkId=521401). For more information, see [Extensible Key Management Using Azure Key Vault (SQL Server)](../../Topics/TopicNameNotContainA/Extensible-Key-Management-Using-Azure-Key-Vault--SQL-Server-.md).  
  
## EKM Configuration  
 Extensible Key Management is not available in every edition of [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], see [Features Supported by the Editions of SQL Server 2016](../../Topics/TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md).  
  
 By default, Extensible Key Management is off. To enable this feature, use the sp_configure command that has the following option and value, as in the following example:  
  
```  
sp_configure 'show advanced', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'EKM provider enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
> [!NOTE]  
>  If you use the sp_configure command for this option on editions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] that do not support EKM, you will receive an error.  
  
 To disable the feature, set the value to **0**. For more information about how to set server options, see [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8).  
  
## How to Use EKM  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Extensible Key Management enables the encryption keys that protect the database files to be stored in an off-box device such as a smartcard, USB device, or EKM/HSM module. This also enables data protection from database administrators (except members of the sysadmin group). Data can be encrypted by using encryption keys that only the database user has access to on the external EKM/HSM module.  
  
 Extensible Key Management also provides the following benefits:  
  
-   Additional authorization check (enabling separation of duties).  
  
-   Higher performance for hardware-based encryption/decryption.  
  
-   External encryption key generation.  
  
-   External encryption key storage (physical separation of data and keys).  
  
-   Encryption key retrieval.  
  
-   External encryption key retention (enables encryption key rotation).  
  
-   Easier encryption key recovery.  
  
-   Manageable encryption key distribution.  
  
-   Secure encryption key disposal.  
  
 You can use Extensible Key Management for a username and password combination or other methods defined by the EKM driver.  
  
> [!CAUTION]  
>  For troubleshooting, [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] technical support might require the encryption key from the EKM provider. You might also need to access vendor tools or processes to help resolve an issue.  
  
### Authentication with an EKM Device  
 An EKM module can support more than one type of authentication. Each provider exposes only one type of authentication to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], that is if the module supports Basic or Other authentication types, it exposes one or the other, but not both.  
  
#### EKM Device-Specific Basic Authentication Using username/password  
 For those EKM modules that support Basic authentication using a *username/password* pair, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] provides transparent authentication using credentials. For more information about credentials, see [Credentials (Database Engine)](../../Topics/TopicNameNotContainA/Credentials--Database-Engine-.md).  
  
 A credential can be created for an EKM provider and mapped to a login (both Windows and [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] accounts) to access an EKM module on per-login basis. The *Identify* field of the credential contains the username; the *secret* field contains a password to connect to an EKM module.  
  
 If there is no login mapped credential for the EKM provider, the credential mapped to the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] service account is used.  
  
 A login can have multiple credentials mapped to it, as long as they are used for distinctive EKM providers. There must be only one mapped credential per EKM provider per login. The same credential can be mapped to other logins.  
  
#### Other Types of EKM Device-Specific Authentication  
 For EKM modules that have authentication other than Windows or *user/password* combinations, authentication must be performed independently from [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
### Encryption and Decryption by an EKM Device  
 You can use the following functions and features to encrypt and decrypt data by using symmetric and asymmetric keys:  
  
|Function or feature|Reference|  
|-------------------------|---------------|  
|Symmetric key encryption|[CREATE SYMMETRIC KEY (Transact-SQL)](assetId:///b5d23572-b79d-4cf1-9eef-d648fa3b1358)|  
|Asymmetric Key encryption|[CREATE ASYMMETRIC KEY (Transact-SQL)](assetId:///141bc976-7631-49f6-82bd-a235028645b1)|  
|EncryptByKey(key_guid, 'cleartext', …)|[EncryptByKey (Transact-SQL)](assetId:///0e11f8c5-f79d-46c1-ab11-b68ef05d6787)|  
|DecryptByKey(ciphertext, …)|[DecryptByKey (Transact-SQL)](assetId:///6edf121f-ac62-4dae-90e6-6938f32603c9)|  
|EncryptByAsmKey(key_guid, 'cleartext')|[EncryptByAsymKey (Transact-SQL)](assetId:///86bb2588-ab13-4db2-8f3c-42c9f572a67b)|  
|DecryptByAsmKey(ciphertext)|[DecryptByAsymKey (Transact-SQL)](assetId:///d9ebcd30-f01c-4cfe-b95e-ffe6ea13788b)|  
  
#### Database Keys Encryption by EKM Keys  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] can use EKM keys to encrypt other keys in a database. You can create and use both symmetric and asymmetric keys on an EKM device. You can encrypt native (non-EKM) symmetric keys with EKM asymmetric keys.  
  
 The following example creates a database symmetric key and encrypts it using a key on an EKM module.  
  
```  
CREATE SYMMETRIC KEY Key1  
WITH ALGORITHM = AES_256  
ENCRYPTION BY EKM_AKey1;  
GO  
--Open database key  
OPEN SYMMETRIC KEY Key1  
DECRYPTION BY EKM_AKey1  
```  
  
 For more information about Database and Server Keys in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], see [SQL Server and Database Encryption Keys (Database Engine)](../../Topics/TopicNameNotContainA/SQL-Server-and-Database-Encryption-Keys--Database-Engine-.md).  
  
> [!NOTE]  
>  You cannot encrypt one EKM key with another EKM key.  
>   
>  [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] does not support signing modules with asymmetric keys generated from EKM provider.  
  
## Related Tasks  
 [EKM provider enabled Server Configuration Option](../../Topics/TopicNameNotContainA/EKM-provider-enabled-Server-Configuration-Option.md)  
  
 [Enable TDE on SQL Server Using EKM](../../Topics/TopicNameNotContainA/Enable-TDE-on-SQL-Server-Using-EKM.md)  
  
 [Extensible Key Management Using Azure Key Vault (SQL Server)](../../Topics/TopicNameNotContainA/Extensible-Key-Management-Using-Azure-Key-Vault--SQL-Server-.md)  
  
## See Also  
 [CREATE CRYPTOGRAPHIC PROVIDER (Transact-SQL)](assetId:///059a39a6-9d32-4d3f-965b-0a1ce75229c7)   
 [DROP CRYPTOGRAPHIC PROVIDER (Transact-SQL)](assetId:///71c55c20-439e-4897-aef5-f20e556d668f)   
 [ALTER CRYPTOGRAPHIC PROVIDER (Transact-SQL)](assetId:///876b6348-fb29-49e1-befc-4217979f6416)   
 [sys.cryptographic_providers (Transact-SQL)](assetId:///9da0da95-792e-48b4-9f60-47f0729c279c)   
 [sys.dm_cryptographic_provider_sessions](assetId:///9a4de02b-1a07-4850-979a-0861fddb7f9d)   
 [sys.dm_provider_properties](assetId:///024b0095-6766-4189-a39a-d316c5ec2874)   
 [sys.fn_provider_algorithms (Transact-SQL)](assetId:///8bcccb37-5cfb-4e1e-a0bb-7ff4c279fe8e)   
 [sys.fn_cryptographic_provider_keys (Transact-SQL)](assetId:///5a8c1421-c56b-44b5-96e5-4f01782a0c7c)   
 [sys.credentials (Transact-SQL)](assetId:///ea48cf80-904a-4273-a950-6d35b1b0a1b6)   
 [CREATE CREDENTIAL (Transact-SQL)](assetId:///d5e9ae69-41d9-4e46-b13d-404b88a32d9d)   
 [ALTER LOGIN (Transact-SQL)](assetId:///e247b84e-c99e-4af8-8b50-57586e1cb1c5)   
 [CREATE ASYMMETRIC KEY (Transact-SQL)](assetId:///141bc976-7631-49f6-82bd-a235028645b1)   
 [ALTER ASYMMETRIC KEY (Transact-SQL)](assetId:///958e95d6-fbe6-43e8-abbd-ccedbac2dbac)   
 [DROP ASYMMETRIC KEY (Transact-SQL)](assetId:///bf94ac07-9b62-4318-b55b-1eed8f3a1ac6)   
 [CREATE SYMMETRIC KEY (Transact-SQL)](assetId:///b5d23572-b79d-4cf1-9eef-d648fa3b1358)   
 [ALTER SYMMETRIC KEY (Transact-SQL)](assetId:///d3c776a4-7d71-4e6f-84fc-1db47400c465)   
 [DROP SYMMETRIC KEY (Transact-SQL)](assetId:///6150bc67-08cb-402e-9c24-b04c9654b434)   
 [OPEN SYMMETRIC KEY (Transact-SQL)](assetId:///ff019a7c-c373-46c7-ac43-ffb7e2ee60b3)   
 [Back Up and Restore Reporting Services Encryption Keys](../../Topics/TopicNameNotContainA/Back-Up-and-Restore-Reporting-Services-Encryption-Keys.md)   
 [Delete and Re-create Encryption Keys  (SSRS Configuration Manager)](../../Topics/TopicNameNotContainA/Delete-and-Re-create-Encryption-Keys---SSRS-Configuration-Manager-.md)   
 [Add and Remove Encryption Keys for Scale-Out Deployment (SSRS Configuration Manager)](../../Topics/TopicNameNotContainA/Add-and-Remove-Encryption-Keys-for-Scale-Out-Deployment--SSRS-Configuration-Manager-.md)   
 [Back Up the Service Master Key](../../Topics/TopicNameNotContainA/Back-Up-the-Service-Master-Key.md)   
 [Restore the Service Master Key](../../Topics/TopicNameNotContainA/Restore-the-Service-Master-Key.md)   
 [Create a Database Master Key](../../Topics/TopicNameContainA/Create-a-Database-Master-Key.md)   
 [Back Up a Database Master Key](../../Topics/TopicNameContainA/Back-Up-a-Database-Master-Key.md)   
 [Restore a Database Master Key](../../Topics/TopicNameContainA/Restore-a-Database-Master-Key.md)   
 [Create Identical Symmetric Keys on Two Servers](../../Topics/TopicNameNotContainA/Create-Identical-Symmetric-Keys-on-Two-Servers.md)