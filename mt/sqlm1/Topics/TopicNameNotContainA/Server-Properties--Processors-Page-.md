---
title: Server Properties (Processors Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cc1581a2-492b-41f0-bda5-17909b65c4f7
---
# Server Properties (Processors Page)
  Use this page to view or modify your processor options. Processor affinity settings are only enabled when more than one processor is installed.  
  
## Options  
 **Processor Affinity**  
 Assigns processors to specific threads to eliminating processor reloads and reduce thread migration across processors. For more information, see [affinity mask Server Configuration Option](../../Topics\TopicNameNotContainA/affinity-mask-Server-Configuration-Option.md).  
  
 **I\/O Affinity**  
 Binds [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] disk I\/Os to a specified subset of CPUs. For more information, see [affinity Input-Output mask Server Configuration Option](../../Topics\TopicNameNotContainA/affinity-Input-Output-mask-Server-Configuration-Option.md).  
  
 **Automatically set processor affinity mask for all processors**  
 Allows [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to set the processor affinity.  
  
 **Automatically set I\/O affinity mask for all processors**  
 Allows [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to set the I\/O affinity.  
  
 **Maximum worker threads**  
 0 allows [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to dynamically set the number of worker threads. This setting is best for most systems. However, depending on your system configuration, setting this option to a specific value sometimes improves performance. For more information, see [Configure the max worker threads Server Configuration Option](../../Topics\TopicNameNotContainA/Configure-the-max-worker-threads-Server-Configuration-Option.md).  
  
 **Boost SQL Server priority**  
 Specifies whether [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] should run at a higher [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows scheduling priority than other processes on the same computer. For more information, see [Configure the priority boost Server Configuration Option](../../Topics\TopicNameNotContainA/Configure-the-priority-boost-Server-Configuration-Option.md).  
  
 **Use Windows fibers \(lightweight pooling\)**  
 Use Windows fibers instead of threads for the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service. Note that this is only available in Windows 2003 Server Edition. For more information, see [lightweight pooling Server Configuration Option](../../Topics\TopicNameNotContainA/lightweight-pooling-Server-Configuration-Option.md).  
  
 **Configured Values**  
 Displays the configured values for the options on this pane. If you change these values, click **Running Values** to see whether the changes have taken effect. If they have not, the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] must be restarted first.  
  
 **Running Values**  
 View the currently running values for the options on this pane. These values are read\-only.  
  
## See Also  
 [Server Configuration Options &#40;SQL Server&#41;](../Topic/Server%20Configuration%20Options%20\(SQL%20Server\).md)  
  
  