---
title: DTAXML Element (DTA)
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
ms.assetid: 3d9942ed-8a27-40db-a7c9-808984d914a2
---
# DTAXML Element (DTA)
  The root element of a Database Engine Tuning Advisor XML input or output file, **DTAXML** contains all elements that describe tuning input and the tuning output that Database Engine Tuning Advisor generates.  
  
## Syntax  
  
```  
  
<DTAXML   
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
    xmlns="http://schemas.microsoft.com/sqlserver/2004/07/dta">  
    ...code removed here...  
</DTAXML>  
```  
  
## Element Attributes  
  
|Attribute|Description|  
|---------------|-----------------|  
|**xmlns:xsi**|Required. Identifies the XML Schema Instance namespace. Attributes from this namespace are used to reference the schema that is used to validate the Database Engine Tuning Advisor XML file.<br /><br /> Required value: [http:\/\/www.w3.org\/2001\/XMLSchema\-instance](http://www.w3.org/2001/XMLSchema-instance)|  
|**xmlns**|Required. Identifies the Database Engine Tuning Advisor namespace.<br /><br /> If you edit the Database Engine Tuning Advisor XML file using the XML editor in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], this value is used by F1 Help and Dynamic Help to locate possible reference topics in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Books Online.<br /><br /> Required value:<br /><br /> [Database Engine Tuning Advisor XML Schema](http://go.microsoft.com/fwlink/?LinkId=43100) Namespace|  
  
## Element Characteristics  
  
|Characteristic|Description|  
|--------------------|-----------------|  
|**Data type and length**|None.|  
|**Default value**|None.|  
|**Occurrence**|Required once per DTA XML file.|  
  
## Element Relationships  
  
|Relationship|Elements|  
|------------------|--------------|  
|**Parent element**|None|  
|**Child elements**|[DTAInput Element &#40;DTA&#41;](../Topic/DTAInput%20Element%20\(DTA\).md)<br /><br /> **DTAOutput** Element \(see [Database Engine Tuning Advisor XML schema](http://schemas.microsoft.com/sqlserver/) for information\)|  
  
## Remarks  
 For more information about XML namespaces, see [Namespaces in an XML Document](http://go.microsoft.com/fwlink/?LinkId=7341) in the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] MSDN Library.  
  
## Example  
 For examples of typical **DTAXML** elements, see [XML Input File Samples &#40;DTA&#41;](../Topic/XML%20Input%20File%20Samples%20\(DTA\).md).  
  
## See Also  
 [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](../Topic/XML%20Input%20File%20Reference%20\(Database%20Engine%20Tuning%20Advisor\).md)   
 [Start and Use the Database Engine Tuning Advisor](../../Topics\TopicNameNotContainA/Start-and-Use-the-Database-Engine-Tuning-Advisor.md)  
  
  