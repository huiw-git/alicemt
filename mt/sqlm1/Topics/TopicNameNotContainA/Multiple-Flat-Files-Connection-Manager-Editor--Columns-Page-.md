---
title: Multiple Flat Files Connection Manager Editor (Columns Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ad0cb668-0df2-4d4e-9a20-d20692a0b67a
---
# Multiple Flat Files Connection Manager Editor (Columns Page)
  Use the **Columns** node of the **Multiple Flat Files Connection Manager Editor** dialog box to specify the row and column information, and to preview the first selected file.  
  
 To learn more about the Multiple Flat Files connection manager, see [Multiple Flat Files Connection Manager](../../Topics\TopicNameNotContainA/Multiple-Flat-Files-Connection-Manager.md).  
  
## Static Options  
 **Connection manager name**  
 Provide a unique name for the Multiple Flat Files connection in the workflow. The name provided will be displayed within [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer.  
  
 **Description**  
 Describe the connection. As a best practice, describe the connection in terms of its purpose, to make packages self\-documenting and easier to maintain.  
  
## Flat File Format Dynamic Options  
  
### Format \= Delimited  
 **Row delimiter**  
 Select from the list of available row delimiters, or enter the delimiter text.  
  
|Value|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Rows are delimited by a carriage return\-line feed combination.|  
|**{CR}**|Rows are delimited by a carriage return.|  
|**{LF}**|Rows are delimited by a line feed.|  
|**Semicolon {;}**|Rows are delimited by a semicolon.|  
|**Colon {:}**|Rows are delimited by a colon.|  
|**Comma {,}**|Rows are delimited by a comma.|  
|**Tab {t}**|Rows are delimited by a tab.|  
|**Vertical bar {&#124;}**|Rows are delimited by a vertical bar.|  
  
 **Column delimiter**  
 Select from the list of available column delimiters, or enter the delimiter text.  
  
|Value|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Columns are delimited by a carriage return\-line feed combination.|  
|**{CR}**|Columns are delimited by a carriage return.|  
|**{LF}**|Columns are delimited by a line feed.|  
|**Semicolon {;}**|Columns are delimited by a semicolon.|  
|**Colon {:}**|Columns are delimited by a colon.|  
|**Comma {,}**|Columns are delimited by a comma.|  
|**Tab {t}**|Columns are delimited by a tab.|  
|**Vertical bar {&#124;}**|Columns are delimited by a vertical bar.|  
  
 **Reset Columns**  
 Remove all but the original columns by clicking **Reset Columns**.  
  
### Format \= Fixed Width  
 **Font**  
 Select the font in which to display the preview data.  
  
 **Source data columns**  
 Adjust the width of the row by sliding the vertical row marker, and adjust the width of the columns by clicking the ruler at the top of the preview window  
  
 **Row width**  
 Specify the length of the row before adding delimiters for individual columns. Or, drag the vertical line in the preview window to mark the end of the row. The row width value is automatically updated.  
  
 **Reset Columns**  
 Remove all but the original columns by clicking **Reset Columns**.  
  
### Format \= Ragged Right  
  
> [!NOTE]  
>  Ragged right files are those in which every column has a fixed width, except for the last column. It is delimited by the row delimiter.  
  
 **Font**  
 Select the font in which to display the preview data.  
  
 **Source data columns**  
 Adjust the width of the row by sliding the vertical row marker, and adjust the width of the columns by clicking the ruler at the top of the preview window  
  
 **Row delimiter**  
 Select from the list of available row delimiters, or enter the delimiter text.  
  
|Value|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Rows are delimited by a carriage return\-line feed combination.|  
|**{CR}**|Rows are delimited by a carriage return.|  
|**{LF}**|Rows are delimited by a line feed.|  
|**Semicolon {;}**|Rows are delimited by a semicolon.|  
|**Colon {:}**|Rows are delimited by a colon.|  
|**Comma {,}**|Rows are delimited by a comma.|  
|**Tab {t}**|Rows are delimited by a tab.|  
|**Vertical bar {&#124;}**|Rows are delimited by a vertical bar.|  
  
 **Reset Columns**  
 Remove all but the original columns by clicking **Reset Columns**.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Multiple Flat Files Connection Manager Editor &#40;General Page&#41;](../Topic/Multiple%20Flat%20Files%20Connection%20Manager%20Editor%20\(General%20Page\).md)   
 [Multiple Flat Files Connection Manager Editor &#40;Advanced Page&#41;](../Topic/Multiple%20Flat%20Files%20Connection%20Manager%20Editor%20\(Advanced%20Page\).md)   
 [Multiple Flat Files Connection Manager Editor &#40;Preview Page&#41;](../Topic/Multiple%20Flat%20Files%20Connection%20Manager%20Editor%20\(Preview%20Page\).md)  
  
  