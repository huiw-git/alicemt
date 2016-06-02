---
title: Extensible Key Management (EKM)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9bfaf500-2d1e-4c02-b041-b8761a9e695b
---
# Extensible Key Management (EKM)
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provides data encryption capabilities together with *Extensible Key Management* \(EKM\), using the *Microsoft Cryptographic API* \(MSCAPI\) provider for encryption and key generation. Encryption keys for data and key encryption are created in transient key containers, and they must be exported from a provider before they are stored in the database. This approach enables key management that includes an encryption key hierarchy and key backup, to be handled by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
 With the growing demand for regulatory compliance and concern for data privacy, organizations are taking advantage of encryption as a way to provide a "defense in depth" solution. This approach is often impractical using only database encryption management tools. Hardware vendors provide products that address enterprise key management by using *Hardware Security Modules* \(HSM\). HSM devices store encryption keys on hardware or software modules. This is a more secure solution because the encryption keys do not reside with encryption data.  
  
 A number of vendors offer HSM for both key management and encryption acceleration. HSM devices use hardware interfaces with a server process as an intermediary between an application and an HSM. Vendors also implement MSCAPI providers over their modules, which might be hardware or software. MSCAPI often offers only a subset of the functionality that is offered by an HSM. Vendors can also provide management software for HSM, key configuration, and key access.  
  
 HSM implementations vary from vendor to vendor, and to use them with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] requires a common interface. Although the MSCAPI provides this interface, it supports only a subset of the HSM features. It also has other limitations, such as the inability to natively persist symmetric keys, and a lack of session\-oriented support.  
  
 The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Extensible Key Management enables third\-party EKM\/HSM vendors to register their modules in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. When registered, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] users can use the encryption keys stored on EKM modules. This enables [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to access the advanced encryption features these modules support such as bulk encryption and decryption, and key management functions such as key aging and key rotation.  
  
 When running [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in an Azure VM, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] can use keys stored in the [Azure Key Vault](http://go.microsoft.com/fwlink/?LinkId=521401). For more information, see [Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;](../Topic/Extensible%20Key%20Management%20Using%20Azure%20Key%20Vault%20\(SQL%20Server\).md).  
  
## EKM Configuration  
 Extensible Key Management is not available in every edition of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md).  
  
 By default, Extensible Key Management is off. To enable this feature, use the sp\_configure command that has the following option and value, as in the following example:  
  
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
>  If you use the sp\_configure command for this option on editions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that do not support EKM, you will receive an error.  
  
 To disable the feature, set the value to **0**. For more information about how to set server options, see [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md).  
  
## How to Use EKM  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Extensible Key Management enables the encryption keys that protect the database files to be stored in an off\-box device such as a smartcard, USB device, or EKM\/HSM module. This also enables data protection from database administrators \(except members of the sysadmin group\). Data can be encrypted by using encryption keys that only the database user has access to on the external EKM\/HSM module.  
  
 Extensible Key Management also provides the following benefits:  
  
-   Additional authorization check \(enabling separation of duties\).  
  
-   Higher performance for hardware\-based encryption\/decryption.  
  
-   External encryption key generation.  
  
-   External encryption key storage \(physical separation of data and keys\).  
  
-   Encryption key retrieval.  
  
-   External encryption key retention \(enables encryption key rotation\).  
  
-   Easier encryption key recovery.  
  
-   Manageable encryption key distribution.  
  
-   Secure encryption key disposal.  
  
 You can use Extensible Key Management for a username and password combination or other methods defined by the EKM driver.  
  
> [!CAUTION]  
>  For troubleshooting, [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] technical support might require the encryption key from the EKM provider. You might also need to access vendor tools or processes to help resolve an issue.  
  
### Authentication with an EKM Device  
 An EKM module can support more than one type of authentication. Each provider exposes only one type of authentication to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], that is if the module supports Basic or Other authentication types, it exposes one or the other, but not both.  
  
