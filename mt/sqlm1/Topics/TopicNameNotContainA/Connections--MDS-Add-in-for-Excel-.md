---
title: Connections (MDS Add-in for Excel)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2f2b2f9d-7744-460e-83cd-56d34ea70ff0
---
# Connections (MDS Add-in for Excel)
  To download data in to the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)], you must first create a connection. A connection is how the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] web service knows which MDS database to connect to.  
  
 The connection string is usually the URL of the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application, for example http:\/\/contoso\/mds.  
  
 Each time you start Excel, you must connect to an MDS repository. The only exception is when the active spreadsheet already contains MDS\-managed data. In this case, a connection is automatically made each time you refresh or publish data in the sheet.  
  
 You can create multiple connections. The most recently\-accessed connection is considered the default.  
  
 Multiple users can be connected at the same time. However, conflicts can arise when multiple users attempt to publish the same data. For more information, see [Overview: Importing Data from Excel &#40;MDS Add-in for Excel&#41;](../Topic/Overview:%20Importing%20Data%20from%20Excel%20\(MDS%20Add-in%20for%20Excel\).md).  
  
## Connect Automatically and Load Frequently\-Used Data  
 If you want to always connect to the same server and load the same set of data, you can create shortcut query files, which contain connection and filter information. For more information about query files, see [Shortcut Query Files &#40;MDS Add-in for Excel&#41;](../Topic/Shortcut%20Query%20Files%20\(MDS%20Add-in%20for%20Excel\).md).  
  
## Data Quality Services  
 The [!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)] has Data Quality Services functionality to help you match data before publishing it to the MDS repository. When you make a connection, if a DQS database is installed on the same instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] as the MDS database, you will be able to view DQS buttons on the ribbon. If the DQS\_Main database does not exist on the instance, these buttons are not displayed and data quality functionality is not available.  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Create a connection to a [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database.|[Connect to an MDS Repository &#40;MDS Add-in for Excel&#41;](../Topic/Connect%20to%20an%20MDS%20Repository%20\(MDS%20Add-in%20for%20Excel\).md)|  
|Load MDS data into Excel.|[Export Data to Excel from Master Data Services](../../Topics\TopicNameNotContainA/Export-Data-to-Excel-from-Master-Data-Services.md)|  
|Filter MDS data before you load it into Excel.|[Filter Data before Exporting &#40;MDS Add-in for Excel&#41;](../Topic/Filter%20Data%20before%20Exporting%20\(MDS%20Add-in%20for%20Excel\).md)|  
  
## Related Content  
  
-   [Overview: Exporting Data to Excel &#40;MDS Add-in for Excel&#41;](../Topic/Overview:%20Exporting%20Data%20to%20Excel%20\(MDS%20Add-in%20for%20Excel\).md)  
  
-   [Shortcut Query Files &#40;MDS Add-in for Excel&#41;](../Topic/Shortcut%20Query%20Files%20\(MDS%20Add-in%20for%20Excel\).md)  
  
-   [Master Data Services Add-in for Microsoft Excel](../../Topics\TopicNameNotContainA/Master-Data-Services-Add-in-for-Microsoft-Excel.md)  
  
  