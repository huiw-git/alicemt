---
title: Path Properties
ms.custom: na
ms.devlang: 
  - VB
  - CSharp
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 89b1e347-9579-4f6b-af74-c6519ea08eea
---
# Path Properties
  The data flow objects in the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] object model have common properties and custom properties at the level of the component, inputs and outputs, and input columns and output columns. Many properties have read\-only values that are assigned at run time by the data flow engine.  
  
 This topic lists and describes the custom properties of the paths that connect data flow objects.  
  
## Path Properties  
 In the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] object model, a path that connects components in the data flow implements the [IDTSPath100](assetId:///T:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100) interface.  
  
 The following table describes the configurable properties of the paths in a data flow. The data flow engine also assigns values to additional read\-only properties that are not listed here.  
  
|Property name|Data Type|Description|  
|-------------------|---------------|-----------------|  
|PathAnnotation|Integer \(enumeration\)|A value that indicates whether an annotation should be displayed with the path on the designer surface. The possible values are **AsNeeded**, **SourceName**, **PathName**, and **Never**. The default value is **AsNeeded**.|  
|DestinationName|[IDTSInput100](assetId:///T:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100)|The input associated with the path.|  
|SourceName|[IDTSOutput100](assetId:///T:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100)|The output associated with the path.|  
  
## See Also  
 [Integration Services Paths](../../Topics\TopicNameNotContainA/Integration-Services-Paths.md)   
 [Common Properties](../../Topics\TopicNameNotContainA/Common-Properties.md)   
 [Transformation Custom Properties](../../Topics\TopicNameNotContainA/Transformation-Custom-Properties.md)   
 [Data Flow Properties that Can Be Set by Using Expressions](../../Topics\TopicNameNotContainA/Data-Flow-Properties-that-Can-Be-Set-by-Using-Expressions.md)  
  
  