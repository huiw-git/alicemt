---
title: Sequence Container
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7731f91e-b8b3-4d96-a0d9-73f568547cb3
---
# Sequence Container
  The Sequence container defines a control flow that is a subset of the package control flow. Sequence containers group the package into multiple separate control flows, each containing one or more tasks and containers that run within the overall package control flow.  
  
 The Sequence container can include multiple tasks in addition to other containers. Adding tasks and containers to a Sequence container is similar to adding them to a package, except you drag the tasks and containers to the Sequence container instead of to the package container. If the Sequence container includes more than one task or container, you can connect them using precedence constraints just as you do in a package. For more information, see [Precedence Constraints](../../Topics\TopicNameNotContainA/Precedence-Constraints.md).  
  
 There are many benefits of using a Sequence container:  
  
-   Disabling groups of tasks to focus package debugging on one subset of the package control flow.  
  
-   Managing properties on multiple tasks in one location by setting properties on a Sequence container instead of on the individual tasks.  
  
     For example, you can set the **Disable** property of the Sequence container to **True** to disable all the tasks and containers in the Sequence container.  
  
-   Providing scope for variables that a group of related tasks and containers use.  
  
-   Grouping many tasks so you can more easily managed them by collapsing and expanding the Sequence container.  
  
     You can also create task groups, which expand and collapse using the **Group** box. However, the **Group** box is a design\-time feature that has no properties or run\-time behavior. For more information, see [Group or Ungroup Components](../../Topics\TopicNameNotContainA/Group-or-Ungroup-Components.md)  
  
-   Set a transaction attribute on the Sequence container to define a transaction for a subset of the package control flow. In this way, you can manage transactions at a more granular level.  
  
     For example, if a Sequence container includes two related tasks, one task that deletes data in a table and another task that inserts data into a table, you can configure a transaction to ensure that the delete action is rolled back if the insert action fails. For more information, see [Integration Services Transactions](../../Topics\TopicNameNotContainA/Integration-Services-Transactions.md).  
  
## Configuration of the Sequence Container  
 The Sequence container has no custom user interface and you can configure it only in the **Properties** window of [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] or programmatically.  
  
 For information about programmatically setting these properties, see documentation for the **T:Microsoft.SqlServer.Dts.Runtime.Sequence** class in the Developer Guide.  
  
## Related Tasks  
 For information about how to set properties of the component in the [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], see [Set the Properties of a Task or Container](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md).  
  
## See Also  
 [Add or Delete a Task or a Container in a Control Flow](../../Topics\TopicNameContainA/Add-or-Delete-a-Task-or-a-Container-in-a-Control-Flow.md)   
 [Connect Tasks and Containers by Using a Default Precedence Constraint](../../Topics\TopicNameContainA/Connect-Tasks-and-Containers-by-Using-a-Default-Precedence-Constraint.md)   
 [Integration Services Containers](../../Topics\TopicNameNotContainA/Integration-Services-Containers.md)  
  
  