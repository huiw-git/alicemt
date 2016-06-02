---
title: Data Quality Matching Columns (MDS Add-in for Excel)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f683fdc6-0d4c-4793-8143-567616cb2094
---
# Data Quality Matching Columns (MDS Add-in for Excel)
  In the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)], after you match data, in the **Data Quality** group on the ribbon, you can click **Show Details** to display columns that provide matching details.  
  
 The following table shows the columns that are displayed when matching data.  
  
|Name|Description|  
|----------|-----------------|  
|**CLUSTER\_ID**|A unique identifier used to group similar records. All rows that are similar have the same **CLUSTER\_ID**. If no **CLUSTER\_ID** is displayed for a row, then no similar records were found.|  
|**RECORD\_ID**|A unique identifier used to identify records. Similar to the Code value stored in the MDS repository, it is a value used to identify a record. It is generated automatically each time matching takes place.|  
|**PIVOT\_MARK**|An arbitrary record that other records are compared to; it does not have a score value.|  
|**SCORE**|Represents how similar the records in the group are to the pivot record. This score is determined by DQS. If no score is displayed, either the record is the pivot for other records, or no matches were found.|  
  
## See Also  
 [Data Quality Matching in the MDS Add-in for Excel](../../Topics\TopicNameNotContainA/Data-Quality-Matching-in-the-MDS-Add-in-for-Excel.md)   
 [Match Similar Data &#40;MDS Add-in for Excel&#41;](../Topic/Match%20Similar%20Data%20\(MDS%20Add-in%20for%20Excel\).md)   
 [Data Matching](../../Topics\TopicNameNotContainA/Data-Matching.md)  
  
  