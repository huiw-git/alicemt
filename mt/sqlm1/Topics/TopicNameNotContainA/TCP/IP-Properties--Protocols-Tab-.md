---
title: TCP/IP Properties (Protocols Tab)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 007638fc-3a24-4460-adbe-545ded5d6f88
---
# TCP/IP Properties (Protocols Tab)
  Use the **TCP\/IP Properties** dialog box to configure the options for the TCP\/IP protocol. Click **TCP\/IP** in the left pane, to show individual IP address configurations in the details pane.  
  
 Microsoft [!INCLUDE[ssNoVersion](../../../Token\Other/ssNoVersion_md.md)] must be restarted before the changes take effect.  
  
## Options  
 **Enabled**  
 Possible values are **Yes** and **No**.  
  
 **Keep Alive**  
 Specify the interval \(milliseconds\) in which keep\-alive packets are transmitted to verify that the computer at the remote end of a connection is still available.  
  
 **Listen All**  
 Specify whether SQL Server will listen on all the IP addresses that are bound to network cards on the computer. If set to **No**, configure each IP address separately using the properties dialog box for each IP address. If set to **Yes**, the settings of the **IPAll** properties box will apply to all IP addresses. Default value is **Yes**.  
  
 **No Delay**  
 [!INCLUDE[ssNoVersion](../../../Token\Other/ssNoVersion_md.md)] does not implement changes to this property.  
  
## See Also  
 [Choosing a Network Protocol](../Topic/Choosing%20a%20Network%20Protocol.md)   
 [Creating a Valid Connection String Using TCP IP](../../../Topics\TopicNameContainA/Creating-a-Valid-Connection-String-Using-TCP-IP.md)  
  
  