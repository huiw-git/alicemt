---
title: Raw File Source
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5b4daea5-7f76-4674-aa77-0a79f9f97f7d
---
# Raw File Source
  The Raw File source reads raw data from a file. Because the representation of the data is native to the source, the data requires no translation and almost no parsing. This means that the Raw File source can read data more quickly than other sources such as the Flat File and the OLE DB sources.  
  
 The Raw File source is used to retrieve raw data that was previously written by the Raw File destination. You can also point the Raw File source to an empty raw file that contains only the columns \(metadata\-only file\). You use the Raw File destination to generate the metadata\-only file without having to run the package. For more information, see [Raw File Destination](../../Topics\TopicNameNotContainA/Raw-File-Destination.md).  
  
 The raw file format contains sort information. The Raw File Destination saves all the sort information including the comparison flags for string columns. The Raw File source reads and honors the sort information. You do have the option of configuring the Raw File Source to ignore the sort flags in the file, using the Advanced Editor. For more information about comparison flags, see [Comparing String Data](../../Topics\TopicNameNotContainA/Comparing-String-Data.md).  
  
 You configure the Raw File by specifying the name of the name of the file that the Raw File source reads.  
  
> [!NOTE]  
>  This source does not use a connection manager.  
  
 This source has one output. It does not support an error output.  
  
## Configuration of the Raw File Source  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 The **Advanced Editor** dialog box reflects the properties that can be set programmatically. For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:  
  
-   [Common Properties](../../Topics\TopicNameNotContainA/Common-Properties.md)  
  
-   [Raw File Custom Properties](../../Topics\TopicNameNotContainA/Raw-File-Custom-Properties.md)  
  
## Related Tasks  
 For information about how to set the properties of the component, see [Set the Properties of a Data Flow Component](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Data-Flow-Component.md).  
  
## Related Content  
  
-   Blog entry, [Raw Files Are Awesome](http://www.sqlservercentral.com/blogs/stratesql/archive/2011/1/1/31-days-of-ssis-_1320_-raw-files-are-awesome-_2800_1_2F00_31_2900_.aspx), on sqlservercentral.com  
  
## See Also  
 [Raw File Destination](../../Topics\TopicNameNotContainA/Raw-File-Destination.md)   
 [Data Flow](../../Topics\TopicNameNotContainA/Data-Flow.md)  
  
  