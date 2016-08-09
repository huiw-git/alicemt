---
title: "EKM provider enabled Server Configuration Option"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: da58ed50-3a13-4172-9065-960559d8f383
caps.latest.revision: 13
caps.handback.revision: 0
manager: jhubbard
---
# EKM provider enabled Server Configuration Option
The **EKM provider enabled** option controls Extensible Key Management device support in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. By default this option is off.  
  
 To enable or disable the feature, issue one of the following **sp_configure** commands:  
  
```  
/* Enable the external encryption provider option */  
sp_configure 'EKM provider enabled', 1  
/* Disable the external encryption provider option */  
sp_configure 'EKM provider enabled', 0  
```  
  
> [!NOTE]  
>  This option is not enabled in every edition of [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], see [Features Supported by the Editions of SQL Server 2016](../../Topics/TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md).  
  
## See Also  
 [Extensible Key Management (EKM)](../../Topics/TopicNameNotContainA/Extensible-Key-Management--EKM-.md)   
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [Monitor Resource Usage (System Monitor)](../../Topics/TopicNameNotContainA/Monitor-Resource-Usage--System-Monitor-.md)   
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)   
 [RECONFIGURE (Transact-SQL)](assetId:///2e6e4eeb-b70b-4f45-a253-28ac4e595d75)