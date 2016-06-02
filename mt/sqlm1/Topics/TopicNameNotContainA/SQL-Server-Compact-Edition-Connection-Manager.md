---
title: SQL Server Compact Edition Connection Manager
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ba627d4d-41f4-49fc-a921-f534cde67770
---
# SQL Server Compact Edition Connection Manager
  A [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact connection manager enables a package to connect to a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact database. The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact destination that [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] includes uses this connection manager to load data into a table in a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact database.  
  
> [!NOTE]  
>  On a 64\-bit computer, you must run packages that connect to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact data sources in 32\-bit mode. The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact provider that [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] uses to connect to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact data sources is available only in a 32\-bit version.  
  
## Configuration the SQL Server Compact Edition Connection Manager  
 When you add a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact connection manager to a package, [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] creates a connection manager that will resolve to a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact connection at run time, sets the connection manager properties, and adds the connection manager to the **Connections** collection on the package.  
  
 The **ConnectionManagerType** property of the connection manager is set to **SQLMOBILE**.  
  
 You can configure the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact connection manager in the following ways:  
  
-   Provide a connection string that specifies the location of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact database.  
  
-   Provide a password for a password\-protected database.  
  
-   Specify the server on which the database is stored.  
  
-   Indicate whether the connection that is created from the connection manager is retained at run time.  
  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click one of the following topics:  
  
-   [SQL Server Compact Edition Connection Manager Editor &#40;Connection Page&#41;](../Topic/SQL%20Server%20Compact%20Edition%20Connection%20Manager%20Editor%20\(Connection%20Page\).md)  
  
-   [SQL Server Compact Edition Connection Manager Editor &#40;All Page&#41;](../Topic/SQL%20Server%20Compact%20Edition%20Connection%20Manager%20Editor%20\(All%20Page\).md)  
  
 For information about configuring a connection manager programmatically, see [ConnectionManager](assetId:///T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager) and [Adding Connections Programmatically](../Topic/Adding%20Connections%20Programmatically.md).  
  
  