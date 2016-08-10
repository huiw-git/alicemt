---
title: "Service Master Key"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 85f2095d-2590-4f59-8a29-7e100edd02bb
caps.latest.revision: 19
caps.handback.revision: 0
manager: jhubbard
---
# Service Master Key
The Service Master Key is the root of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] encryption hierarchy. It is generated automatically the first time it is needed to encrypt another key. By default, the Service Master Key is encrypted using the Windows data protection API and using the local machine key. The Service Master Key can only be opened by the Windows service account under which it was created or by a principal with access to both the service account name and its password.  
  
 Regenerating or restoring the Service Master Key involves decrypting and re-encrypting the complete encryption hierarchy. Unless the key has been compromised, this resource-intensive operation should be scheduled during a period of low demand.  
  
 [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] uses the AES encryption algorithm to protect the service master key (SMK) and the database master key (DMK). AES is a newer encryption algorithm than 3DES used in earlier versions. After upgrading an instance of the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] to [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] the SMK and DMK should be regenerated in order to upgrade the master keys to AES. For more information about regenerating the SMK, see [ALTER SERVICE MASTER KEY (Transact-SQL)](assetId:///a1e9be0e-4115-47d8-9d3a-3316d876a35e) and [ALTER MASTER KEY (Transact-SQL)](assetId:///8ac501c3-4280-4d5b-b58a-1524fa715b50).  
  
## Best Practice  
 Back up the Service Master Key and store the backed up copy in a secure, off-site location.  
  
## Related Tasks  
 [BACKUP SERVICE MASTER KEY (Transact-SQL)](assetId:///f8356683-6680-4f1c-9eaf-5c29a9a9020d)  
  
 [RESTORE SERVICE MASTER KEY (Transact-SQL)](assetId:///a68fd0ee-70ce-4104-aca0-fcae5f41fc38)  
  
 [ALTER SERVICE MASTER KEY (Transact-SQL)](assetId:///a1e9be0e-4115-47d8-9d3a-3316d876a35e)  
  
## See Also  
 [Encryption Hierarchy](../../Topics/TopicNameNotContainA/Encryption-Hierarchy.md)