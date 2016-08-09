---
title: "Set Up an Encrypted Mirror Database"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7329a575-be29-46e0-abc6-1344db37920c
caps.latest.revision: 25
caps.handback.revision: 0
manager: jhubbard
---
# Set Up an Encrypted Mirror Database
To enable automatic decryption of the database master key of a mirror database, you must provide the password used to encrypt the master key to the mirror server instance. [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)] and later versions include mechanisms to transfer the password. Use **sp_control_dbmasterkey_password** to create a credential for the database master key before you start database mirroring. You must repeat this process for every database that will be mirrored. For more information, see [sp_control_dbmasterkey_password (Transact-SQL)](assetId:///63979a87-42a2-446e-8e43-30481faaf3ca).  
  
> [!CAUTION]  
>  Do not enable failover decryption of a database that must remain inaccessible to **sa** and other highly privileged server principals. You can configure a database so that its key hierarchy cannot be decrypted by the service master key. This option is supported as a defense-in-depth for databases that contain information that should not be accessible to **sa** or other highly privileged server principals. Enabling failover decryption of such a database removes this defense-in-depth, enabling **sa** and other highly privileged server principals to decrypt the database.  
  
## See Also  
 [sp_control_dbmasterkey_password (Transact-SQL)](assetId:///63979a87-42a2-446e-8e43-30481faaf3ca)   
 [CREATE MASTER KEY (Transact-SQL)](assetId:///1710a305-1a4f-48ec-836c-11ffd0356d76)   
 [ALTER MASTER KEY (Transact-SQL)](assetId:///8ac501c3-4280-4d5b-b58a-1524fa715b50)   
 [Encryption Hierarchy](../../Topics/TopicNameNotContainA/Encryption-Hierarchy.md)   
 [Setting Up Database Mirroring (SQL Server)](../../Topics/TopicNameNotContainA/Setting-Up-Database-Mirroring--SQL-Server-.md)