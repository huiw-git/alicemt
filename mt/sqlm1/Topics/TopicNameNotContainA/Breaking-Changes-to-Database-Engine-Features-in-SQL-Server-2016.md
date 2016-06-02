---
title: Breaking Changes to Database Engine Features in SQL Server 2016
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 47edefbd-a09b-4087-937a-453cd5c6e061
---
# Breaking Changes to Database Engine Features in SQL Server 2016
  This topic describes breaking changes in the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)][!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] and earlier versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. These changes might break applications, scripts, or functionalities that are based on earlier versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. You might encounter these issues when you upgrade.  
  
##  <a name="SQL15"></a> Breaking Changes in [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)]  
  
-   The sample\_ms column of sys.dm\_io\_virtual\_file\_stats has expanded from an **int** to a **bigint** data type.  
  
-   Using the MD2, MD4, MD5, SHA, or SHA1 hash algorithms \(not recommended\) requires setting the database compatibility level to earlier than 130.  
  
## Previous Versions  
  
-   [Breaking Changes to Database Engine Features in SQL Server 2014](https://msdn.microsoft.com/library/ms143179\(v=sql.120\))  
  
-   [Breaking Changes to Database Engine Features in SQL Server 2012](https://msdn.microsoft.com/library/ms143179\(v=sql.110\))  
  
-   [Breaking Changes to Database Engine Features in SQL Server 2008](https://msdn.microsoft.com/library/ms143179\(v=sql.100\))  
  
## See Also  
 [Deprecated Database Engine Features in SQL Server 2016](../../Topics\TopicNameNotContainA/Deprecated-Database-Engine-Features-in-SQL-Server-2016.md)   
 [Discontinued Database Engine Functionality in SQL Server 2016](../../Topics\TopicNameNotContainA/Discontinued-Database-Engine-Functionality-in-SQL-Server-2016.md)   
 [SQL Server Database Engine Backward Compatibility](../../Topics\TopicNameNotContainA/SQL-Server-Database-Engine-Backward-Compatibility.md)   
 [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20Compatibility%20Level%20\(Transact-SQL\).md)  
  
  