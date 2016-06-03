---
title: Add Enumeration to a Control Flow
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f212b5fb-3cc4-422e-9b7c-89eb769a812a
---
# Add Enumeration to a Control Flow
  [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] includes the Foreach Loop container, a control flow element that makes it simple to include a looping construct that enumerates files and objects in the control flow of a package. For more information, see [Foreach Loop Container](../../Topics\TopicNameNotContainA/Foreach-Loop-Container.md).  
  
 The Foreach Loop container provides no functionality; it provides only the structure in which you build the repeatable control flow, specify an enumerator type, and configure the enumerator. To provide container functionality, you must include at least one task in the Foreach Loop container. For more information, see [Integration Services Tasks](../../Topics\TopicNameNotContainA/Integration-Services-Tasks.md).  
  
 The Foreach Loop container can include a control flow with multiple tasks and other containers. Adding tasks and containers to a Foreach Loop container is similar to adding them to a package, except you drag the tasks and containers to the Foreach Loop container instead of to the package. If the Foreach Loop container includes more than one task or container, you can connect them using precedence constraints just as you do in a package. For more information, see [Precedence Constraints](../../Topics\TopicNameNotContainA/Precedence-Constraints.md).  
  
### To implement a Foreach Loop container in a control flow  
  
1.  Add the Foreach Loop container to the package. For more information, see [Add or Delete a Task or a Container in a Control Flow](../../Topics\TopicNameContainA/Add-or-Delete-a-Task-or-a-Container-in-a-Control-Flow.md).  
  
2.  Add tasks and containers to the Foreach Loop container. For more information, see [Add or Delete a Task or a Container in a Control Flow](../../Topics\TopicNameContainA/Add-or-Delete-a-Task-or-a-Container-in-a-Control-Flow.md).  
  
3.  Connect tasks and containers in the Foreach Loop container using precedence constraints. For more information, see [Connect Tasks and Containers by Using a Default Precedence Constraint](../../Topics\TopicNameContainA/Connect-Tasks-and-Containers-by-Using-a-Default-Precedence-Constraint.md).  
  
4.  Configure the Foreach Loop container. For more information, see [Configure a Foreach Loop Container](../../Topics\TopicNameContainA/Configure-a-Foreach-Loop-Container.md).  
  
## See Also  
 [Add or Delete a Task or a Container in a Control Flow](../../Topics\TopicNameContainA/Add-or-Delete-a-Task-or-a-Container-in-a-Control-Flow.md)   
 [Group or Ungroup Components](../../Topics\TopicNameNotContainA/Group-or-Ungroup-Components.md)   
 [Precedence Constraints](../../Topics\TopicNameNotContainA/Precedence-Constraints.md)   
 [Add Iteration to a Control Flow](../../Topics\TopicNameContainA/Add-Iteration-to-a-Control-Flow.md)   
 [Control Flow](../../Topics\TopicNameNotContainA/Control-Flow.md)  
  
  