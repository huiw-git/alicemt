---
title: Broadcast a Shutdown Message (Command Prompt)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9f20ccd5-d952-431d-ba12-339911af9430
---
# Broadcast a Shutdown Message (Command Prompt)
  This topic describes how to broadcast a shutdown message in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using the **net send** command. In the message, include the time the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] will be stopped so that users can finish their tasks.  
  
##  <a name="SSMSProcedure"></a>  
  
#### To broadcast a shutdown message  
  
1.  From a command prompt, enter:  
  
     **net send \/users "message"**  
  
     The **\/users** option specifies that the message be sent to all users connected to the server  
  
> [!NOTE]  
>  The **net send** command requires the messenger service to be running on both the sending and the receiving computers. The messenger service is disabled by default on Windows Server 2003. For information about **net send**, see the Windows documentation.  
  
 On your network, it may be more appropriate to contact users by e\-mail or the telephone. To determine which users are currently connected to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], use the Activity Monitor. For information on the Activity Monitor, see [Activity Monitor](../../Topics\TopicNameNotContainA/Activity-Monitor.md) and [Open Activity Monitor &#40;SQL Server Management Studio&#41;](../Topic/Open%20Activity%20Monitor%20\(SQL%20Server%20Management%20Studio\).md).  
  
## See Also  
 [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../Topics\TopicNameNotContainA/Start,-Stop,-Pause,-Resume,-Restart-the-Database-Engine,-SQL-Server-Agent,-or-SQL-Server-Browser-Service.md)  
  
  