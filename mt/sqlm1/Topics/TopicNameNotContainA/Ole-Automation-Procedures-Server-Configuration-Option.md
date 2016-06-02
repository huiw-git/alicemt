---
title: Ole Automation Procedures Server Configuration Option
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e8982e05-4984-4406-9760-285e8c028ddf
---
# Ole Automation Procedures Server Configuration Option
  Use the **Ole Automation Procedures** option to specify whether OLE Automation objects can be instantiated within [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] batches. This option can also be configured using the Policy\-Based Management or the **sp\_configure** stored procedure. For more information, see [Surface Area Configuration](../../Topics\TopicNameNotContainA/Surface-Area-Configuration.md).  
  
 The **Ole Automation Procedures** option can be set to the following values.  
  
 0  
 OLE Automation Procedures are disabled. Default for new instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
 1  
 OLE Automation Procedures are enabled.  
  
 When OLE Automation Procedures are enabled, a call to **sp\_OACreate** will start the OLE shared execution environment.  
  
 The current value of the **Ole Automation Procedures** option can be viewed and changed by using the **sp\_configure** system stored procedure.  
  
## Examples  
 The following example shows how to view the current setting of OLE Automation procedures.  
  
```  
EXEC sp_configure 'Ole Automation Procedures';  
GO  
```  
  
 The following example shows how to enable OLE Automation procedures.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Ole Automation Procedures', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## See Also  
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../Topic/RECONFIGURE%20\(Transact-SQL\).md)   
 [Surface Area Configuration](../../Topics\TopicNameNotContainA/Surface-Area-Configuration.md)   
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)  
  
  