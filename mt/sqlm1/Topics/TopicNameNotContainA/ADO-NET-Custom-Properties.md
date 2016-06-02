---
title: ADO NET Custom Properties
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e062a9ab-1e6b-4061-845a-4f8a0552b09d
---
# ADO NET Custom Properties
  **Source Custom Properties**  
  
 The ADO NET source has both custom properties and the properties common to all data flow components.  
  
 The following table describes the custom properties of the ADO NET source. All properties are read\/write.  
  
|Property name|Data Type|Description|  
|-------------------|---------------|-----------------|  
|CommandTimeout|String|A value that specifies the number of seconds before the SQL command times out. A value of 0 indicates that the command never times out.|  
|SqlCommand|String|The SQL statement that the ADO NET source uses to extract data.<br /><br /> When the package loads, you can dynamically update this property with the SQL statement that the ADO NET source will use. For more information, see [Integration Services &#40;SSIS&#41; Expressions](../Topic/Integration%20Services%20\(SSIS\)%20Expressions.md) and [Use Property Expressions in Packages](../../Topics\TopicNameNotContainA/Use-Property-Expressions-in-Packages.md).|  
|AllowImplicitStringConversion|Boolean|A value that indicates whether the following occurs:<br /><br /> \-No generation of a validation error if there is a mismatch between external metadata types and output column types that are strings \(DT\_WSTR or DT\_NTEXT\).<br /><br /> \-Implicit conversion of external metadata types to the string data type that the output column uses.<br /><br /> <br /><br /> The default value is TRUE.<br /><br /> For more information, see [ADO NET Source](../../Topics\TopicNameNotContainA/ADO-NET-Source.md).|  
  
 The output and the output columns of the ADO NET source have no custom properties.  
  
 For more information, see [ADO NET Source](../../Topics\TopicNameNotContainA/ADO-NET-Source.md).  
  
 **Destination Custom Properties**  
  
 The [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] destination has both custom properties and the properties common to all data flow components.  
  
 The following table describes the custom properties of the [!INCLUDE[vstecado](../../Token\Other/vstecado_md.md)] destination. All properties are read\/write. These properties are not available in the **ADO NET Destination Editor**, but can be set by using the **Advanced Editor**.  
  
|Property|Data Type|Description|  
|--------------|---------------|-----------------|  
|BatchSize|Integer|The number of rows in a batch that is sent to the server. A value of **0** indicates that the batch size matches the internal buffer size. The default value of this property is **0**.|  
|CommandTimeOut|Integer|The maximum number of seconds that the SQL command can run before timing out. A value of **0** indicates an infinite time. The default value of this property is **0**.|  
|TableOrViewName|String|The name of the destination table or view.|  
  
 For more information, see [ADO NET Destination](../../Topics\TopicNameNotContainA/ADO-NET-Destination.md).  
  
## See Also  
 [Common Properties](../../Topics\TopicNameNotContainA/Common-Properties.md)  
  
  