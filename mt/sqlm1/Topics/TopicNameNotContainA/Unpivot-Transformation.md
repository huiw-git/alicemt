---
title: Unpivot Transformation
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f635c64b-a9c5-4f11-9c40-9cd9d5298c5d
---
# Unpivot Transformation
  The Unpivot transformation makes an unnormalized dataset into a more normalized version by expanding values from multiple columns in a single record into multiple records with the same values in a single column. For example, a dataset that lists customer names has one row for each customer, with the products and the quantity purchased shown in columns in the row. After the Unpivot transformation normalizes the data set, the data set contains a different row for each product that the customer purchased.  
  
 The following diagram shows a data set before the data is unpivoted on the Product column.  
  
 ![Dataset after it is unpivoted](../../Images\Image\ImageNotContaina/mw_dts_18.gif "mw_dts_18")  
  
 The following diagram shows a data set after it has been unpivoted on the Product column.  
  
 ![Dataset before it is unpivoted](../../Images\Image\ImageNotContaina/mw_dts_17.gif "mw_dts_17")  
  
 Under some circumstances, the unpivot results may contain rows with unexpected values. For example, if the sample data to unpivot shown in the diagram had null values in all the Qty columns for Fred, then the output would include only one row for Fred, not five. The Qty column would contain either null or zero, depending on the column data type.  
  
## Configuration of the Unpivot Transformation  
 The Unpivot transformation includes the **PivotKeyValue** custom property. This property can be updated by a property expression when the package is loaded. For more information, see [Integration Services &#40;SSIS&#41; Expressions](../Topic/Integration%20Services%20\(SSIS\)%20Expressions.md), [Use Property Expressions in Packages](../../Topics\TopicNameNotContainA/Use-Property-Expressions-in-Packages.md), and [Transformation Custom Properties](../../Topics\TopicNameNotContainA/Transformation-Custom-Properties.md).  
  
 This transformation has one input and one output. It has no error output.  
  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in the **Unpivot Transformation Editor** dialog box, click one of the following topics:  
  
-   [Unpivot Transformation Editor](../../Topics\TopicNameNotContainA/Unpivot-Transformation-Editor.md)  
  
 For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:  
  
-   [Common Properties](../../Topics\TopicNameNotContainA/Common-Properties.md)  
  
-   [Transformation Custom Properties](../../Topics\TopicNameNotContainA/Transformation-Custom-Properties.md)  
  
 For more information about how to set the properties, see [Set the Properties of a Data Flow Component](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Data-Flow-Component.md).  
  
  