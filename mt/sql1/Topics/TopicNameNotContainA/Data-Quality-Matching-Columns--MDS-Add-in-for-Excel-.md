---
title: "Data Quality Matching Columns (MDS Add-in for Excel)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f683fdc6-0d4c-4793-8143-567616cb2094
caps.latest.revision: 10
caps.handback.revision: 0
manager: jhubbard
---
# Data Quality Matching Columns (MDS Add-in for Excel)
In the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Topics/TopicNameContainA/tokens/ssMDSXLS_md.md)], after you match data, in the **Data Quality** group on the ribbon, you can click **Show Details** to display columns that provide matching details.  
  
 The following table shows the columns that are displayed when matching data.  
  
|Name|Description|  
|----------|-----------------|  
|**CLUSTER_ID**|A unique identifier used to group similar records. All rows that are similar have the same **CLUSTER_ID**. If no **CLUSTER_ID** is displayed for a row, then no similar records were found.|  
|**RECORD_ID**|A unique identifier used to identify records. Similar to the Code value stored in the MDS repository, it is a value used to identify a record. It is generated automatically each time matching takes place.|  
|**PIVOT_MARK**|An arbitrary record that other records are compared to; it does not have a score value.|  
|**SCORE**|Represents how similar the records in the group are to the pivot record. This score is determined by DQS. If no score is displayed, either the record is the pivot for other records, or no matches were found.|  
  
## See Also  
 [Data Quality Matching in the MDS Add-in for Excel](../../Topics/TopicNameNotContainA/Data-Quality-Matching-in-the-MDS-Add-in-for-Excel.md)   
 [Match Similar Data (MDS Add-in for Excel)](../../Topics/TopicNameNotContainA/Match-Similar-Data--MDS-Add-in-for-Excel-.md)   
 [Data Matching](../../Topics/TopicNameNotContainA/Data-Matching.md)