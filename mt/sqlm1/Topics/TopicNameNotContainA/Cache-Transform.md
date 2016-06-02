---
title: Cache Transform
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a5683fc8-9c32-4634-819e-e9815627e4f1
---
# Cache Transform
  The Cache Transform transformation generates a reference dataset for the Lookup Transformation by writing data from a connected data source in the data flow to a Cache connection manager. The Lookup transformation performs lookups by joining data in input columns from a connected data source with columns in the reference database.  
  
 You can use the Cache connection manager when you want to configure the Lookup Transformation to run in the full cache mode. In this mode, the reference dataset is loaded into cache before the Lookup Transformation runs.  
  
 For instructions on how to configure the Lookup transformation in full cache mode with the Cache connection manager and Cache Transform transformation, see [Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager](../../Topics\TopicNameContainA/Implement-a-Lookup-Transformation-in-Full-Cache-Mode-Using-the-Cache-Connection-Manager.md).  
  
 For more information on caching the reference dataset, see [Lookup Transformation](../../Topics\TopicNameNotContainA/Lookup-Transformation.md).  
  
> [!NOTE]  
>  The Cache Transform writes only unique rows to the Cache connection manager.  
  
 In a single package, only one Cache Transform can write data to the same Cache connection manager. If the package contains multiple Cache Transforms, the first Cache Transform that is called when the package runs, writes the data to the connection manager. The write operations of subsequent Cache Transforms fail.  
  
 For more information, see [Cache Connection Manager](../../Topics\TopicNameNotContainA/Cache-Connection-Manager.md) and [Cache Connection Manager Editor](../../Topics\TopicNameNotContainA/Cache-Connection-Manager-Editor.md).  
  
## Configuration of the Cache Transform  
 You can configure the Cache connection manager to save the data to a cache file \(.caw\).  
  
 You can configure the Cache Transform in the following ways:  
  
-   Specify the Cache connection manager.  
  
-   Map the input columns in the Cache Transform to destination columns in the Cache connection manager.  
  
    > [!NOTE]  
    >  Each input column must be mapped to a destination column, and the column data types must match. Otherwise, [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] Designer displays an error message.  
  
     You can use the **Cache Connection Manager Editor** to modify column data types, names, and other column properties.  
  
 You can set properties through [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] Designer. For more information about the properties that you can set in the **Advanced Editor** dialog box, see [Transformation Custom Properties](../../Topics\TopicNameNotContainA/Transformation-Custom-Properties.md).  
  
 For more information about how to set properties, see [Set the Properties of a Data Flow Component](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Data-Flow-Component.md).  
  
## See Also  
 [Integration Services Transformations](../../Topics\TopicNameNotContainA/Integration-Services-Transformations.md)   
 [Data Flow](../../Topics\TopicNameNotContainA/Data-Flow.md)  
  
  