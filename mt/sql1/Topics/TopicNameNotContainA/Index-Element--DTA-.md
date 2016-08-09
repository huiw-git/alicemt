---
title: "Index Element (DTA)"
ms.custom: na
ms.date: 07/04/2016
ms.devlang: 
  - XML
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 447d3964-b387-40f6-9189-71386774c29e
caps.latest.revision: 19
caps.handback.revision: 0
manager: jhubbard
---
# Index Element (DTA)
Contains information about an index that you want to create or drop for a user-specified configuration.  
  
## Syntax  
  
```  
  
<Recommendation>  
  <Create>  
    <Index [Clustered | Unique | Online | IndexSizeInMB | NumberOfRows             | QUOTED_IDENTIFIER | ARITHABORT | CONCAT_NULL_YIELDS_NULL             | ANSI_NULLS | ANSI_PADDING | ANSI_WARNINGS  
            | NUMERIC_ROUNDABORT]  
     ...code removed here...  
    </Index>  
```  
  
## Element Attributes  
  
|Index attribute|Data type|Description|  
|---------------------|---------------|-----------------|  
|**Clustered**|**boolean**|Optional. Specifies a clustered index. Set to either "true" or "false", for example:<br /><br /> `<Index Clustered="true">`<br /><br /> By default, this attribute is set to "false".|  
|**Unique**|**boolean**|Optional. Specifies a unique index. Set to either "true" or "false", for example:<br /><br /> `<Index Unique="true">`<br /><br /> By default, this attribute is set to "false".|  
|**Online**|**boolean**|Optional. Specifies an index that can perform operations while the server is online, which requires temporary disk space. Set to either "true" or "false", for example:<br /><br /> `<Index Online="true">`<br /><br /> By default, this attribute is set to "false".<br /><br /> For more information, see [Perform Index Operations Online](../../Topics/TopicNameNotContainA/Perform-Index-Operations-Online.md).|  
|**IndexSizeInMB**|**double**|Optional. Specifies the maximum size of the index in megabytes, for example:<br /><br /> `<Index IndexSizeInMB="873.75">`<br /><br /> No default setting.|  
|**NumberOfRows**|**integer**|Optional. Simulates different index sizes, which effectively simulates different table sizes, for example:<br /><br /> `<Index NumberOfRows="3000">`<br /><br /> No default setting.|  
|**QUOTED_IDENTIFIER**|**boolean**|Optional. Causes [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] to follow the ISO rules regarding quotation marks delimiting identifiers and literal strings. This attribute must be turned on if the index is on a computed column or a view. For example, the following syntax sets this attribute on:<br /><br /> `<Index QUOTED_IDENTIFIER [...]>`<br /><br /> By default this attribute is turned off.<br /><br /> For more information, see [SET QUOTED_IDENTIFIER (Transact-SQL)](assetId:///10f66b71-9241-4a3a-9292-455ae7252565).|  
|**ARITHABORT**|**boolean**|Optional. Causes a query to terminate when an overflow or divide-by-zero error occurs during query execution. This attribute must be turned on if the index is on a computed column or a view. For example, the following syntax sets this attribute on:<br /><br /> `<Index ARITHABORT [...]>`<br /><br /> By default this attribute is turned off.<br /><br /> For more information, see [SET ARITHABORT (Transact-SQL)](assetId:///f938a666-fdd1-4233-b97f-719f27b1a0e6).|  
|**CONCAT_NULL_YIELDS_**<br /><br /> **NULL**|**boolean**|Optional. Controls whether or not concatenation results are treated as null or empty string values. This attribute must be turned on if the index is on a computed column or a view. For example, the following syntax sets this attribute on:<br /><br /> `<Index CONCAT_NULL_YIELDS_NULL [...]>`<br /><br /> By default this attribute is turned off.<br /><br /> For more information, see [SET CONCAT_NULL_YIELDS_NULL (Transact-SQL)](assetId:///3091b71c-6518-4eb4-88ab-acae49102bc5).|  
|**ANSI_NULLS**|**boolean**|Optional. Specifies ISO compliant behavior of the Equals (=) and Not Equal to (<>) comparison operators when used with null values. This attribute must be turned on if the index is on a computed column or a view. For example, the following syntax sets this attribute on:<br /><br /> `<Index ANSI_NULLS [...]>`<br /><br /> By default this attribute is turned off.<br /><br /> For more information, see [SET ANSI_NULLS (Transact-SQL)](assetId:///aae263ef-a3c7-4dae-80c2-cc901e48c755).|  
|**ANSI_PADDING**|**boolean**|Optional. Controls the way a column stores values shorter than its defined size. This attribute must be turned on if the index is on a computed column or a view. For example, the following syntax sets this attribute on:<br /><br /> `<Index ANSI_PADDING [...]>`<br /><br /> By default this attribute is turned off.<br /><br /> For more information, see [SET ANSI_PADDING (Transact-SQL)](assetId:///92bd29a3-9beb-410e-b7e0-7bc1dc1ae6d0).|  
|**ANSI_WARNINGS**|**boolean**|Optional. Specifies ISO standard behavior for several error conditions. This attribute must be turned on if the index is on a computed column or a view. For example, the following syntax sets this attribute on:<br /><br /> `<Index ANSI_WARNING [...]>`<br /><br /> By default this attribute is turned off.<br /><br /> For more information, see [SET ANSI_WARNINGS (Transact-SQL)](assetId:///f82aaab0-334f-427b-89b0-de4af596b4fa).|  
|**NUMERIC_ROUNDABORT**|**boolean**|Optional. Specifies the level of error reporting generated when rounding in an expression causes a loss of precision. This attribute must be off if the index is on a computed column or a view.<br /><br /> The following syntax sets this attribute on:<br /><br /> `<Index ANSI_WARNING [...]>`<br /><br /> By default this attribute is turned off.<br /><br /> For more information, see [SET NUMERIC_ROUNDABORT (Transact-SQL)](assetId:///d20e74f1-b8da-466c-b180-9d8a8b851a77).|  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|None.|  
|**Default value**|None.|  
|**Occurrence**|Required once for each **Create** or **Drop** element if no other physical design structure is specified with either the **Statistics** or the **Heap** elements.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|[Create Element (DTA)](../../Topics/TopicNameNotContainA/Create-Element--DTA-.md)<br /><br /> **Drop** Element. For more information, see the Database Engine Tuning Advisor XML schema.|  
|**Child elements**|[Name Element for Index (DTA)](../../Topics/TopicNameNotContainA/Name-Element-for-Index--DTA-.md)<br /><br /> [Column Element for Index (DTA)](../../Topics/TopicNameNotContainA/Column-Element-for-Index--DTA-.md)<br /><br /> **PartitionScheme** Element. For more information, see the Database Engine Tuning Advisor XML schema.<br /><br /> **PartitionColumn** Element. For more information, see the Database Engine Tuning Advisor XML schema.<br /><br /> [Filegroup Element for Index (DTA)](../../Topics/TopicNameNotContainA/Filegroup-Element-for-Index--DTA-.md)<br /><br /> **NumberOfReferences** Element. For more information, see the Database Engine Tuning Advisor XML schema.<br /><br /> **PercentUsage** Element. For more information, see the Database Engine Tuning Advisor XML schema.|  
  
## Example  
 For a usage example of this element, see the [XML Input File Sample with User-specified Configuration (DTA)](../../Topics/TopicNameNotContainA/XML-Input-File-Sample-with-User-specified-Configuration--DTA-.md) .  
  
## See Also  
 [XML Input File Reference (Database Engine Tuning Advisor)](../../Topics/TopicNameNotContainA/XML-Input-File-Reference--Database-Engine-Tuning-Advisor-.md)