#### EKM Device\-Specific Basic Authentication Using username\/password  
 For those EKM modules that support Basic authentication using a *username\/password* pair, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provides transparent authentication using credentials. For more information about credentials, see [Credentials &#40;Database Engine&#41;](../Topic/Credentials%20\(Database%20Engine\).md).  
  
 A credential can be created for an EKM provider and mapped to a login \(both Windows and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] accounts\) to access an EKM module on per\-login basis. The *Identify* field of the credential contains the username; the *secret* field contains a password to connect to an EKM module.  
  
 If there is no login mapped credential for the EKM provider, the credential mapped to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service account is used.  
  
 A login can have multiple credentials mapped to it, as long as they are used for distinctive EKM providers. There must be only one mapped credential per EKM provider per login. The same credential can be mapped to other logins.  
  
#### Other Types of EKM Device\-Specific Authentication  
 For EKM modules that have authentication other than Windows or *user\/password* combinations, authentication must be performed independently from [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
### Encryption and Decryption by an EKM Device  
 You can use the following functions and features to encrypt and decrypt data by using symmetric and asymmetric keys:  
  
|Function or feature|Reference|  
|-------------------------|---------------|  
|Symmetric key encryption|[CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../Topic/CREATE%20SYMMETRIC%20KEY%20\(Transact-SQL\).md)|  
|Asymmetric Key encryption|[CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../Topic/CREATE%20ASYMMETRIC%20KEY%20\(Transact-SQL\).md)|  
|EncryptByKey\(key\_guid, 'cleartext', …\)|[ENCRYPTBYKEY &#40;Transact-SQL&#41;](../Topic/ENCRYPTBYKEY%20\(Transact-SQL\).md)|  
|DecryptByKey\(ciphertext, …\)|[DECRYPTBYKEY &#40;Transact-SQL&#41;](../Topic/DECRYPTBYKEY%20\(Transact-SQL\).md)|  
|EncryptByAsmKey\(key\_guid, 'cleartext'\)|[ENCRYPTBYASYMKEY &#40;Transact-SQL&#41;](../Topic/ENCRYPTBYASYMKEY%20\(Transact-SQL\).md)|  
|DecryptByAsmKey\(ciphertext\)|[DECRYPTBYASYMKEY &#40;Transact-SQL&#41;](../Topic/DECRYPTBYASYMKEY%20\(Transact-SQL\).md)|  
  
#### Database Keys Encryption by EKM Keys  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] can use EKM keys to encrypt other keys in a database. You can create and use both symmetric and asymmetric keys on an EKM device. You can encrypt native \(non\-EKM\) symmetric keys with EKM asymmetric keys.  
  
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
  
 For more information about Database and Server Keys in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see [SQL Server and Database Encryption Keys &#40;Database Engine&#41;](../Topic/SQL%20Server%20and%20Database%20Encryption%20Keys%20\(Database%20Engine\).md).  
  
> [!NOTE]  
>  You cannot encrypt one EKM key with another EKM key.  
>   
>  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] does not support signing modules with asymmetric keys generated from EKM provider.  
  
## Related Tasks  
 [EKM provider enabled Server Configuration Option](../../Topics\TopicNameNotContainA/EKM-provider-enabled-Server-Configuration-Option.md)  
  
 [Enable TDE on SQL Server Using EKM](../../Topics\TopicNameNotContainA/Enable-TDE-on-SQL-Server-Using-EKM.md)  
  
 [Extensible Key Management Using Azure Key Vault &#40;SQL Server&#41;](../Topic/Extensible%20Key%20Management%20Using%20Azure%20Key%20Vault%20\(SQL%20Server\).md)  
  
## See Also  
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../Topic/CREATE%20CRYPTOGRAPHIC%20PROVIDER%20\(Transact-SQL\).md)   
 [DROP CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../Topic/DROP%20CRYPTOGRAPHIC%20PROVIDER%20\(Transact-SQL\).md)   
 [ALTER CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../Topic/ALTER%20CRYPTOGRAPHIC%20PROVIDER%20\(Transact-SQL\).md)   
 [sys.cryptographic_providers &#40;Transact-SQL&#41;](../Topic/sys.cryptographic_providers%20\(Transact-SQL\).md)   
 [sys.dm_cryptographic_provider_sessions &#40;Transact-SQL&#41;](../Topic/sys.dm_cryptographic_provider_sessions%20\(Transact-SQL\).md)   
 [sys.dm_cryptographic_provider_properties &#40;Transact-SQL&#41;](../Topic/sys.dm_cryptographic_provider_properties%20\(Transact-SQL\).md)   
 [sys.dm_cryptographic_provider_algorithms &#40;Transact-SQL&#41;](../Topic/sys.dm_cryptographic_provider_algorithms%20\(Transact-SQL\).md)   
 [sys.dm_cryptographic_provider_keys &#40;Transact-SQL&#41;](../Topic/sys.dm_cryptographic_provider_keys%20\(Transact-SQL\).md)   
 [sys.credentials &#40;Transact-SQL&#41;](../Topic/sys.credentials%20\(Transact-SQL\).md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../Topic/CREATE%20CREDENTIAL%20\(Transact-SQL\).md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../Topic/ALTER%20LOGIN%20\(Transact-SQL\).md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../Topic/CREATE%20ASYMMETRIC%20KEY%20\(Transact-SQL\).md)   
 [ALTER ASYMMETRIC KEY &#40;Transact-SQL&#41;](../Topic/ALTER%20ASYMMETRIC%20KEY%20\(Transact-SQL\).md)   
 [DROP ASYMMETRIC KEY &#40;Transact-SQL&#41;](../Topic/DROP%20ASYMMETRIC%20KEY%20\(Transact-SQL\).md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../Topic/CREATE%20SYMMETRIC%20KEY%20\(Transact-SQL\).md)   
 [ALTER SYMMETRIC KEY &#40;Transact-SQL&#41;](../Topic/ALTER%20SYMMETRIC%20KEY%20\(Transact-SQL\).md)   
 [DROP SYMMETRIC KEY &#40;Transact-SQL&#41;](../Topic/DROP%20SYMMETRIC%20KEY%20\(Transact-SQL\).md)   
 [OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](../Topic/OPEN%20SYMMETRIC%20KEY%20\(Transact-SQL\).md)   
 [Back Up and Restore Reporting Services Encryption Keys](../../Topics\TopicNameNotContainA/Back-Up-and-Restore-Reporting-Services-Encryption-Keys.md)   
 [Delete and Re-create Encryption Keys  &#40;SSRS Configuration Manager&#41;](../Topic/Delete%20and%20Re-create%20Encryption%20Keys%20%20\(SSRS%20Configuration%20Manager\).md)   
 [Add and Remove Encryption Keys for Scale-Out Deployment &#40;SSRS Configuration Manager&#41;](../Topic/Add%20and%20Remove%20Encryption%20Keys%20for%20Scale-Out%20Deployment%20\(SSRS%20Configuration%20Manager\).md)   
 [Back Up the Service Master Key](../../Topics\TopicNameNotContainA/Back-Up-the-Service-Master-Key.md)   
 [Restore the Service Master Key](../../Topics\TopicNameNotContainA/Restore-the-Service-Master-Key.md)   
 [Create a Database Master Key](../../Topics\TopicNameContainA/Create-a-Database-Master-Key.md)   
 [Back Up a Database Master Key](../../Topics\TopicNameContainA/Back-Up-a-Database-Master-Key.md)   
 [Restore a Database Master Key](../../Topics\TopicNameContainA/Restore-a-Database-Master-Key.md)   
 [Create Identical Symmetric Keys on Two Servers](../../Topics\TopicNameNotContainA/Create-Identical-Symmetric-Keys-on-Two-Servers.md)  
  
  