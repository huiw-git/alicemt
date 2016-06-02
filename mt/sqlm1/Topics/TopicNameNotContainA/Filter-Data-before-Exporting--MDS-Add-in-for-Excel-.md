---
title: Filter Data before Exporting (MDS Add-in for Excel)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9e30eae0-776b-4a09-aac3-0c0249d92ca5
---
# Filter Data before Exporting (MDS Add-in for Excel)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)], filter data when you want to limit the size or scope of data that you are exporting to Excel.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **Explorer** functional area.  
  
### To filter data before exporting  
  
1.  Open Excel and on the **Master Data** tab, connect to an MDS repository. For more information, see [Connect to an MDS Repository &#40;MDS Add-in for Excel&#41;](../Topic/Connect%20to%20an%20MDS%20Repository%20\(MDS%20Add-in%20for%20Excel\).md).  
  
2.  In the **Master Data Explorer** pane, select a model and version. The list of entities is populated.  
  
    -   If the **Master Data Explorer** pane is not visible, in the **Connect and Load** group, click **Show Explorer**.  
  
    -   If the **Master Data Explorer** pane is disabled, it is because the existing sheet already contains MDS\-managed data. To enable the pane, open a new worksheet.  
  
3.  In the **Master Data Explorer** pane, in the list of entities, click the entity you want to filter.  
  
4.  On the ribbon, in the **Connect and Load** group, click **Filter**.  
  
5.  Complete the **Filter** dialog box by selecting the attributes \(columns\) to display, setting the order of the columns, and if needed, filtering the data so fewer rows are returned. View the **Summary** pane for how much data will be returned. For more information, see [Filter Dialog Box &#40;MDS Add-in for Excel&#41;](../Topic/Filter%20Dialog%20Box%20\(MDS%20Add-in%20for%20Excel\).md).  
  
6.  Click **Load Data**. The sheet is populated with MDS\-managed data.  
  
    > [!NOTE]  
    >  -   Only the first one million members are loaded into Excel.  
    > -   In columns that are constrained lists \(domain\-based attributes\), by default only the first 25000 values are loaded.  
  
## Next Steps  
 [Import Data from Excel to Master Data Services &#40;MDS Add-in for Excel&#41;](../Topic/Import%20Data%20from%20Excel%20to%20Master%20Data%20Services%20\(MDS%20Add-in%20for%20Excel\).md)  
  
## See Also  
 [Overview: Exporting Data to Excel &#40;MDS Add-in for Excel&#41;](../Topic/Overview:%20Exporting%20Data%20to%20Excel%20\(MDS%20Add-in%20for%20Excel\).md)   
 [Filter Dialog Box &#40;MDS Add-in for Excel&#41;](../Topic/Filter%20Dialog%20Box%20\(MDS%20Add-in%20for%20Excel\).md)   
 [Reorder Columns &#40;MDS Add-in for Excel&#41;](../Topic/Reorder%20Columns%20\(MDS%20Add-in%20for%20Excel\).md)  
  
  