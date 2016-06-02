---
title: SQL Server Certificates and Asymmetric Keys
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8519aa2f-f09c-4c1c-96b5-abc24811e60c
---
# SQL Server Certificates and Asymmetric Keys
  Public Key Cryptography \(PKI\) is a form of message secrecy in which a user creates a *public* key and a *private* key. The private key is kept secret, whereas the public key can be distributed to others. Although the keys are mathematically related, the private key cannot be easily derived by using the public key. The public key is used to encrypt data and the private key is used to decrypt data. A message that is encrypted by using the public key can only be decrypted by using the correct private key. Since there are two different keys, these keys are *asymmetric*.  
  
 Certificates and asymmetric keys are both ways to use asymmetric encryption. Certificates are often used as containers for asymmetric keys because they can contain more information such as expiry dates and issuers. There is no difference between the two mechanisms for the cryptographic algorithm, and no difference in strength given the same key length. Generally, you use a certificate to encrypt other types of encryption keys in a database, or to sign code modules.  
  
 Certificates and asymmetric keys can decrypt data that the other encrypts. Generally, you use asymmetric encryption to encrypt a symmetric key for storage in a database.  
  
 A public key does not have a particular format like a certificate would have, and you cannot export it to a file.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] contains features that enable you to create and manage certificates and keys for use with the server and database. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] cannot be used to create and manage certificates and keys with other applications or in the operating system.  
  
## Certificates  
 A certificate is a digitally signed security object that contains a public \(and optionally a private\) key for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. You can use externally generated certificates or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] can generate certificates.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] certificates comply with the IETF X.509v3 certificate standard.  
  
 Certificates are useful because of the option of both exporting and importing keys to X.509 certificate files. The syntax for creating certificates allows for creation options for certificates such as an expiry date.  
  
### Using a Certificate in SQL Server  
 Certificates can be used to help secure connections, in database mirroring, to sign packages and other objects, or to encrypt data or connections. The following table lists additional resources for certificates in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
|Topic|Description|  
|-----------|-----------------|  
|[CREATE CERTIFICATE &#40;Transact-SQL&#41;](../Topic/CREATE%20CERTIFICATE%20\(Transact-SQL\).md)|Explains the command for creating certificates.|  
|[Identify the Source of Packages with Digital Signatures](../../Topics\TopicNameNotContainA/Identify-the-Source-of-Packages-with-Digital-Signatures.md)|Shows information about how to use certificates to sign software packages.|  
|[Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](../Topic/Use%20Certificates%20for%20a%20Database%20Mirroring%20Endpoint%20\(Transact-SQL\).md)|Covers information about how to use certificates with Database Mirroring.|  
  
## Asymmetric Keys  
 Asymmetric keys are used for securing symmetric keys. They can also be used for limited data encryption and to digitally sign database objects. An asymmetric key consists of a private key and a corresponding public key. For more information about asymmetric keys, see [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../Topic/CREATE%20ASYMMETRIC%20KEY%20\(Transact-SQL\).md).  
  
 Asymmetric keys can be imported from strong name key files, but they cannot be exported. They also do not have expiry options. Asymmetric keys cannot encrypt connections.  
  
### Using an Asymmetric Key in SQL Server  
 Asymmetric keys can be used to help secure data or sign plaintext. The following table lists additional resources for asymmetric keys in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
|Topic|Description|  
|-----------|-----------------|  
|[CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../Topic/CREATE%20ASYMMETRIC%20KEY%20\(Transact-SQL\).md)|Explains the command for creating asymmetric keys.|  
|[SIGNBYASYMKEY &#40;Transact-SQL&#41;](../Topic/SIGNBYASYMKEY%20\(Transact-SQL\).md)|Displays the options for signing objects.|  
  
## Tools  
 [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] provides tools and utilities that will generate certificates and strong name key files. These tools offer a richer amount of flexibility in the key generation process than the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] syntax. You can use these tools to create RSA keys with more complex key lengths and then import them into [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. The following table explains shows where to find these tools.  
  
|||  
|-|-|  
|Tool|Purpose|  
|[makecert](http://msdn2.microsoft.com/library/bfsktky3\(VS.80\).aspx)|Creates certificates.|  
|[sn](http://msdn2.microsoft.com/library/k5b5tt23\(VS.80\).aspx)|Creates strong names for symmetric keys.|  
  
## Related Tasks  
 [Choose an Encryption Algorithm](../../Topics\TopicNameNotContainA/Choose-an-Encryption-Algorithm.md)  
  
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../Topic/CREATE%20SYMMETRIC%20KEY%20\(Transact-SQL\).md)  
  
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../Topic/CREATE%20CERTIFICATE%20\(Transact-SQL\).md)  
  
## See Also  
 [sys.certificates &#40;Transact-SQL&#41;](../Topic/sys.certificates%20\(Transact-SQL\).md)   
 [Transparent Data Encryption &#40;TDE&#41;](../Topic/Transparent%20Data%20Encryption%20\(TDE\).md)  
  
  