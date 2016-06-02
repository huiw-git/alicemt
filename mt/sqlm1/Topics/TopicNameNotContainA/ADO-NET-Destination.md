---
title: ADO NET Destination
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cb883990-d875-4d8b-b868-45f9f15ebeae
---
# ADO NET Destination
  The ADO NET destination loads data into a variety of [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)]\-compliant databases that use a database table or view. You have the option of loading this data into an existing table or view, or you can create a new table and load the data into the new table.  
  
 You can use the ADO NET destination to connect to [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssSDSFull](../../Token\Other/ssSDSfull_md.md)]. Connecting to [!INCLUDE[ssSDS](../../Token\Other/ssSDS_md.md)] by using OLE DB is not supported. For more information about [!INCLUDE[ssSDS](../../Token\Other/ssSDS_md.md)], see [General Guidelines and Limitations \(Windows Azure SQL Database\)](http://go.microsoft.com/fwlink/?LinkId=248228).  
  
## Troubleshooting the ADO NET Destination  
 You can log the calls that the ADO NET destination makes to external data providers. You can use this logging capability to troubleshoot the saving of data to external data sources that the ADO NET destination performs. To log the calls that the ADO NET destination makes to external data providers, enable package logging and select the **Diagnostic** event at the package level. For more information, see [Troubleshooting Tools for Package Execution](../../Topics\TopicNameNotContainA/Troubleshooting-Tools-for-Package-Execution.md).  
  
## Configuring the ADO NET Destination  
 This destination uses an [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] connection manager to connect to a data source and the connection manager specifies the [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] provider to use. For more information, see [ADO.NET Connection Manager](../../Topics\TopicNameNotContainA/ADO.NET-Connection-Manager.md).  
  
 An ADO NET destination includes mappings between input columns and columns in the destination data source. You do not have to map input columns to all destination columns. However, the properties of some destination columns can require the mapping of input columns. Otherwise, errors might occur. For example, if a destination column does not allow for null values, you must map an input column to that destination column. In addition, the data types of mapped columns must be compatible. For example, you cannot map an input column with a string data type to a destination column with a numeric data type if the [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] provider does not support this mapping.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] does not support inserting text into columns whose data type is set to image. For more information about [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] data types, see [Data Types &#40;Transact-SQL&#41;](../Topic/Data%20Types%20\(Transact-SQL\).md).  
  
> [!NOTE]  
>  The ADO NET destination does not support mapping an input column whose type is set to DT\_DBTIME to a database column whose type is set to datetime. For more information about [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] data types, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
 The ADO NET destination has one regular input and one error output.  
  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in the **ADO NET Destination Editor** dialog box, click one of the following topics:  
  
-   [ADO NET Destination Editor &#40;Connection Manager Page&#41;](../Topic/ADO%20NET%20Destination%20Editor%20\(Connection%20Manager%20Page\).md)  
  
-   [ADO NET Destination Editor &#40;Mappings Page&#41;](../Topic/ADO%20NET%20Destination%20Editor%20\(Mappings%20Page\).md)  
  
-   [ADO NET Destination Editor &#40;Error Output Page&#41;](../Topic/ADO%20NET%20Destination%20Editor%20\(Error%20Output%20Page\).md)  
  
 The **Advanced Editor** dialog box reflects the properties that can be set programmatically. For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:  
  
-   [Common Properties](../../Topics\TopicNameNotContainA/Common-Properties.md)  
  
-   [ADO NET Custom Properties](../../Topics\TopicNameNotContainA/ADO-NET-Custom-Properties.md)  
  
 For more information about how to set properties, see [Set the Properties of a Data Flow Component](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Data-Flow-Component.md).  
  
  