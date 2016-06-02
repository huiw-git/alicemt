---
title: ODBC Connection Manager
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e8c77aa7-6772-485e-918e-cef9eeb18c58
---
# ODBC Connection Manager
  An ODBC connection manager enables a package to connect to a variety of database management systems using the Open Database Connectivity specification \(ODBC\).  
  
 When you add an ODBC connection to a package and set the connection manager properties, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] creates a connection manager and adds the connection manager to the **Connections** collection of the package. At run time the connection manager is resolved as a physical ODBC connection.  
  
 The **ConnectionManagerType** property of the connection manager is set to **ODBC**.  
  
 You can configure the ODBC connection manager in the following ways:  
  
-   Provide a connection string that references a user or system data source name.  
  
-   Specify the server to connect to.  
  
-   Indicate whether the connection is retained at run time.  
  
## Configuration of the ODBC Connection Manager  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click one of the following topic:  
  
-   [ODBC Connection Manager UI Reference](../../Topics\TopicNameNotContainA/ODBC-Connection-Manager-UI-Reference.md)  
  
 For information about configuring a connection manager programmatically, see [ConnectionManager](assetId:///T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager) and [Adding Connections Programmatically](../Topic/Adding%20Connections%20Programmatically.md).  
  
## See Also  
 [Integration Services &#40;SSIS&#41; Connections](../Topic/Integration%20Services%20\(SSIS\)%20Connections.md)  
  
  