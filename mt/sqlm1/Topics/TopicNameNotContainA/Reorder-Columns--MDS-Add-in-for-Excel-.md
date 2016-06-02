---
title: Reorder Columns (MDS Add-in for Excel)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ac00462e-c0f7-4b8d-86f2-d9eda2598a15
---
# Reorder Columns (MDS Add-in for Excel)
  In the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)], you can reorder columns by filtering the list before loading.  
  
 When you reorder attributes in the **Filter** dialog box, the data is loaded into Excel with the new order. However, the next time that you filter the attribute data, the order will revert to the order in the original design. To change the order permanently, an administrator should change the order in the **System Administration** area of Master Data Manager. For more information, see [Change the Order of Attributes](../../Topics\TopicNameNotContainA/Change-the-Order-of-Attributes.md).  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **Explorer** functional area.  
  
### To reorder MDS\-managed columns  
  
1.  Open Excel and on the **Master Data** tab, connect to an MDS repository. For more information, see [Connect to an MDS Repository &#40;MDS Add-in for Excel&#41;](../Topic/Connect%20to%20an%20MDS%20Repository%20\(MDS%20Add-in%20for%20Excel\).md).  
  
2.  In the **Master Data Explorer** pane, select a model and version. The list of entities is populated.  
  
    -   If the **Master Data Explorer** pane is not visible, in the **Connect and Load** group, click **Show Explorer**.  
  
    -   If the **Master Data Explorer** pane is disabled, it is because the existing sheet already contains MDS\-managed data. To enable the pane, open a new worksheet.  
  
3.  In the **Master Data Explorer** pane, click an entity.  
  
4.  In the **Connect and Load** group, click **Filter**.  
  
5.  In the **Filter** dialog box, in the **Columns** section, in the list of attributes, click the attribute you want to move.  
  
6.  To the right of the list, click the **Up** or **Down** arrow to move the attribute left and right in the worksheet.  
  
7.  Repeat step 7 for each attribute until the top\-to\-bottom order represents the left\-to\-right order you want in the worksheet.  
  
8.  Click **Load Data**. The sheet is populated with MDS\-managed data and the columns are displayed in the order you specified.  
  
## See Also  
 [Overview: Exporting Data to Excel &#40;MDS Add-in for Excel&#41;](../Topic/Overview:%20Exporting%20Data%20to%20Excel%20\(MDS%20Add-in%20for%20Excel\).md)  
  
  