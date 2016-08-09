---
title: "Ole Automation Procedures Server Configuration Option"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e8982e05-4984-4406-9760-285e8c028ddf
caps.latest.revision: 21
caps.handback.revision: 0
manager: jhubbard
---
# Ole Automation Procedures Server Configuration Option
Use the **Ole Automation Procedures** option to specify whether OLE Automation objects can be instantiated within [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] batches. This option can also be configured using the Policy-Based Management or the **sp_configure** stored procedure. For more information, see [Surface Area Configuration](../../Topics/TopicNameNotContainA/Surface-Area-Configuration.md).  
  
 The **Ole Automation Procedures** option can be set to the following values.  
  
 0  
 OLE Automation Procedures are disabled. Default for new instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
 1  
 OLE Automation Procedures are enabled.  
  
 When OLE Automation Procedures are enabled, a call to **sp_OACreate** will start the OLE shared execution environment.  
  
 The current value of the **Ole Automation Procedures** option can be viewed and changed by using the **sp_configure** system stored procedure.  
  
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
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)   
 [RECONFIGURE (Transact-SQL)](assetId:///2e6e4eeb-b70b-4f45-a253-28ac4e595d75)   
 [Surface Area Configuration](../../Topics/TopicNameNotContainA/Surface-Area-Configuration.md)   
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)