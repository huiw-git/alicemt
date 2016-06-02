---
title: Status Option (Distributed Replay Administration Tool)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ea89386e-1598-4412-8b37-680d14b2a5b6
---
# Status Option (Distributed Replay Administration Tool)
  The [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Distributed Replay administration tool, **DReplay.exe**, is a command\-line tool that you can use to communicate with the distributed replay controller. This topic describes the **status** command\-line option and corresponding syntax.  
  
 The **status** option queries the controller and displays the current status.  
  
 ![Topic link icon](../../Images\Image\ImageNotContaina/Topic_Link.gif "Topic_Link") For more information about the syntax conventions that are used with the administration tool syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](../Topic/Transact-SQL%20Syntax%20Conventions%20\(Transact-SQL\).md).  
  
## Syntax  
  
```  
  
dreplay status [-m controller] [-f status_interval]  
```  
  
#### Parameters  
 **\-m** *controller*  
 Specifies the computer name of the controller. You can use "`localhost`" or "`.`" to refer to the local computer.  
  
 If the **\-m** parameter is not specified, the local computer is used.  
  
 **\-f** *status\_interval*  
 Specifies the frequency \(in seconds\) at which to display the status.  
  
 If the **\-f** parameter is not specified, the default interval is 30 seconds.  
  
## Examples  
 In the following example, the current status is displayed every 60 seconds. The value `localhost` indicates that the controller service is running on the same computer as the administration tool.  
  
```  
dreplay status –m localhost -f 60  
```  
  
## Permissions  
 You must run the administration tool as an interactive user, as either a local user or a domain user account. To use a local user account, the administration tool and controller must be running on the same computer.  
  
 For more information, see [Distributed Replay Security](../../Topics\TopicNameNotContainA/Distributed-Replay-Security.md).  
  
## See Also  
 [SQL Server Distributed Replay](../../Topics\TopicNameNotContainA/SQL-Server-Distributed-Replay.md)   
 [Transact-SQL Debugger](../../Topics\TopicNameNotContainA/Transact-SQL-Debugger.md)  
  
  