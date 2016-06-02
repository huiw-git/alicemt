---
title: Flat File Destination
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e0d6e356-8db4-48aa-ba66-029397f98f61
---
# Flat File Destination
  The Flat File destination writes data to a text file. The text file can be in delimited, fixed width, fixed width with row delimiter, or ragged right format.  
  
 You can configure the Flat File destination in the following ways:  
  
-   Provide a block of text that is inserted in the file before any data is written. The text can provide information such as column headings.  
  
-   Specify whether to overwrite a data in a destination file that has the same name.  
  
 This destination uses a Flat File connection manager to access the text file. By setting properties on the Flat File connection manager that the Flat File destination uses, you can specify how the Flat File destination formats and writes the text file. When you configure the Flat File connection manager, you specify information about the file and about each column in the file. For example, you specify the characters that delimit columns and rows in the file, and you specify the data type and the length of each column. For more information, see [Flat File Connection Manager](../../Topics\TopicNameNotContainA/Flat-File-Connection-Manager.md).  
  
 The Flat File destination includes the Header custom property. This property can be updated by a property expression when the package is loaded. For more information, see [Integration Services &#40;SSIS&#41; Expressions](../Topic/Integration%20Services%20\(SSIS\)%20Expressions.md), [Use Property Expressions in Packages](../../Topics\TopicNameNotContainA/Use-Property-Expressions-in-Packages.md), and [Flat File Custom Properties](../../Topics\TopicNameNotContainA/Flat-File-Custom-Properties.md).  
  
 This destination has one output. It does not support an error output.  
  
## Configuration of the Flat File Destination  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in the **Flat File Source Editor** dialog box, click one of the following topics:  
  
-   [Flat File Destination Editor &#40;Connection Manager Page&#41;](../Topic/Flat%20File%20Destination%20Editor%20\(Connection%20Manager%20Page\).md)  
  
-   [Flat File Destination Editor &#40;Mappings Page&#41;](../Topic/Flat%20File%20Destination%20Editor%20\(Mappings%20Page\).md)  
  
 The **Advanced Editor** dialog box reflects the properties that can be set programmatically. For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:  
  
-   [Common Properties](../../Topics\TopicNameNotContainA/Common-Properties.md)  
  
-   [Flat File Custom Properties](../../Topics\TopicNameNotContainA/Flat-File-Custom-Properties.md)  
  
## Related Tasks  
 For information about how to set the properties of a data flow component, see [Set the Properties of a Data Flow Component](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Data-Flow-Component.md).  
  
## See Also  
 [Flat File Source](../../Topics\TopicNameNotContainA/Flat-File-Source.md)   
 [Data Flow](../../Topics\TopicNameNotContainA/Data-Flow.md)  
  
  