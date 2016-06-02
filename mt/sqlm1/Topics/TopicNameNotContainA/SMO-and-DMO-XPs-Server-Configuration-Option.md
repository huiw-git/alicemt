---
title: SMO and DMO XPs Server Configuration Option
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bcd945ba-5d81-4124-9a2b-d87491c2a369
---
# SMO and DMO XPs Server Configuration Option
  Use the SMO and DMO XPs option to enable [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Management Object \(SMO\) extended stored procedures on this server.  
  
 Note than beginning in [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], DMO has been removed from [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
 The possible values are described in the following table:  
  
|Value|Meaning|  
|-----------|-------------|  
|0|SMO XPs are not available.|  
|1|SMO XPs are available. This is the default.|  
  
 The setting takes effect immediately.  
  
## Examples  
 The following example enables SMO extended stored procedures.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'SMO and DMO XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## See Also  
 [SQL Server Management Objects &#40;SMO&#41; Programming Guide](../Topic/SQL%20Server%20Management%20Objects%20\(SMO\)%20Programming%20Guide.md)  
  
  