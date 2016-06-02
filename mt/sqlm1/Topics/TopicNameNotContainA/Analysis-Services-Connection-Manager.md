---
title: Analysis Services Connection Manager
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9f9cadad-a1d0-4db5-98f5-df5dbbec1be4
---
# Analysis Services Connection Manager
  An [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] connection manager enables a package to connect to a server that runs an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database or to an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project that provides access to cube and dimension data. You can only connect to an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project while developing packages in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)]. At run time, packages connect to the server and the database to which you deployed the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project.  
  
 Both tasks, such as the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] Execute DDL task and the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] Processing task, and destinations, such as the Data Mining Model Training destination, use an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] connection manager.  
  
 For more information about [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] databases, see [Multidimensional Model Databases &#40;SSAS&#41;](../Topic/Multidimensional%20Model%20Databases%20\(SSAS\).md).  
  
## Configuration of the Analysis Services Connection Manager  
 When you add an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] connection manager to a package, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] creates a connection manager that is resolved as an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] connection at run time, sets the connection manager properties, and adds the connection manager to the **Connections** collection on the package. The **ConnectionManagerType** property of the connection manager is set to **MSOLAP100**.  
  
 You can configure the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] connection manager in the following ways:  
  
-   Provide a connection string configured to meet the requirements of the Microsoft OLE Provider for Analysis Services provider.  
  
-   Specify the instance of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] or the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project to connect to.  
  
-   If you are connecting to an instance of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)], specify the authentication mode.  
  
-   Indicate whether the connection that is created from the connection manager is retained at run time.  
  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click one of the following topic:  
  
-   [Add Analysis Services Connection Manager Dialog Box UI Reference](../../Topics\TopicNameNotContainA/Add-Analysis-Services-Connection-Manager-Dialog-Box-UI-Reference.md)  
  
 For information about configuring a connection manager programmatically, see [ConnectionManager](assetId:///T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager) and [Adding Connections Programmatically](../Topic/Adding%20Connections%20Programmatically.md).  
  
  