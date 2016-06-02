---
title: Shortcut Query Files (MDS Add-in for Excel)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1ba0219a-6c40-41fa-aff9-8c8f41ef3220
---
# Shortcut Query Files (MDS Add-in for Excel)
  In the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)], use shortcut query files to quickly connect and load frequently\-used data. You can also use them when you want to share MDS data with others. Instead of saving the worksheet and emailing it, you should save a shortcut query file and email that instead. This ensures that you are both connecting to the MDS repository to get the latest data.  
  
 Shortcut query files are XML files that contain information about:  
  
-   The MDS repository connection.  
  
-   The model, version, and entity.  
  
-   Any filters that were applied when the shortcut was created.  
  
-   The left\-to\-right order of the columns when the shortcut was created.  
  
 You can save these files in a list and choose from them when you open the Add\-in. You can export them to your computer or to a shared location, or you can send them to others.  
  
 There are two ways to open shortcut query files: you can import them, or you can double\-click them to open them automatically by the QueryOpener application.  
  
## QueryOpener Application  
 All users who install the [!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)] have an application called QueryOpener installed. This application is used to open shortcut query files in the [!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)]. If you double\-click a shortcut query file, this application is automatically used to open the file in the Add\-in.  
  
 When you open a shortcut query file with this application, you are prompted to make the connection a “safe” connection, which means you trust content from this location. \(You can make a connection safe by selecting **Always allow connection to this address** in the prompt window.\) Each time you mark a connection as safe, it is added to a list. If you want to clear this list, open the **Settings** dialog box and in the **Servers Added to Safe List** section, click **Clear All**.  
  
 The default location for the application is *drive*:\\Program Files\\Microsoft SQL Server\\130\\Master Data Services\\Excel Add\-In\\Microsoft.MasterDataServices.QueryOpener.exe.  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Save the contents of the active worksheet as a shortcut query file.|[Save a Shortcut Query File &#40;MDS Add-in for Excel&#41;](../Topic/Save%20a%20Shortcut%20Query%20File%20\(MDS%20Add-in%20for%20Excel\).md)|  
|Email a shortcut query file that represents the contents of the active worksheet.|[Email a Shortcut Query File &#40;MDS Add-in for Excel&#41;](../Topic/Email%20a%20Shortcut%20Query%20File%20\(MDS%20Add-in%20for%20Excel\).md)|  
  
## Related Content  
  
-   [Connections &#40;MDS Add-in for Excel&#41;](../Topic/Connections%20\(MDS%20Add-in%20for%20Excel\).md)  
  
-   [Master Data Services Add-in for Microsoft Excel](../../Topics\TopicNameNotContainA/Master-Data-Services-Add-in-for-Microsoft-Excel.md)  
  
-   [Security &#40;Master Data Services&#41;](../Topic/Security%20\(Master%20Data%20Services\).md)  
  
  