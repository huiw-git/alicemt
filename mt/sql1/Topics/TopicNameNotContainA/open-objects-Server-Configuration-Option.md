---
title: "open objects Server Configuration Option"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c8424d3c-86ba-4cc5-bf0c-be4ce44bdd04
caps.latest.revision: 27
caps.handback.revision: 0
manager: jhubbard
---
# open objects Server Configuration Option
This option is still present in **sp_configure**, although its functionality has been disabled in [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. (The setting has no effect.) In [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], the number of open database objects is managed dynamically and is limited only by the available memory. The **open objects** option available in **sp_configure** for backward compatibility with existing scripts.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../Topics/TopicNameContainA/tokens/ssNoteDepFutureDontUse_md.md)]  
  
## See Also  
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)