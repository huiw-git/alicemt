---
title: SSIS Package Essentials
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b0c86c35-e3d3-4724-9a96-4087e9d74bf3
---
# SSIS Package Essentials
  A package is the object that implements [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] functionality to extract, transform, and load data. You create a package by using the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer in [!INCLUDE[ssBIDevStudio](../../Token\Other/ssBIDevStudio_md.md)]. You can also create a package by running the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard or the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] Connections Project Wizard. For more information, see [Create Packages in SQL Server Data Tools](../../Topics\TopicNameNotContainA/Create-Packages-in-SQL-Server-Data-Tools.md) and [SQL Server Import and Export Wizard](../../Topics\TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md).  
  
 A basic package includes the following elements:  
  
 **Control flow elements**  
 These required elements perform various functions, provide structure, and control the order in which elements run. The main control flow elements are tasks, containers, and precedence constraints. There must be at least one control flow element in a package.  
  
 For more information, see [Control Flow](../../Topics\TopicNameNotContainA/Control-Flow.md).  
  
 **Data flow elements**  
 These optional elements extract data, modify data, and load data into data sources. The main data flow elements are sources, transformations, and destinations. There does not have to be any data flow elements in package.  
  
 For more information, see [Data Flow](../../Topics\TopicNameNotContainA/Data-Flow.md).  
  
 For an example of how to create a basic package, see [Lesson 1: Create a Project and Basic Package with SSIS](../Topic/Lesson%201:%20Create%20a%20Project%20and%20Basic%20Package%20with%20SSIS.md).  
  
## Related Tasks  
  
-   [Create Packages in SQL Server Data Tools](../../Topics\TopicNameNotContainA/Create-Packages-in-SQL-Server-Data-Tools.md)  
  
-   [Add or Delete a Task or a Container in a Control Flow](../../Topics\TopicNameContainA/Add-or-Delete-a-Task-or-a-Container-in-a-Control-Flow.md)  
  
-   [Set the Properties of a Task or Container](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md)  
  
-   [Add or Delete a Component in a Data Flow](../../Topics\TopicNameContainA/Add-or-Delete-a-Component-in-a-Data-Flow.md)  
  
## Related Content  
  
1.  Video, [Creating a Basic Package \(SQL Server Video\)](http://go.microsoft.com/fwlink/?LinkId=131023), on MSDN.Microsoft.com  
  
## See Also  
 [Integration Services &#40;SSIS&#41; Packages](../Topic/Integration%20Services%20\(SSIS\)%20Packages.md)   
 [Precedence Constraints](../../Topics\TopicNameNotContainA/Precedence-Constraints.md)  
  
  