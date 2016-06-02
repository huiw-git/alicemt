---
title: external scripts enabled Server Configuration Option
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: language-reference
ms.assetid: 9d0ce165-8719-4007-9ae8-00f85cab3a0d
---
# external scripts enabled Server Configuration Option
  Use the **external scripts enabled** option to enable the execution of scripts with certain remote language extensions. This property will be OFF by default. Setup can optionally set this property to true if **Advanced Analytics Services** is installed.  
  
||  
|-|  
|**Applies to**: [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] \([!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] through [current version](http://go.microsoft.com/fwlink/p/?LinkId=299658).|  
  
 You must enable the external script enabled option before you can execute an external script using the **sp\_execute\_external\_script** procedure. Use **sp\_execute\_external\_script** to execute scripts written in a supported language such as R. In [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)], [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] is comprised of a server component installed with [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)], and a set of workstation tools and connectivity libraries that connect the data scientist to the high\-performance environment of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  Install the **Advanced Analytics Extensions** feature during [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup to enable the execution of R scripts. For more information, see [Installing Previous Versions of SQL Server R Services](../../Topics\TopicNameNotContainA/Installing-Previous-Versions-of-SQL-Server-R-Services.md).  
  
 Execute the following script to enable external scripts.  
  
```  
sp_configure 'external scripts enabled', 1;  
RECONFIGURE;  
```  
  
 You must restart [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to make this change effective.  
  
## See Also  
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../Topic/RECONFIGURE%20\(Transact-SQL\).md)   
 [sp_execute_external_script &#40;Transact-SQL&#41;](../Topic/sp_execute_external_script%20\(Transact-SQL\).md)   
 [SQL Server R Services](../../Topics\TopicNameNotContainA/SQL-Server-R-Services.md)  
  
  