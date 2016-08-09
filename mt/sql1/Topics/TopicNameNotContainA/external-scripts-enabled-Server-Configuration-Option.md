---
title: "external scripts enabled Server Configuration Option"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 2015-10-28
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: language-reference
ms.assetid: 9d0ce165-8719-4007-9ae8-00f85cab3a0d
caps.latest.revision: 9
caps.handback.revision: 0
manager: jhubbard
---
# external scripts enabled Server Configuration Option
Use the **external scripts enabled** option to enable the execution of scripts with certain remote language extensions. This property will be OFF by default. Setup can optionally set this property to true if **Advanced Analytics Services** is installed.  
  
||  
|-|  
|**Applies to**: [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] ([!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)] through [current version](http://go.microsoft.com/fwlink/p/?LinkId=299658).|  
  
 You must enable the external script enabled option before you can execute an external script using the **sp_execute_external_script** procedure. Use **sp_execute_external_script** to execute scripts written in a supported language such as R. In [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)], [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] is comprised of a server component installed with [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)], and a set of workstation tools and connectivity libraries that connect the data scientist to the high-performance environment of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  Install the **Advanced Analytics Extensions** feature during [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] setup to enable the execution of R scripts. For more information, see [Installing Previous Versions of SQL Server R Services](../../Topics/TopicNameNotContainA/Installing-Previous-Versions-of-SQL-Server-R-Services.md).  
  
 Execute the following script to enable external scripts.  
  
```  
sp_configure 'external scripts enabled', 1;  
RECONFIGURE;  
```  
  
 You must restart [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] to make this change effective.  
  
## See Also  
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)   
 [RECONFIGURE (Transact-SQL)](assetId:///2e6e4eeb-b70b-4f45-a253-28ac4e595d75)   
 [sp_execute_external_script (Transact-SQL)](assetId:///de4e1fcd-0e1a-4af3-97ee-d1becc7f04df)   
 [SQL Server R Services](../../Topics/TopicNameNotContainA/SQL-Server-R-Services.md)