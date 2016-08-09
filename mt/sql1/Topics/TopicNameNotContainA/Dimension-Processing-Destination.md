---
title: "Dimension Processing Destination"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4c49bb95-7259-42f4-a785-bb6aaf5f8566
caps.latest.revision: 41
caps.handback.revision: 0
manager: jhubbard
---
# Dimension Processing Destination
The Dimension Processing destination loads and processes an [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] dimension. For more information about dimensions, see [Dimensions (Analysis Services)](assetId:///2b114135-2572-4479-8c81-3ccf0cfeb9f7).  
  
 The Dimension Processing destination includes the following features:  
  
-   Options to perform incremental, full, or update processing.  
  
-   Error configuration, to specify whether dimension processing ignores errors or stops after a specified number of errors.  
  
-   Mapping of input columns to columns in dimension tables.  
  
 For more information about processing [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] objects, see [Processing Options and Settings (Analysis Services)](../../Topics/TopicNameNotContainA/Processing-Options-and-Settings--Analysis-Services-.md).  
  
## Configuration of the Dimension Processing Destination  
 The Dimension Processing destination uses an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] connection manager to connect to the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] project or the instance of [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] that contains the dimensions the destination processes. For more information, see [Analysis Services Connection Manager](../../Topics/TopicNameNotContainA/Analysis-Services-Connection-Manager.md).  
  
 This destination has one input. It does not support an error output.  
  
 You can set properties through [!INCLUDE[ssIS](../../Topics/TopicNameContainA/tokens/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in the **Dimension Processing Destination Editor** dialog box, click one of the following topics:  
  
-   [Dimension Processing Destination Editor (Connection Manager Page)](../../Topics/TopicNameNotContainA/Dimension-Processing-Destination-Editor--Connection-Manager-Page-.md)  
  
-   [Dimension Processing Destination Editor (Mappings Page)](../../Topics/TopicNameNotContainA/Dimension-Processing-Destination-Editor--Mappings-Page-.md)  
  
-   [Dimension Processing Destination Editor (Advanced Page)](../../Topics/TopicNameNotContainA/Dimension-Processing-Destination-Editor--Advanced-Page-.md)  
  
 The **Advanced Editor** dialog box reflects the properties that can be set programmatically. For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topic:  
  
-   [Common Properties](../../Topics/TopicNameNotContainA/Common-Properties.md)  
  
 For more information about how to set the properties, see [Set the Properties of a Data Flow Component](../../Topics/TopicNameContainA/Set-the-Properties-of-a-Data-Flow-Component.md).  
  
## See Also  
 [Data Flow](../../Topics/TopicNameNotContainA/Data-Flow.md)   
 [Integration Services Transformations](../../Topics/TopicNameNotContainA/Integration-Services-Transformations.md)