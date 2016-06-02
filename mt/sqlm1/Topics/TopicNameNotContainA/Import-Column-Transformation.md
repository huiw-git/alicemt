---
title: Import Column Transformation
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ac3b74c1-ef54-4297-8062-1734324fffcc
---
# Import Column Transformation
  The Import Column transformation reads data from files and adds the data to columns in a data flow. Using this transformation, a package can add text and images stored in separate files to a data flow. For example, a data flow that loads data into a table that stores product information can include the Import Column transformation to import customer reviews of each product from files and add the reviews to the data flow.  
  
 You can configure the Import Column transformation in the following ways:  
  
-   Specify the columns to which the transformation adds data.  
  
-   Specify whether the transformation expects a byte\-order mark \(BOM\).  
  
    > [!NOTE]  
    >  A BOM is only expected if the data has the DT\_NTEXT data type.  
  
 A column in the transformation input contains the names of files that hold the data. Each row in the dataset can specify a different file. When the Import Column transformation processes a row, it reads the file name, opens the corresponding file in the file system, and loads the file content into an output column. The data type of the output column must be DT\_TEXT, DT\_NTEXT, or DT\_IMAGE. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
 This transformation has one input, one output, and one error output.  
  
## Configuration of the Import Column Transformation  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 The **Advanced Editor** dialog box reflects the properties that can be set programmatically. For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:  
  
-   [Common Properties](../../Topics\TopicNameNotContainA/Common-Properties.md)  
  
-   [Transformation Custom Properties](../../Topics\TopicNameNotContainA/Transformation-Custom-Properties.md)  
  
## Related Tasks  
 For information about how to set properties of this component, see [Set the Properties of a Data Flow Component](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Data-Flow-Component.md).  
  
## See Also  
 [Export Column Transformation](../../Topics\TopicNameNotContainA/Export-Column-Transformation.md)   
 [Data Flow](../../Topics\TopicNameNotContainA/Data-Flow.md)   
 [Integration Services Transformations](../../Topics\TopicNameNotContainA/Integration-Services-Transformations.md)  
  
  