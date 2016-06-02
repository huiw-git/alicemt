---
title: SMO Connection Manager
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d273f1fb-a6a8-4f2f-a5ff-55c2e3de4723
---
# SMO Connection Manager
  An SMO connection manager enables a package to connect to a SQL Management Object \(SMO\) server. The transfer tasks that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] includes use an SMO connection manager. For example, the Transfer Logins task that transfers [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] logins uses an SMO connection manager.  
  
 When you add an SMO connection manager to a package, [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] creates a connection manager that will resolve to an SMO connection at run time, sets the connection manager properties, and adds the connection manager to the **Connections** collection on the package. The **ConnectionManagerType** property of the connection manager is set to **SMOServer**.  
  
 You can configure an SMO connection manager in the following ways:  
  
-   Specify the name of a server on which [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is installed.  
  
-   Select the authentication mode for connecting to the server.  
  
## Configuration of the SMO Connection Manager  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, see [SMO Connection Manager Editor](../../Topics\TopicNameNotContainA/SMO-Connection-Manager-Editor.md).  
  
 For information about configuring a connection manager programmatically, see [ConnectionManager](assetId:///T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager) and [Adding Connections Programmatically](../Topic/Adding%20Connections%20Programmatically.md).  
  
## See Also  
 [Integration Services &#40;SSIS&#41; Connections](../Topic/Integration%20Services%20\(SSIS\)%20Connections.md)  
  
  