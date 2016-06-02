---
title: ad hoc distributed queries Server Configuration Option
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5b982015-e196-44c3-83b8-275fb9d769b2
---
# ad hoc distributed queries Server Configuration Option
  By default, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] does not allow ad hoc distributed queries using OPENROWSET and OPENDATASOURCE. When this option is set to 1, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] allows ad hoc access. When this option is not set or is set to 0, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] does not allow ad hoc access.  
  
 Ad hoc distributed queries use the OPENROWSET and OPENDATASOURCE functions to connect to remote data sources that use OLE DB. OPENROWSET and OPENDATASOURCE should be used only to reference OLE DB data sources that are accessed infrequently. For any data sources that will be accessed more than several times, define a linked server.  
  
> [!IMPORTANT]  
>  Enabling the use of ad hoc names means that any authenticated login to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] can access the provider. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] administrators should enable this feature for providers that are safe to be accessed by any local login.  
  
## Remarks  
 Attempting to make an ad hoc connection with **Ad Hoc Distributed Queries** not enabled results in error: Msg 7415, Level 16, State 1, Line 1  
  
 Ad hoc access to OLE DB provider 'Microsoft.ACE.OLEDB.12.0' has been denied. You must access this provider through a linked server.  
  
## Examples  
 The following example enables ad hoc distributed queries and then queries a server named `Seattle1` using the `OPENROWSET` function.  
  
```  
sp_configure 'show advanced options', 1;  
RECONFIGURE;  
sp_configure 'Ad Hoc Distributed Queries', 1;  
RECONFIGURE;  
GO  
  
SELECT a.*  
FROM OPENROWSET('SQLNCLI', 'Server=Seattle1;Trusted_Connection=yes;',  
     'SELECT GroupName, Name, DepartmentID  
      FROM AdventureWorks2012.HumanResources.Department  
      ORDER BY GroupName, Name') AS a;  
GO  
```  
  
## See Also  
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)   
 [Linked Servers &#40;Database Engine&#41;](../Topic/Linked%20Servers%20\(Database%20Engine\).md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../Topic/OPENROWSET%20\(Transact-SQL\).md)   
 [OPENDATASOURCE &#40;Transact-SQL&#41;](../Topic/OPENDATASOURCE%20\(Transact-SQL\).md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../Topic/sp_addlinkedserver%20\(Transact-SQL\).md)  
  
  