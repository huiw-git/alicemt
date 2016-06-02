---
title: MSMQ Connection Manager
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a86900e2-450e-479f-b207-e1b02361d395
---
# MSMQ Connection Manager
  An MSMQ connection manager enables a package to connect to a message queue that uses Message Queuing \(also known as MSMQ\). The Message Queue task that [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] includes uses an MSMQ connection manager.  
  
 When you add an MSMQ connection manager to a package, [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] creates a connection manager that will resolve to an MSMQ connection at run time, sets the connection manager properties, and adds the connection manager to the **Connections** collection on the package. The **ConnectionManagerType** property of the connection manager is set to **MSMQ**.  
  
 You can configure an MSMQ connection manager in the following ways:  
  
-   Provide a connection string.  
  
-   Provide the path of the message queue to connect to.  
  
 The format of the path depends on the type of queue, as shown in the following table.  
  
|Queue type|Sample path|  
|----------------|-----------------|  
|Public|\<computer name\>\\\<queue name\>|  
|Private|\<computer name\>\\Private$\\\<queue name\>|  
  
 You can use a period \(.\) to represent the local computer.  
  
## Configuration of the MSMQ Connection Manager  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, see [MSMQ Connection Manager Editor](../../Topics\TopicNameNotContainA/MSMQ-Connection-Manager-Editor.md).  
  
 For information about configuring a connection manager programmatically, see [ConnectionManager](assetId:///T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager) and [Adding Connections Programmatically](../Topic/Adding%20Connections%20Programmatically.md).  
  
## See Also  
 [Message Queue Task](../../Topics\TopicNameNotContainA/Message-Queue-Task.md)   
 [Integration Services &#40;SSIS&#41; Connections](../Topic/Integration%20Services%20\(SSIS\)%20Connections.md)  
  
  