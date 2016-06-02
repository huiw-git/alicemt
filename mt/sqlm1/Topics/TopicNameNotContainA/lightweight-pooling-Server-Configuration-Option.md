---
title: lightweight pooling Server Configuration Option
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2dc11b61-d065-4126-8e00-acf40390f9fb
---
# lightweight pooling Server Configuration Option
  Use the **lightweight pooling** option to provide a means of reducing the system overhead associated with the excessive context switching sometimes seen in symmetric multiprocessing \(SMP\) environments. When excessive context switching is present, lightweight pooling can provide better throughput by performing the context switching inline, thus helping to reduce user\/kernel ring transitions.  
  
 Fiber mode is intended for certain situations in which the context switching of the UMS workers are the critical bottleneck in performance. Because this is rare, fiber mode rarely enhances performance or scalability on the typical system. Improved context switching in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[winxpsvr](../../Token\Other/winxpsvr_md.md)] has also reduced the need for fiber mode. We do not recommend that you use fiber mode scheduling for routine operation. This is because it can decrease performance by inhibiting the regular benefits of context switching, and because some components of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that use Thread Local Storage \(TLS\) or thread\-owned objects, such as mutexes \(a type of Win32 kernel object\), cannot function correctly in fiber mode.  
  
 Setting **lightweight pooling** to 1 causes [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to switch to fiber mode scheduling. The default value for this option is 0.  
  
 The **lightweight pooling** option is an advanced option. If you are using the **sp\_configure** system stored procedure to change the setting, you can change **lightweight pooling** only when **show advanced options** is set to 1. The setting takes effect after the server is restarted.  
  
> [!NOTE]  
>  Lightweight pooling is not supported for [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows 2000 and [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows XP. [!INCLUDE[winxpsvr](../../Token\Other/winxpsvr_md.md)] provides full support for lightweight pooling.  
  
> [!NOTE]  
>  Common language runtime \(CLR\) execution is not supported under lightweight pooling. Disable one of two options: "clr enabled" or "lightweight pooling". Features that rely upon CLR and that do not work properly in fiber mode include the hierarchy data type, replication, and Policy\-Based Management.  
  
## See Also  
 [clr enabled Server Configuration Option](../../Topics\TopicNameNotContainA/clr-enabled-Server-Configuration-Option.md)   
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)   
 [sp_configure &#40;Transact-SQL&#41;](../Topic/sp_configure%20\(Transact-SQL\).md)   
 [clr enabled Server Configuration Option](../../Topics\TopicNameNotContainA/clr-enabled-Server-Configuration-Option.md)  
  
  