---
title: MSMQ Connection Manager Editor
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ef842cb4-82da-4550-85fe-9bedbc1e77c7
---
# MSMQ Connection Manager Editor
  Use the **MSMQ Connection Manager** dialog box to specify the path to a Message Queuing \(also known as MSMQ\) message queue.  
  
 To learn more about the MSMQ connection manager, see [MSMQ Connection Manager](../../Topics\TopicNameNotContainA/MSMQ-Connection-Manager.md).  
  
> [!NOTE]  
>  The MSMQ connection manager supports local public and private queues and remote public queues. It does not support remote private queues. For a workaround that uses the Script Task, see [Sending to a Remote Private Message Queue with the Script Task](../Topic/Sending%20to%20a%20Remote%20Private%20Message%20Queue%20with%20the%20Script%20Task.md).  
  
## Options  
 **Name**  
 Provide a unique name for the MSMQ connection manager in the workflow. The name provided will be displayed within [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer.  
  
 **Description**  
 Describe the connection manager. As a best practice, describe the connection manager in terms of its purpose, to make packages self\-documenting and easier to maintain.  
  
 **Path**  
 Type the complete path of the message queue. The format of the path depends on the type of queue.  
  
|Queue type|Sample path|  
|----------------|-----------------|  
|Public|\<computer name\>\\\<queue name\>|  
|Private|\<computer name\>\\Private$\\\<queue name\>|  
  
 You can use "." to represent the local computer.  
  
 **Test**  
 After configuring the MSMQ connection manager, confirm that the connection is viable by clicking **Test**.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)  
  
  