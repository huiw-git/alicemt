---
title: "SQL Server Properties (FILESTREAM Page)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8a8d38d3-e97a-4b09-a40b-659b2e3a5c47
caps.latest.revision: 11
caps.handback.revision: 0
manager: jhubbard
---
# SQL Server Properties (FILESTREAM Page)
Use this page to enable FILESTREAM for this installation of [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)].  
  
## UIElement List  
 **Enable FILESTREAM for Transact-SQL access**  
 Select to enable FILESTREAM for [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] access. This control must be checked before the other control options will be available.  
  
 **Enable FILESTREAM for file I/O streaming access**  
 Select to enable Win32 streaming access for FILESTREAM.  
  
 **Windows share name**  
 Use this control to enter the name of the Windows share in which the FILESTREAM data will be stored.  
  
 **Allow remote clients to have streaming access to FILESTREAM data**  
 Select this control to allow remote clients to access this FILESTREAM data on this server.  
  
## See Also  
 [FILESTREAM (SQL Server)](../../Topics/TopicNameNotContainA/FILESTREAM--SQL-Server-.md)   
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)