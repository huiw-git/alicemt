---
title: Cancel Option (Distributed Replay Administration Tool)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fea376de-307a-4b45-b7e2-37df88f3681a
---
# Cancel Option (Distributed Replay Administration Tool)
  The [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Distributed Replay administration tool, **DReplay.exe**, is a command\-line tool that you can use to communicate with the distributed replay controller. This topic describes the **cancel** command\-line option and corresponding syntax.  
  
 The **cancel** option cancels the current operation that is running on the controller.  
  
 ![Topic link icon](../../Images\Image\ImageNotContaina/Topic_Link.gif "Topic_Link") For more information about the syntax conventions that are used with the administration tool syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](../Topic/Transact-SQL%20Syntax%20Conventions%20\(Transact-SQL\).md).  
  
## Syntax  
  
```  
  
dreplay cancel [-m controller] [-q]   
```  
  
#### Parameters  
 **\-m** *controller*  
 The computer name of the controller. You can use "`localhost`" or "`.`" to refer to the local computer.  
  
 If the **\-m** parameter is not specified, the local computer is used.  
  
 **\-q**  
 Quiet mode. Does not prompt for confirmation.  
  
 The **\-q** parameter is optional.  
  
## Examples  
 In the following example, a cancel request is submitted in quiet mode. The value `localhost` indicates that the controller service is running on the same computer as the administration tool.  
  
```  
dreplay cancel –m localhost -q  
```  
  
## Permissions  
 You must run the administration tool as an interactive user, as either a local user or a domain user account. To use a local user account, the administration tool and controller must be running on the same computer.  
  
 For more information, see [Distributed Replay Security](../../Topics\TopicNameNotContainA/Distributed-Replay-Security.md).  
  
## See Also  
 [SQL Server Distributed Replay](../../Topics\TopicNameNotContainA/SQL-Server-Distributed-Replay.md)  
  
  