---
title: "Test for new conversion"
ms.custom: na
ms.date: 08/09/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 19dfccd0-671d-454c-9fdb-b8931de608fa
caps.latest.revision: 7
---
# Test for new conversion
The SQLServer:Dep\\\recated Features object in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] provides a counter to monitor the features designated as deprecated. In each case the counter provides a usage count that lists the number of times the deprecated feature was encountered since [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] last started.  
  
 The value of these counters are also available by executing the following statement:  
  
```  
SELECT \* FROM sys.dm_os_performance_counters   
WHERE object_name \= 'SQLServer:Deprecated Features';  
```  
  
 The following table describes the SQL Server Deprecated Features counter instances.  
  
```  
SELECT \* FROM sys.dm_os_performance_counters   
WHERE object_name \= 'SQLServer:Deprecated Features';  
```  
  
 The following table describes the SQL Server Deprecated Features counter instances.  
  
```  
SELECT \* FROM sys.dm_os_performance_counters   
WHERE object_name \= 'SQLServer:Deprecated Features';  
```  
  
 The following table describes the SQL Server Deprecated Features counter instances.  
  
```  
SELECT \* FROM sys.dm_os_performance_counters   
WHERE object_name \= 'SQLServer:Deprecated Features';  
```  
  
 The following table describes the SQL Server Deprecated Features counter instances.  
  
```  
SELECT \* FROM sys.dm_os_performance_counters   
WHERE object_name \= 'SQLServer:Deprecated Features';  
```  
  
## See Also  
 [Deprecated Database Engine Features in SQL Server 2016](../../Topics/TopicNameNotContainA/Deprecated-Database-Engine-Features-in-SQL-Server-2016.md)   
 [Deprecated Full-Text Search Features in SQL Server 2016](../../Topics/TopicNameNotContainA/Deprecated-Full-Text-Search-Features-in-SQL-Server-2016.md)   
 [Deprecation Announcement Event Class](../../Topics/TopicNameNotContainA/Deprecation-Announcement-Event-Class.md)   
 [Deprecation Final Support Event Class](../../Topics/TopicNameNotContainA/Deprecation-Final-Support-Event-Class.md)   
 [Discontinued Database Engine Functionality in SQL Server 2016](../../Topics/TopicNameNotContainA/Discontinued-Database-Engine-Functionality-in-SQL-Server-2016.md)   
 [Discontinued Full-Text Search Features in SQL Server 2016](../../Topics/TopicNameNotContainA/Discontinued-Full-Text-Search-Features-in-SQL-Server-2016.md)   
 [Use SQL Server Objects](../../Topics/TopicNameNotContainA/Use-SQL-Server-Objects.md)