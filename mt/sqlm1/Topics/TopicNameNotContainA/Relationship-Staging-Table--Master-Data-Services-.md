---
title: Relationship Staging Table (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e19b6002-67bd-4e7d-9f19-ecb455522b1a
---
# Relationship Staging Table (Master Data Services)
  Use the relationship staging table \(stg.name\_Relationship\) in the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database to change the location of members in an explicit hierarchy, based on the relationship the members have to one another.  
  
##  <a name="TableColumns"></a> Table Columns  
 The following table explains what each of the fields in the Relationship staging table are used for.  
  
|Column Name|Description|Value|  
|-----------------|-----------------|-----------|  
|**ID**|An automatically assigned identifier.|Do not enter a value in this field. If the batch has not been processed, this field is blank.|  
|**RelationshipType**|Required<br /><br /> The type of relationship that’s being set.|Possible values are:<br /><br /> **1**:Parent<br /><br /> **2**: Sibling \(at the same level\)|  
|**ImportStatus\_ID**|Required<br /><br /> The status of the import process.|Possible values are:<br /><br /> **0**, which you specify to indicate that the record is ready for staging.<br /><br /> **1**, which is automatically assigned and indicates that the staging process for the record has succeeded.<br /><br /> **2**, which is automatically assigned and indicates that the staging process for the record has failed.|  
|**Batch\_ID**|Required by web service only<br /><br /> An automatically assigned identifier that groups records for staging.<br /><br /> If the batch has not been processed, this field is blank.|All members in the batch are assigned this identifier, which is displayed in the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] user interface in the **ID** column.|  
|**BatchTag**|Required, except by web service<br /><br /> A unique name for the batch, up to 50 characters.||  
|**HierarchyName**|Required<br /><br /> The explicit hierarchy name. Each consolidated member can belong to one hierarchy only.||  
|**ParentCode**|Required<br /><br /> For parent\-child relationships, the code of the consolidated member that will be the parent of the child leaf or consolidated member.<br /><br /> For sibling relationships, the code of one of the siblings.||  
|**ChildCode**|Required<br /><br /> For parent\-child relationships, the code of the consolidated or leaf member that will be the child.<br /><br /> For sibling relationships, the code of one of the siblings.||  
|**Sort Order**|Optional<br /><br /> An integer that indicates the order of the member in relation to the other members under the parent. Each child member should have a unique identifier.||  
|**ErrorCode**|Displays an error code. For all records with a **ImportStatus\_ID** of **2**, see [Staging Process Errors &#40;Master Data Services&#41;](../Topic/Staging%20Process%20Errors%20\(Master%20Data%20Services\).md).||  
  
## See Also  
 [Overview: Importing Data from Tables &#40;Master Data Services&#41;](../Topic/Overview:%20Importing%20Data%20from%20Tables%20\(Master%20Data%20Services\).md)   
 [View Errors that Occur During Staging &#40;Master Data Services&#41;](../Topic/View%20Errors%20that%20Occur%20During%20Staging%20\(Master%20Data%20Services\).md)   
 [Staging Process Errors &#40;Master Data Services&#41;](../Topic/Staging%20Process%20Errors%20\(Master%20Data%20Services\).md)  
  
  