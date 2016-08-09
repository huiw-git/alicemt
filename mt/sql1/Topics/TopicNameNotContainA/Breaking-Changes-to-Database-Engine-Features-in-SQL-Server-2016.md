---
title: "Breaking Changes to Database Engine Features in SQL Server 2016"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 2016-05-03
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 47edefbd-a09b-4087-937a-453cd5c6e061
caps.latest.revision: 143
caps.handback.revision: 0
manager: jhubbard
---
# Breaking Changes to Database Engine Features in SQL Server 2016
This topic describes breaking changes in the [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)][!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] and earlier versions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. These changes might break applications, scripts, or functionalities that are based on earlier versions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. You might encounter these issues when you upgrade.  
  
##  <a name="SQL15"></a> Breaking Changes in [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)]  
  
-   The sample_ms column of sys.dm_io_virtual_file_stats has expanded from an **int** to a **bigint** data type.  
  
-   Using the MD2, MD4, MD5, SHA, or SHA1 hash algorithms (not recommended) requires setting the database compatibility level to earlier than 130.  
  
## Previous Versions  
  
-   [Breaking Changes to Database Engine Features in SQL Server 2014](https://msdn.microsoft.com/library/ms143179\(v=sql.120\))  
  
-   [Breaking Changes to Database Engine Features in SQL Server 2012](https://msdn.microsoft.com/library/ms143179\(v=sql.110\))  
  
-   [Breaking Changes to Database Engine Features in SQL Server 2008](https://msdn.microsoft.com/library/ms143179\(v=sql.100\))  
  
## See Also  
 [Deprecated Database Engine Features in SQL Server 2016](../../Topics/TopicNameNotContainA/Deprecated-Database-Engine-Features-in-SQL-Server-2016.md)   
 [Discontinued Database Engine Functionality in SQL Server 2016](../../Topics/TopicNameNotContainA/Discontinued-Database-Engine-Functionality-in-SQL-Server-2016.md)   
 [SQL Server Database Engine Backward Compatibility](../../Topics/TopicNameNotContainA/SQL-Server-Database-Engine-Backward-Compatibility.md)   
 [ALTER DATABASE Compatibility Level (Transact-SQL)](assetId:///ca5fd220-d5ea-4182-8950-55d4101a86f6)