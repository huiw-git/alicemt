---
title: Add Iteration to a Control Flow
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: eb3a7494-88ae-4165-9d0f-58715eb1734a
---
# Add Iteration to a Control Flow
  [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] includes the For Loop container, a control flow element that makes it simple to include looping that conditionally repeats a control flow in a package. For more information, see [For Loop Container](../../Topics\TopicNameNotContainA/For-Loop-Container.md).  
  
 The For Loop container evaluates a condition on each iteration of the loop, and stops when the condition evaluates to false. The For Loop container includes expressions for initializing the loop, specifying the evaluation condition that stops execution of the repeating control flow, and assigning a value to an expression that updates the value against which the evaluation condition is compared. You must provide an evaluation condition, but initialization and assignment expressions are optional.  
  
 The For Loop container provides no functionality; it provides only the structure in which you build the repeatable control flow. To provide container functionality, you must include at least one task in the For Loop container. For more information, see [Integration Services Tasks](../../Topics\TopicNameNotContainA/Integration-Services-Tasks.md).  
  
 The For Loop container can include a control flow with multiple tasks, and can include other containers. Adding tasks and containers to a For Loop container is similar to adding them to a package, except you drag the tasks and containers to the For Loop container instead of to the package. If the For Loop container includes more than one task or container, you can connect them using precedence constraints just as you do in a package. For more information, see [Precedence Constraints](../../Topics\TopicNameNotContainA/Precedence-Constraints.md).  
  
## Using Expressions in For Loop Configuration  
 When you configure the For Loop container by specifying an evaluation condition, initialization value, or assignment value, you can use either literals or expressions.  
  
 The expressions can include variables. The advantage of using variables is that they can be updated at run time, making the packages more flexible and easier to manage. The maximum length of an expression is 4000 characters.  
  
 When you specify a variable in an expression, you must preface the variable name with the at sign \(@\). For example, for a variable named **Counter**, enter @Counter in the expression that the For Loop container uses. If you include the namespace property on the variable, you must enclose the variable and namespace in brackets. For example, for a **Counter** variable in the **MyNamespace** namespace, type \[@MyNamespace::Counter\].  
  
 The variables that the For Loop container uses must be defined in the scope of the For Loop container or in the scope of any container that is higher in the package container hierarchy. For example, a For Loop container can use variables defined in its scope and also variables defined in package scope. For more information, see [Integration Services &#40;SSIS&#41; Variables](../Topic/Integration%20Services%20\(SSIS\)%20Variables.md) and [Use Variables in Packages](../../Topics\TopicNameNotContainA/Use-Variables-in-Packages.md).  
  
 The [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] expression grammar provides a complete set of operators and functions for implementing complex expressions used for evaluation, initialization, or assignment. For more information, see [Integration Services &#40;SSIS&#41; Expressions](../Topic/Integration%20Services%20\(SSIS\)%20Expressions.md).  
  
### To implement a For Loop container in a control flow  
  
1.  Add the For Loop container to the package. For more information, see [Add or Delete a Task or a Container in a Control Flow](../../Topics\TopicNameContainA/Add-or-Delete-a-Task-or-a-Container-in-a-Control-Flow.md).  
  
2.  Add tasks and containers to the For Loop container. For more information, see [Add or Delete a Task or a Container in a Control Flow](../../Topics\TopicNameContainA/Add-or-Delete-a-Task-or-a-Container-in-a-Control-Flow.md).  
  
3.  Connect tasks and containers in the For Loop container using precedence constraints. For more information, see [Connect Tasks and Containers by Using a Default Precedence Constraint](../../Topics\TopicNameContainA/Connect-Tasks-and-Containers-by-Using-a-Default-Precedence-Constraint.md).  
  
4.  Configure the For Loop container. For more information, see [Configure a For Loop Container](../../Topics\TopicNameContainA/Configure-a-For-Loop-Container.md).  
  
## See Also  
 [Add or Delete a Task or a Container in a Control Flow](../../Topics\TopicNameContainA/Add-or-Delete-a-Task-or-a-Container-in-a-Control-Flow.md)   
 [Group or Ungroup Components](../../Topics\TopicNameNotContainA/Group-or-Ungroup-Components.md)   
 [Connect Tasks and Containers by Using a Default Precedence Constraint](../../Topics\TopicNameContainA/Connect-Tasks-and-Containers-by-Using-a-Default-Precedence-Constraint.md)   
 [Add Enumeration to a Control Flow](../../Topics\TopicNameContainA/Add-Enumeration-to-a-Control-Flow.md)   
 [Control Flow](../../Topics\TopicNameNotContainA/Control-Flow.md)  
  
  