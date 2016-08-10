---
title: "Overview: Exporting Data to Excel (MDS Add-in for Excel)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b628548b-982b-4e45-abf4-c8e83e3ab1c2
caps.latest.revision: 11
caps.handback.revision: 0
manager: jhubbard
---
# Overview: Exporting Data to Excel (MDS Add-in for Excel)
In the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Topics/TopicNameContainA/tokens/ssMDSXLS_md.md)], you must export data from the MDS repository into an active Excel worksheet before you can work with it. When you are done working with the data, import it to the MDS repository so other users can share it.  
  
 The data you can export  is limited to the data you have permission to access. Permission to access data is set in the [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)] web application or set programmatically.  
  
 When you export  large amounts of data, you can set warnings that are displayed when the data that might take a long time to load. To do this, in the **Options** group, click **Settings**. On the **Data** tab, select the **Display filter warning for large data sets**.  
  
> [!WARNING]  
>  An MDS-enabled workbook must be opened and updated only in Excel with the MDS Add-in for Excel. Opening an MDS-enabled workbook in Excel on a computer in which the MDS Excel Add-in is not installed is not supported, and could cause corruption of the workbook file. If you want to share data with someone else, email a shortcut query file to them, rather than saving the worksheet and emailing it. For more information on the query, see [Email a Shortcut Query File (MDS Add-in for Excel)](../../Topics/TopicNameContainA/Email-a-Shortcut-Query-File--MDS-Add-in-for-Excel-.md).  
  
## Filtering Data  
 You can filter data before exporting to limit the amount of data that you’re going to download. This includes choosing which attributes (columns) you want to load, the order you want to display the attributes, and the members (rows of data) you want to work with. For more info see [Filter Data before Exporting (MDS Add-in for Excel)](../../Topics/TopicNameNotContainA/Filter-Data-before-Exporting--MDS-Add-in-for-Excel-.md).  
  
## Connect Automatically and Load Frequently-Used Data  
 If you want to always connect to the same server and export the same set of data, you can create shortcut query files, which contain connection and filter information. For more information about query files, see [Shortcut Query Files (MDS Add-in for Excel)](../../Topics/TopicNameNotContainA/Shortcut-Query-Files--MDS-Add-in-for-Excel-.md).  
  
## Refreshing Data  
 Data in the MDS repository may be updated by other users after you export it. You can retrieve this data without losing changes you’ve made to non-MDS data. For more information, see [Refreshing Data (MDS Add-in for Excel)](../../Topics/TopicNameNotContainA/Refreshing-Data--MDS-Add-in-for-Excel-.md).  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Filter MDS data before you load it into Excel.|[Filter Data before Exporting (MDS Add-in for Excel)](../../Topics/TopicNameNotContainA/Filter-Data-before-Exporting--MDS-Add-in-for-Excel-.md)|  
|Load MDS data into Excel.|[Export Data to Excel from Master Data Services](../../Topics/TopicNameNotContainA/Export-Data-to-Excel-from-Master-Data-Services.md)|  
|Change the order of columns before you download data.|[Reorder Columns (MDS Add-in for Excel)](../../Topics/TopicNameNotContainA/Reorder-Columns--MDS-Add-in-for-Excel-.md)|  
  
## Related Content  
  
-   [Connections (MDS Add-in for Excel)](../../Topics/TopicNameNotContainA/Connections--MDS-Add-in-for-Excel-.md)  
  
-   [Shortcut Query Files (MDS Add-in for Excel)](../../Topics/TopicNameNotContainA/Shortcut-Query-Files--MDS-Add-in-for-Excel-.md)  
  
-   [Master Data Services Add-in for Microsoft Excel](../../Topics/TopicNameNotContainA/Master-Data-Services-Add-in-for-Microsoft-Excel.md)  
  
-   [Security (Master Data Services)](../../Topics/TopicNameNotContainA/Security--Master-Data-Services-.md)