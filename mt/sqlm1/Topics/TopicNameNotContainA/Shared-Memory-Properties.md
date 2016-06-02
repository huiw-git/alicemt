---
title: Shared Memory Properties
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dc1704da-eacd-4d26-b529-c996f958ca4b
---
# Shared Memory Properties
  Use the **Protocol**page on the **Shared Memory Properties** dialog box to enable or disable the shared memory protocol. Shared memory is the simplest protocol to use and has no configurable settings. Because clients using the shared memory protocol can only connect to a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance running on the same computer, it is not useful for most database activity. Use the shared memory protocol for troubleshooting when you suspect the other protocols are configured incorrectly.  
  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] must be restarted to enable or disable the protocol.  
  
## Options  
 **Enabled**  
 Possible values are **Yes** and **No**. The shared memory protocol is enabled by default.  
  
## See Also  
 [Choosing a Network Protocol](../Topic/Choosing%20a%20Network%20Protocol.md)   
 [Creating a Valid Connection String Using Shared Memory Protocol](../../Topics\TopicNameContainA/Creating-a-Valid-Connection-String-Using-Shared-Memory-Protocol.md)  
  
  