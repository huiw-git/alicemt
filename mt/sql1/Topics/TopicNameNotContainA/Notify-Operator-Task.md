---
title: "Notify Operator Task"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6c816c68-c6d6-44e4-bb34-c8e060a958a1
caps.latest.revision: 44
caps.handback.revision: 0
manager: jhubbard
---
# Notify Operator Task
The Notify Operator task sends notification messages to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent operators. A [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent operator is an alias for a person or group that can receive electronic notifications. For more information about [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] operators, see [Defining Operators](assetId:///38e8488f-2669-4cea-b9c3-5f394a663678).  
  
 By using the Notify Operator task, a package can notify one or more operators via e-mail, pager, or **net send**. Each operator can be notified by different methods. For example, OperatorA is notified by e-mail and pager, and OperatorB is notified by pager and **net send**. The operators who receive notifications from the task must be members of the **OperatorNotify** collection on the Notify Operator task.  
  
 The Notify Operator task is the only database maintenance task that does not encapsulate a Transact-SQL statement or a DBCC command.  
  
## Configuration of the Notify Operator Task  
 You can set properties through [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer. This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer, click the following topic:  
  
-   [Notify Operator Task (Maintenance Plan)](../../Topics/TopicNameNotContainA/Notify-Operator-Task--Maintenance-Plan-.md)  
  
 For more information about how to set these properties in [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer, click the following topic:  
  
-   [Set the Properties of a Task or Container](../../Topics/TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md)