---
title: Excel Connection Manager
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 667419f2-74fb-4b50-b963-9197d1368cda
---
# Excel Connection Manager
  An Excel connection manager enables a package to connect to an existing [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Excel workbook file. The Excel source and the Excel destination that [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] includes use the Excel connection manager.  
  
 When you add an Excel connection manager to a package, [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] creates a connection manager that is resolved as an Excel connection at run time, sets the connection manager properties, and adds the connection manager to the **Connections** collection on the package.  
  
 The **ConnectionManagerType** property of the connection manager is set to **EXCEL**.  
  
## Configuration of the Excel Connection Manager  
 You can configure the Excel connection manager in the following ways:  
  
-   Specify the path of the Excel workbook file.  
  
    > [!NOTE]  
    >  You cannot connect to a password\-protected Excel file.  
  
-   Specify the version of Excel that was used to create the file.  
  
-   Indicate whether the first row of accessed data in the selected worksheets or ranges contains column names.  
  
 If the Excel connection manager is used by an Excel source, the column names are included with the extracted data. If it is used by an Excel destination, the column names are included in the written data.  
  
 For more information about the behavior of Excel sources and Excel destinations, see [Excel Source](../../Topics\TopicNameNotContainA/Excel-Source.md) and [Excel Destination](../../Topics\TopicNameNotContainA/Excel-Destination.md).  
  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, see [Excel Connection Manager Editor](../../Topics\TopicNameNotContainA/Excel-Connection-Manager-Editor.md).  
  
 For information about configuring a connection manager programmatically, see [ConnectionManager](assetId:///T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager) and [Adding Connections Programmatically](../Topic/Adding%20Connections%20Programmatically.md).  
  
 For information about looping through a group of Excel files, see [Loop through Excel Files and Tables by Using a Foreach Loop Container](../../Topics\TopicNameContainA/Loop-through-Excel-Files-and-Tables-by-Using-a-Foreach-Loop-Container.md).  
  
## Related Tasks  
  
-   [Loop through Excel Files and Tables by Using a Foreach Loop Container](../../Topics\TopicNameContainA/Loop-through-Excel-Files-and-Tables-by-Using-a-Foreach-Loop-Container.md)  
  
-   [Connect to an Excel Workbook](../../Topics\TopicNameNotContainA/Connect-to-an-Excel-Workbook.md)  
  
  