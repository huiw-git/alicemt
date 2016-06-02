---
title: Flat File Source
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4a64f7f3-f25d-4db0-93b3-a29496030e58
---
# Flat File Source
  The Flat File source reads data from a text file. The text file can be in delimited, fixed width, or mixed format.  
  
-   Delimited format uses column and row delimiters to define columns and rows.  
  
-   Fixed width format uses width to define columns and rows. This format also includes a character for padding fields to their maximum width.  
  
-   Ragged right format uses width to define all columns, except for the last column, which is delimited by the row delimiter.  
  
 You can configure the Flat File source in the following ways:  
  
-   Add a column to the transformation output that contains the name of the text file from which the Flat File source extracts data.  
  
-   Specify whether the Flat File source interprets zero\-length strings in columns as null values.  
  
    > [!NOTE]  
    >  The Flat File connection manager that the Flat File source uses must be configured to use a delimited format to interpret zero\-length strings as nulls. If the connection manager uses the fixed width or ragged right formats, data that consists of spaces cannot be interpreted as null values.  
  
 The output columns in the output of the Flat File source include the FastParse property. FastParse indicates whether the column uses the quicker, but locale\-insensitive, fast parsing routines that [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] provides or the locale\-sensitive standard parsing routines. For more information, see [Fast Parse](../../Topics\TopicNameNotContainA/Fast-Parse.md) and [Standard Parse](../../Topics\TopicNameNotContainA/Standard-Parse.md).  
  
 Output columns also include the UseBinaryFormat property. You use this property to implement support for binary data, such as data with the packed decimal format, in files. By default UseBinaryFormat is set to **false**. If you want to use a binary format, set UseBinaryFormat to **true** and the data type on the output column to **DT\_BYTES**. When you do this, the Flat File source skips the data conversion and passes the data to the output column as is. You can then use a transformation such as the Derived Column or Data Conversion to cast the **DT\_BYTES** data to a different data type, or you can write custom script in a Script transformation to interpret the data. You can also write a custom data flow component to interpret the data. For more information about which data types you can cast **DT\_BYTES** to, see [Cast &#40;SSIS Expression&#41;](../Topic/Cast%20\(SSIS%20Expression\).md).  
  
 This source uses a Flat File connection manager to access the text file. By setting properties on the Flat File connection manager, you can provide information about the file and each column in it, and specify how the Flat File source should handle the data in the text file. For example, you can specify the characters that delimit columns and rows in the file, and the data type and the length of each column. For more information, see [Flat File Connection Manager](../../Topics\TopicNameNotContainA/Flat-File-Connection-Manager.md).  
  
 This source has one output and one error output.  
  
## Configuration of the Flat File Source  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in the **Flat File Source Editor** dialog box, click one of the following topics:  
  
-   [Flat File Source Editor &#40;Connection Manager Page&#41;](../Topic/Flat%20File%20Source%20Editor%20\(Connection%20Manager%20Page\).md)  
  
-   [Flat File Source Editor &#40;Columns Page&#41;](../Topic/Flat%20File%20Source%20Editor%20\(Columns%20Page\).md)  
  
-   [Flat File Source Editor &#40;Error Output Page&#41;](../Topic/Flat%20File%20Source%20Editor%20\(Error%20Output%20Page\).md)  
  
 The **Advanced Editor** dialog box reflects the properties that can be set programmatically. For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:  
  
-   [Common Properties](../../Topics\TopicNameNotContainA/Common-Properties.md)  
  
-   [Flat File Custom Properties](../../Topics\TopicNameNotContainA/Flat-File-Custom-Properties.md)  
  
## Related Tasks  
 For details about how to set properties of a data flow component, see [Set the Properties of a Data Flow Component](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Data-Flow-Component.md).  
  
## See Also  
 [Flat File Destination](../../Topics\TopicNameNotContainA/Flat-File-Destination.md)   
 [Data Flow](../../Topics\TopicNameNotContainA/Data-Flow.md)  
  
  