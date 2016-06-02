---
title: ADO.NET Connection Manager
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fc5daa2f-0159-4bda-9402-c87f1035a96f
---
# ADO.NET Connection Manager
  An [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] connection manager enables a package to access data sources by using a .NET provider. This connection manager is typically used to access data sources such as [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], and also data sources exposed through OLE DB and XML in custom tasks that are written in managed code by using a language such C\#.  
  
 When you add an [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] connection manager to a package, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] creates a connection manager that is resolved as an [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] connection at run time, sets the connection manager properties, and adds the connection manager to the **Connections** collection on the package.  
  
 The **ConnectionManagerType** property of the connection manager is set to **ADO.NET**. The value of **ConnectionManagerType** is qualified to include the name of the .NET provider that the connection manager uses.  
  
## ADO.NET Connection Manager Troubleshooting  
 You can log the calls that the [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] connection manager makes to external data providers. You can use this logging capability to troubleshoot the connections that the [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] connection manager makes to external data sources. To log the calls that the [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] connection manager makes to external data providers, enable package logging and select the **Diagnostic** event at the package level. For more information, see [Troubleshooting Tools for Package Execution](../../Topics\TopicNameNotContainA/Troubleshooting-Tools-for-Package-Execution.md).  
  
 When being read by an [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] connection manager, data of certain [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] date data types will generate the results shown in the following table.  
  
|SQL Server data type|Result|  
|--------------------------|------------|  
|**time**, **datetimeoffset**|The package fails unless the package uses parameterized SQL commands. To use parameterized SQL commands, use the Execute SQL Task in your package. For more information, see [Execute SQL Task](../../Topics\TopicNameNotContainA/Execute-SQL-Task.md) and [Parameters and Return Codes in the Execute SQL Task](../../Topics\TopicNameNotContainA/Parameters-and-Return-Codes-in-the-Execute-SQL-Task.md).|  
|**datetime2**|The [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] connection manager truncates the millisecond value.|  
  
> [!NOTE]  
>  For more information about [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] data types and how they map to [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] data types, see [Data Types &#40;Transact-SQL&#41;](../Topic/Data%20Types%20\(Transact-SQL\).md) and [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
## ADO.NET Connection Manager Configuration  
 You can configure an [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] connection manager in the following ways:  
  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
-   Provide a specific connection string configured to meet the requirements of the selected .NET provider.  
  
-   Depending on the provider, include the name of the data source to connect to.  
  
-   Provide security credentials as appropriate for the selected provider.  
  
-   Indicate whether the connection that is created from the connection manager is retained at run time.  
  
 Many of configuration options of the [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] connection manager depend on the .NET provider that the connection manager uses.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click one of the following topic:  
  
-   [Configure ADO.NET Connection Manager](../../Topics\TopicNameNotContainA/Configure-ADO.NET-Connection-Manager.md)  
  
 For information about configuring a connection manager programmatically, see [ConnectionManager](assetId:///T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager) and [Adding Connections Programmatically](../Topic/Adding%20Connections%20Programmatically.md).  
  
## See Also  
 [Integration Services &#40;SSIS&#41; Connections](../Topic/Integration%20Services%20\(SSIS\)%20Connections.md)  
  
  