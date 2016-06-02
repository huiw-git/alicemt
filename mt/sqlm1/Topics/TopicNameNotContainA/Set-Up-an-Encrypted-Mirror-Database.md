---
title: Set Up an Encrypted Mirror Database
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7329a575-be29-46e0-abc6-1344db37920c
---
# Set Up an Encrypted Mirror Database
  To enable automatic decryption of the database master key of a mirror database, you must provide the password used to encrypt the master key to the mirror server instance. [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] and later versions include mechanisms to transfer the password. Use **sp\_control\_dbmasterkey\_password** to create a credential for the database master key before you start database mirroring. You must repeat this process for every database that will be mirrored. For more information, see [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](../Topic/sp_control_dbmasterkey_password%20\(Transact-SQL\).md).  
  
> [!CAUTION]  
>  Do not enable failover decryption of a database that must remain inaccessible to **sa** and other highly privileged server principals. You can configure a database so that its key hierarchy cannot be decrypted by the service master key. This option is supported as a defense\-in\-depth for databases that contain information that should not be accessible to **sa** or other highly privileged server principals. Enabling failover decryption of such a database removes this defense\-in\-depth, enabling **sa** and other highly privileged server principals to decrypt the database.  
  
## See Also  
 [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](../Topic/sp_control_dbmasterkey_password%20\(Transact-SQL\).md)   
 [CREATE MASTER KEY &#40;Transact-SQL&#41;](../Topic/CREATE%20MASTER%20KEY%20\(Transact-SQL\).md)   
 [ALTER MASTER KEY &#40;Transact-SQL&#41;](../Topic/ALTER%20MASTER%20KEY%20\(Transact-SQL\).md)   
 [Encryption Hierarchy](../../Topics\TopicNameNotContainA/Encryption-Hierarchy.md)   
 [Setting Up Database Mirroring &#40;SQL Server&#41;](../Topic/Setting%20Up%20Database%20Mirroring%20\(SQL%20Server\).md)  
  
  