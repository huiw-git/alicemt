---
title: Column Element for Index (DTA)
ms.custom: na
ms.devlang: 
  - XML
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ba9fac20-26bd-4333-940e-842c15241b46
---
# Column Element for Index (DTA)
  Specifies the columns on which the index is created for a user\-specified configuration.  
  
## Syntax  
  
```  
  
<Create>  
  <Index>  
    <Name>...</Name>  
    <Column [Type | SortOrder]>  
     ...code removed here...  
     </Column>  
```  
  
## Element Attributes  
  
 **Type**: Optional. Specifies the index column type. Use a **string** data type to specify this attribute with one of the following allowed values:  
  
-   **KeyColumn**  
  
     Specifies that the column is referenced by an index key. Use the following syntax to set this attribute:  
  
    ```  
    <Column Type="KeyColumn">  
    ```  
  
     For more information about key columns, see [Clustered and Nonclustered Indexes Described](../../Topics\TopicNameNotContainA/Clustered-and-Nonclustered-Indexes-Described.md).  
  
-   **IncludedColumn**  
  
     Specifies that the column is an included column \(instead of a key column\). Use the following syntax to set this attribute:  
  
    ```  
    <Column Type="IncludedColumn">  
    ```  
  
     For more information about included columns, see [Create Indexes with Included Columns](../../Topics\TopicNameNotContainA/Create-Indexes-with-Included-Columns.md).  
  
 **SortOrder**: Optional. Specifies the sorting order of the column. Use a **string** data type to specify either an **"Ascending"** or **"Descending"** sorting order as follows:  
  
```  
<Column SortOrder="Ascending">  
```  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|None.|  
|**Default value**|None.|  
|**Occurrence**|Can specify up to 1024 columns for the **Index** element.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[Index Element &#40;DTA&#41;](../Topic/Index%20Element%20\(DTA\).md)|  
|**Child elements**|[Name Element for Column &#40;DTA&#41;](../Topic/Name%20Element%20for%20Column%20\(DTA\).md)|  
  
## Example  
 For a usage example of this element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](../Topic/XML%20Input%20File%20Sample%20with%20User-specified%20Configuration%20\(DTA\).md).  
  
## See Also  
 [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](../Topic/XML%20Input%20File%20Reference%20\(Database%20Engine%20Tuning%20Advisor\).md)  
  
  