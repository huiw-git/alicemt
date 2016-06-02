---
title: Message Queue Task Editor (General Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 09368b18-37a5-4321-a173-7cfe5d42d2a2
---
# Message Queue Task Editor (General Page)
  Use the **General page** of the **Message Queue Task Editor** dialog box to name and describe the Message Queue task, to specify the message format, and to indicate whether the task sends or receives messages.  
  
 To learn about this task, see [Message Queue Task](../../Topics\TopicNameNotContainA/Message-Queue-Task.md).  
  
## Options  
 **Name**  
 Provide a unique name for the Message Queue task. This name is used as the label in the task icon.  
  
> [!NOTE]  
>  Task names must be unique within a package.  
  
 **Description**  
 Type a description of the Message Queue task.  
  
 **Use2000Format**  
 Indicate whether to use the 2000 format of Message Queuing \(also known as MSMQ\). The default is **False**.  
  
 **MSMQConnection**  
 Select an existing MSMQ connection manager or click \<**New connection...**\> to create a new connection manager.  
  
 **Related Topics**: [MSMQ Connection Manager](../../Topics\TopicNameNotContainA/MSMQ-Connection-Manager.md), [MSMQ Connection Manager Editor](../../Topics\TopicNameNotContainA/MSMQ-Connection-Manager-Editor.md)  
  
 **Message**  
 Specify whether the Message Queue task sends or receive messages. If you select **Send message**, the Send page is listed in the left pane of the dialog box; if you select **Receive message**, the Receive page is listed. By default, this value is set to **Send message**.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Message Queue Task Editor &#40;Receive Page&#41;](../Topic/Message%20Queue%20Task%20Editor%20\(Receive%20Page\).md)   
 [Message Queue Task Editor &#40;Send Page&#41;](../Topic/Message%20Queue%20Task%20Editor%20\(Send%20Page\).md)   
 [Expressions Page](../../Topics\TopicNameNotContainA/Expressions-Page.md)  
  
  