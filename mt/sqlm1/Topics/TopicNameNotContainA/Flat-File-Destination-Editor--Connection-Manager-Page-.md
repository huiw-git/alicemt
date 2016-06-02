---
title: Flat File Destination Editor (Connection Manager Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b01571fa-bc19-4742-8eed-ac163172a919
---
# Flat File Destination Editor (Connection Manager Page)
  Use the **Connection Manager** page of the **Flat File Destination Editor** dialog box to select the flat file connection for the destination, and to specify whether to overwrite or append to the existing destination file. The flat file destination writes data to a text file. This text file can be in delimited, fixed width, fixed width with row delimiter, or ragged right format.  
  
 To learn more about the Flat File destination, see [Flat File Destination](../../Topics\TopicNameNotContainA/Flat-File-Destination.md).  
  
## Options  
 **Flat File connection manager**  
 Select an existing connection manager by using the list box, or create a new connection by clicking **New**.  
  
 **New**  
 Create a new connection by using the **Flat File Format** and **Flat File Connection Manager Editor** dialog boxes.  
  
 In addition to the standard flat file formats of delimited, fixed width, and ragged right, the **Flat File Format** dialog box has a fourth option, **Fixed width with row delimiters**. This option represents a special case of the ragged\-right format in which [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] adds a dummy column as the final column of data. This dummy column ensures that the final column has a fixed width.  
  
 The **Fixed width with row delimiters** option is not available in the **Flat File Connection Manager Editor**. If necessary, you can emulate this option in the editor. To emulate this option, on the **General** page of the **Flat File Connection Manager Editor**, for **Format**, select **Ragged right**. Then on the **Advanced** page of the editor, add a new dummy column as the final column of data.  
  
 **Overwrite data in the file**  
 Indicate whether to overwrite an existing file, or to append data to it.  
  
 **Header**  
 Type a block of text to insert into the file before any data is written. Use this option to include additional information, such as column headings.  
  
 **Preview**  
 Preview results by using the **Data View** dialog box. Preview can display up to 200 rows.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Flat File Destination Editor &#40;Mappings Page&#41;](../Topic/Flat%20File%20Destination%20Editor%20\(Mappings%20Page\).md)  
  
  