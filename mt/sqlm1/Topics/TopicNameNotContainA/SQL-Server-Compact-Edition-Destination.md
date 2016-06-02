---
title: SQL Server Compact Edition Destination
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 697742ba-cc14-414d-8187-1845ad0dd99b
---
# SQL Server Compact Edition Destination
  The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact destination writes data to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact databases.  
  
> [!NOTE]  
>  On a 64\-bit computer, you must run packages that connect to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact data sources in 32\-bit mode. The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact provider that [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] uses to connect to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact data sources is available only in a 32\-bit version.  
  
 You configure the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact destination by specifying the name of the table into which the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact destination inserts the data. The custom property TableName of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact destination contains the table name.  
  
 This destination uses an [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact connection manager to connect to a data source, and the connection manager specifies the OLE DB provider to use. For more information, see [SQL Server Compact Edition Connection Manager](../../Topics\TopicNameNotContainA/SQL-Server-Compact-Edition-Connection-Manager.md).  
  
 The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact destination includes the TableName custom property, which can be updated by a property expression when the package is loaded. For more information, see [Integration Services &#40;SSIS&#41; Expressions](../Topic/Integration%20Services%20\(SSIS\)%20Expressions.md), [Use Property Expressions in Packages](../../Topics\TopicNameNotContainA/Use-Property-Expressions-in-Packages.md), and [SQL Server Compact Edition Destination Custom Properties](../../Topics\TopicNameNotContainA/SQL-Server-Compact-Edition-Destination-Custom-Properties.md).  
  
 The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Compact destination has one input and does not support an error output.  
  
## Configuration of the SQL Server Compact Edition Destination  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 The **Advanced Editor** dialog box reflects the properties that can be set programmatically. For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:  
  
-   [Common Properties](../../Topics\TopicNameNotContainA/Common-Properties.md)  
  
-   [SQL Server Destination Custom Properties](../../Topics\TopicNameNotContainA/SQL-Server-Destination-Custom-Properties.md)  
  
## Related Tasks  
 For more information about how to set properties of this component, see [Set the Properties of a Data Flow Component](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Data-Flow-Component.md).  
  
## See Also  
 [Data Flow](../../Topics\TopicNameNotContainA/Data-Flow.md)  
  
  