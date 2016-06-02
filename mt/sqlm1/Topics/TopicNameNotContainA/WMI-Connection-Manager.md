---
title: WMI Connection Manager
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fbfa4ba7-3d0d-4d6b-94ad-50741a88d03d
---
# WMI Connection Manager
  A WMI connection manager enables a package to use Windows Management Instrumentation \(WMI\) to manage information in an enterprise environment. The Web Service task that [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] includes uses a WMI connection manager.  
  
 When you add a WMI connection manager to a package, [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] creates a connection manager that that will resolve to a WMI connection at run time, sets the connection manager properties, and adds the connection manager to the **Connections** collection on the package. The **ConnectionManagerType** property of the connection manager is set to **WMI**.  
  
## Configuration of the WMI Connection Manager  
 You can configure a WMI connection manager in the following ways:  
  
-   Specify the name of a server.  
  
-   Specify a namespace on the server.  
  
-   Select the authentication mode for connecting to the server.  
  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, see [WMI Connection Manager Editor](../../Topics\TopicNameNotContainA/WMI-Connection-Manager-Editor.md).  
  
 For information about configuring a connection manager programmatically, see [ConnectionManager](assetId:///T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager) and [Adding Connections Programmatically](../Topic/Adding%20Connections%20Programmatically.md).  
  
## See Also  
 [Web Service Task](../../Topics\TopicNameNotContainA/Web-Service-Task.md)   
 [Integration Services &#40;SSIS&#41; Connections](../Topic/Integration%20Services%20\(SSIS\)%20Connections.md)  
  
  