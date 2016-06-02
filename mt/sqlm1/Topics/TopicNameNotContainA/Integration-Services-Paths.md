---
title: Integration Services Paths
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6c4629a9-2ede-4011-9101-3b342249640e
---
# Integration Services Paths
  A path connects two components in a data flow by connecting the output of one data flow component to the input of another component. A path has a source and a destination. For example, if a path connects an OLE DB source and a Sort transformation, the OLE DB source is the source of the path, and the Sort transformation is the destination of the path. The source is the component where the path starts, and the destination is the component where the path ends.  
  
 If you run a package in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, you can view the data in a data flow by attaching data viewers to a path. A data viewer can be configured to display data in a grid. A data viewer is a useful debugging tool. For more information, see [Debugging Data Flow](../../Topics\TopicNameNotContainA/Debugging-Data-Flow.md).  
  
## Configuration of the Path  
 The [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer provides the **Data Flow Path Editor** dialog box for setting path properties, viewing the metadata of the data columns that pass through the path, and configuring data viewers.  
  
 The configurable path properties include the name, description, and annotation of the path. You can also configure paths programmatically. For more information, see [Connecting Data Flow Components Programmatically](../Topic/Connecting%20Data%20Flow%20Components%20Programmatically.md).  
  
 A path annotation displays the name of the path source or the path name on the design surface of the **Data Flow** tab in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer. Path annotations are similar to the annotations you can add to data flows, control flows, and event handlers. The only difference is that a path annotation is attached to a path, whereas other annotations appear on the **Data Flow**, **Control Flow**, and **Event Handle**r tabs of [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer.  
  
 The metadata shows the name, data type, precision, scale, length, code page, and source component of each column in the output of the previous component. The source component is the data flow component that created the column. This may or may not be the first component in the data flow. For example, the Union All and Sort transformations create their own columns, and they are the sources of their output columns. In contrast, a Copy Column transformation can pass through columns without changing them or can create new columns by copying input columns. The Copy Column transformation is the source component only of the new columns.  
  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in the **Data Flow Path Editor** dialog box, click one of the following topics:  
  
-   [Data Flow Path Editor &#40;General Page&#41;](../Topic/Data%20Flow%20Path%20Editor%20\(General%20Page\).md)  
  
-   [Data Flow Path Editor &#40;Metadata Page&#41;](../Topic/Data%20Flow%20Path%20Editor%20\(Metadata%20Page\).md)  
  
-   [Data Flow Path Editor &#40;Data Viewers Page&#41;](../Topic/Data%20Flow%20Path%20Editor%20\(Data%20Viewers%20Page\).md)  
  
 For more information about the properties that you can set programmatically, see [Path Properties](../../Topics\TopicNameNotContainA/Path-Properties.md).  
  
## Related Tasks  
  
-   [View Path Metadata in the Data Flow Path Editor](../../Topics\TopicNameNotContainA/View-Path-Metadata-in-the-Data-Flow-Path-Editor.md)  
  
-   [Connect Components in a Data Flow](../../Topics\TopicNameContainA/Connect-Components-in-a-Data-Flow.md)  
  
## See Also  
 [Data Flow](../../Topics\TopicNameNotContainA/Data-Flow.md)  
  
  