---
title: ADO Connection Manager
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 490418bc-5ef1-41b8-a9c8-de38aa96e0f6
---
# ADO Connection Manager
  An ADO connection manager enables a package to connect to ActiveX Data Objects \(ADO\) objects, such as a recordset. This connection manager is typically used in custom tasks written in an earlier version of a language, such as Microsoft Visual Basic 6.0, or in custom tasks that are part of an existing application that uses ADO to connect to a data source.  
  
 When you add an ADO connection manager to a package, [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] creates a connection manager that will resolve to an ADO connection at run time, sets the connection manager properties, and adds the connection manager to the **Connections** collection on the package. The **ConnectionManagerType** property of the connection manager is set to **ADO**.  
  
## Troubleshooting the ADO Connection Manager  
 When being read by an ADO connection manager, certain [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] date data types will generate the results shown in the following table.  
  
|SQL Server Data type|Result|  
|--------------------------|------------|  
|**time**, **datetimeoffset**|The package fails unless the package uses parameterized SQL commands. To use parameterized SQL commands, use the Execute SQL Task in your package. For more information, see [Execute SQL Task](../../Topics\TopicNameNotContainA/Execute-SQL-Task.md) and [Parameters and Return Codes in the Execute SQL Task](../../Topics\TopicNameNotContainA/Parameters-and-Return-Codes-in-the-Execute-SQL-Task.md).|  
|**datetime2**|The ADO connection manager truncates the millisecond value.|  
  
> [!NOTE]  
>  For more information about [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] data types and how they map to [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] data types, see [Data Types &#40;Transact-SQL&#41;](../Topic/Data%20Types%20\(Transact-SQL\).md) and [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
## Configuring the ADO Connection Manager  
 You can configure an ADO connection manager in the following ways:  
  
-   Provide a specific connection string configured to meet the requirements of the selected provider.  
  
-   Depending on the provider, include the name of the data source to connect to.  
  
-   Provide security credentials as appropriate for the selected provider.  
  
-   Indicate whether the connection that is created from the connection manager is retained at run time.  
  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, click the following topic:  
  
-   [Configure OLE DB Connection Manager](../../Topics\TopicNameNotContainA/Configure-OLE-DB-Connection-Manager.md)  
  
 For information about configuring a connection manager programmatically, see [ConnectionManager](assetId:///T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager) and [Adding Connections Programmatically](../Topic/Adding%20Connections%20Programmatically.md).  
  
## See Also  
 [Integration Services &#40;SSIS&#41; Connections](../Topic/Integration%20Services%20\(SSIS\)%20Connections.md)  
  
  