---
title: Integration Services Tasks
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 75c8901d-6966-4af3-abe5-10af6dd9313b
---
# Integration Services Tasks
  Tasks are control flow elements that define units of work that are performed in a package control flow. An [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package is made up of one or more tasks. If the package contains more than one task, they are connected and sequenced in the control flow by precedence constraints.  
  
 You can also write custom tasks using a programming language that supports COM, such as Visual Basic, or a .NET programming language, such as C\#.  
  
 The [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, the graphical tool in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] for working with packages, provides the design surface for creating package control flow, and provides custom editors for configuring tasks. You can also program the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] object model to create packages programmatically.  
  
## Types of Tasks  
 [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] includes the following types of tasks.  
  
 Data Flow Task  
 The task that runs data flows to extract data, apply column level transformations, and load data.  
  
 Data Preparation Tasks  
 These tasks do the following processes: copy files and directories; download files and data; run Web methods; apply operations to XML documents; and profile data for cleansing.  
  
 Workflow Tasks  
 The tasks that communicate with other processes to run packages, run programs or batch files, send and receive messages between packages, send e\-mail messages, read Windows Management Instrumentation \(WMI\) data, and watch for WMI events.  
  
 SQL Server Tasks  
 The tasks that access, copy, insert, delete, and modify [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] objects and data.  
  
 Scripting Tasks  
 The tasks that extend package functionality by using scripts.  
  
 Analysis Services Tasks  
 The tasks that create, modify, delete, and process [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] objects.  
  
 Maintenance Tasks  
 The tasks that perform administrative functions such as backing up and shrinking [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] databases, rebuilding and reorganizing indexes, and running [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent jobs.  
  
 Custom Tasks  
 Additionally, you can write custom tasks using a programming language that supports COM, such as Visual Basic, or a .NET programming language, such as C\#. If you want to access your custom task in the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, you can create and register a user interface for the task. For more information, see [Developing a Custom Task](../Topic/Developing%20a%20Custom%20Task.md).  
  
## Configuration of Tasks  
 An [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package can contain a single task, such as an Execute SQL task that deletes records in a database table when the package runs. However, packages typically contain several tasks, and each task is set to run within the context of the package control flow. Event handlers, which are workflows that run in response to run\-time events, can also have tasks.  
  
 For more information about adding a task to a package using [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, see [Add or Delete a Task or a Container in a Control Flow](../../Topics\TopicNameContainA/Add-or-Delete-a-Task-or-a-Container-in-a-Control-Flow.md).  
  
 For more information about adding a task to a package programmatically, see [Adding Tasks Programmatically](../Topic/Adding%20Tasks%20Programmatically.md).  
  
 Each task can be configured individually using the custom dialog boxes for each task that [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer provides, or the Properties window included in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)]. A package can include multiple tasks of the same type—for example, six Execute SQL tasks—and each task can be configured differently. For more information, see [Set the Properties of a Task or Container](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md).  
  
## Tasks Connections and Groups  
 If the task contains more than one task, they are connected and sequenced in the control flow by precedence constraints. For more information, see [Precedence Constraints](../../Topics\TopicNameNotContainA/Precedence-Constraints.md).  
  
 Tasks can be grouped together and performed as a single unit of work, or repeated in a loop. For more information, see [Foreach Loop Container](../../Topics\TopicNameNotContainA/Foreach-Loop-Container.md), [For Loop Container](../../Topics\TopicNameNotContainA/For-Loop-Container.md), and [Sequence Container](../../Topics\TopicNameNotContainA/Sequence-Container.md).  
  
## Related Tasks  
 [Add or Delete a Task or a Container in a Control Flow](../../Topics\TopicNameContainA/Add-or-Delete-a-Task-or-a-Container-in-a-Control-Flow.md)  
  
  