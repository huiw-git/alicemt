---
title: Move Database Files
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 89f01b10-5fae-4ed8-b0fb-a4b9f540fd28
---
# Move Database Files
  In [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], you can move system and user databases by specifying the new file location in the FILENAME clause of the [ALTER DATABASE](../Topic/ALTER%20DATABASE%20\(Transact-SQL\).md) statement. Data, log, and full\-text catalog files can be moved in this way. This may be useful in the following situations:  
  
-   Failure recovery. For example, the database is in suspect mode or has shut down, because of a hardware failure.  
  
-   Planned relocation.  
  
-   Relocation for scheduled disk maintenance.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Move User Databases](../../Topics\TopicNameNotContainA/Move-User-Databases.md)|Describes the procedures for moving user database files and full\-text catalog files to a new location.|  
|[Move System Databases](../../Topics\TopicNameNotContainA/Move-System-Databases.md)|Describes the procedures for moving system database files to a new location.|  
  
## See Also  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20\(Transact-SQL\).md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../Topic/CREATE%20DATABASE%20\(SQL%20Server%20Transact-SQL\).md)   
 [Database Detach and Attach &#40;SQL Server&#41;](../Topic/Database%20Detach%20and%20Attach%20\(SQL%20Server\).md)  
  
  