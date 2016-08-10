---
title: "lightweight pooling Server Configuration Option"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2dc11b61-d065-4126-8e00-acf40390f9fb
caps.latest.revision: 32
caps.handback.revision: 0
manager: jhubbard
---
# lightweight pooling Server Configuration Option
Use the **lightweight pooling** option to provide a means of reducing the system overhead associated with the excessive context switching sometimes seen in symmetric multiprocessing (SMP) environments. When excessive context switching is present, lightweight pooling can provide better throughput by performing the context switching inline, thus helping to reduce user/kernel ring transitions.  
  
 Fiber mode is intended for certain situations in which the context switching of the UMS workers are the critical bottleneck in performance. Because this is rare, fiber mode rarely enhances performance or scalability on the typical system. Improved context switching in [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[winxpsvr](../../Topics/TopicNameContainA/tokens/winxpsvr_md.md)] has also reduced the need for fiber mode. We do not recommend that you use fiber mode scheduling for routine operation. This is because it can decrease performance by inhibiting the regular benefits of context switching, and because some components of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] that use Thread Local Storage (TLS) or thread-owned objects, such as mutexes (a type of Win32 kernel object), cannot function correctly in fiber mode.  
  
 Setting **lightweight pooling** to 1 causes [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] to switch to fiber mode scheduling. The default value for this option is 0.  
  
 The **lightweight pooling** option is an advanced option. If you are using the **sp_configure** system stored procedure to change the setting, you can change **lightweight pooling** only when **show advanced options** is set to 1. The setting takes effect after the server is restarted.  
  
> [!NOTE]  
>  Lightweight pooling is not supported for [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows 2000 and [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows XP. [!INCLUDE[winxpsvr](../../Topics/TopicNameContainA/tokens/winxpsvr_md.md)] provides full support for lightweight pooling.  
  
> [!NOTE]  
>  Common language runtime (CLR) execution is not supported under lightweight pooling. Disable one of two options: "clr enabled" or "lightweight pooling". Features that rely upon CLR and that do not work properly in fiber mode include the hierarchy data type, replication, and Policy-Based Management.  
  
## See Also  
 [clr enabled Server Configuration Option](../../Topics/TopicNameNotContainA/clr-enabled-Server-Configuration-Option.md)   
 [Server Configuration Options (SQL Server)](../../Topics/TopicNameNotContainA/Server-Configuration-Options--SQL-Server-.md)   
 [sp_configure (Transact-SQL)](assetId:///d18b251d-b37a-4f5f-b50c-502d689594c8)   
 [clr enabled Server Configuration Option](../../Topics/TopicNameNotContainA/clr-enabled-Server-Configuration-Option.md)