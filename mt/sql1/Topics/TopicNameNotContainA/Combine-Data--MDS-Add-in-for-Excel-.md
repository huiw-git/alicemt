---
title: "Combine Data (MDS Add-in for Excel)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a867dc15-5a0d-457c-8304-ac323bcf9377
caps.latest.revision: 7
caps.handback.revision: 0
manager: jhubbard
---
# Combine Data (MDS Add-in for Excel)
In the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Topics/TopicNameContainA/tokens/ssMDSXLS_md.md)], combine data from two worksheets when you want to compare data before publishing. In this procedure, you combine data from a two worksheets into one. Then you can perform further comparisons and determine which data, if any, to publish to the MDS repository.  
  
## Prerequisites  
  
-   You must have a worksheet that contains MDS-managed data. For more information, see [Export Data to Excel from Master Data Services](../../Topics/TopicNameNotContainA/Export-Data-to-Excel-from-Master-Data-Services.md).  
  
-   You must have a worksheet that contains data you want to combine with MDS-managed data. This sheet must have a header row.  
  
### To combine non-managed data into an MDS-managed sheet  
  
1.  On the sheet that contains MDS-managed data, in the **Publish and Validate** group, click **Combine Data**.  
  
2.  In the **Combine Data** dialog box, next to the **Range to combine with MDS data** text box, click the icon. The dialog box contracts.  
  
3.  Click the sheet that contains the data you want to combine.  
  
4.  Highlight all cells on the sheet that you want to combine, including the header row.  
  
5.  In the **Combine Data** dialog box, click the icon. The dialog box expands.  
  
6.  For a column listed for the MDS entity, select a column under **Corresponding Column**. All MDS columns do not need corresponding columns.  
  
7.  Click **Combine**. A **SOURCE** column is displayed, indicating whether the data is from MDS or an external source.  
  
## Next Steps  
  
-   To find similarities between the MDS-managed and external data, see [Match Similar Data (MDS Add-in for Excel)](../../Topics/TopicNameNotContainA/Match-Similar-Data--MDS-Add-in-for-Excel-.md).  
  
## See Also  
 [Overview: Exporting Data to Excel (MDS Add-in for Excel)](../Topic/Overview:%20Exporting%20Data%20to%20Excel%20\(MDS%20Add-in%20for%20Excel\).md)   
 [Data Quality Matching in the MDS Add-in for Excel](../../Topics/TopicNameNotContainA/Data-Quality-Matching-in-the-MDS-Add-in-for-Excel.md)