---
title: "Database Engine Configuration - Filestream"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 641a10a1-ae52-4d26-8f1c-a032a4aeff02
caps.latest.revision: 13
caps.handback.revision: 0
manager: jhubbard
---
# Database Engine Configuration - Filestream
Use this page to enable FILESTREAM for this installation of [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)]. FILESTREAM integrates the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)] with an NTFS file system by storing **varbinary(max)** binary large object (BLOB) data as files on the file system. [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements can insert, update, query, search, and back up FILESTREAM data. Win32 file system interfaces provide streaming access to the data.  
  
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
 [Enable and Configure FILESTREAM](../../Topics/TopicNameNotContainA/Enable-and-Configure-FILESTREAM.md)   
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)