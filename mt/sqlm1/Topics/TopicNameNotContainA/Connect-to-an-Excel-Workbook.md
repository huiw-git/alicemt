---
title: Connect to an Excel Workbook
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d9746318-3669-4ce2-bbb0-4a1bd471c9dd
---
# Connect to an Excel Workbook
  To connect an [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package to a Microsoft Office Excel workbook requires an Excel connection manager.  
  
 You can create these connection managers from either the Connection Managers area in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or from the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard.  
  
 **Providers and drivers for Microsoft Excel and Access files**  
  
 You may have to download the OLE DB providers and drivers for Microsoft Office files if they're not already installed. Later versions of the provider can open files created by earlier versions of Excel.  
  
 If the computer has a 32\-bit version of Office, then you have to install the 32\-bit version of the drivers, and you also have to ensure that you run the wizard or the Integration Services package that it creates in 32\-bit mode.  
  
|Microsoft Office version|Download|  
|------------------------------|--------------|  
|2007|[2007 Office System Driver: Data Connectivity Components](https://www.microsoft.com/en-us/download/details.aspx?id=23734)|  
|2010|[Microsoft Access 2010 Runtime](https://www.microsoft.com/en-us/download/details.aspx?id=10910)|  
|2013|[Microsoft Access 2013 Runtime](http://www.microsoft.com/en-us/download/details.aspx?id=39358)|  
  
### To create an Excel connection manager from the Connection Managers area  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the package.  
  
2.  In the **Connections Managers** area, right\-click anywhere in the area, and then select **New Connection**.  
  
3.  In the **Add SSIS Connection Manager** dialog box, select **Excel**, and then configure the connection manager.  
  
     For information about the configuration options that are available for this connection manager, see [Excel Connection Manager Editor](../../Topics\TopicNameNotContainA/Excel-Connection-Manager-Editor.md).  
  
### To create an Excel connection from the SQL Server Import and Export Wizard  
  
1.  Start the 32\-bit version of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard.  
  
2.  On the **Choose a Data Source** page, for **Data Source**, select **Microsoft Excel**, and then configure the Excel connection.  
  
     For information about the configuration options that are available for this connection type, see [Excel Connection Manager Editor](../../Topics\TopicNameNotContainA/Excel-Connection-Manager-Editor.md).  
  
## See Also  
 [Connect to an Access Database](../../Topics\TopicNameNotContainA/Connect-to-an-Access-Database.md)  
  
  