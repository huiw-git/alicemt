---
title: Character Map Transformation Editor
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3f1dbcf9-9cca-4606-bdcc-7ea6ad48cdf3
---
# Character Map Transformation Editor
  Use the **Character Map Transformation Editor** dialog box to select the string functions to apply to column data and to specify whether mapping is an in\-place change or added as a new column.  
  
 To learn more about the Character Map transformation, see [Character Map Transformation](../../Topics\TopicNameNotContainA/Character-Map-Transformation.md).  
  
## Options  
 **Available Input Columns**  
 Use the check boxes to select the columns to transform using string functions. Your selections appear in the table below.  
  
 **Input Column**  
 View input columns selected from the table above. You can also change or remove a selection by using the list of available input columns.  
  
 **Destination**  
 Specify whether to save the results of the string operations in place, using the existing column, or to save the modified data as a new column.  
  
|Value|Description|  
|-----------|-----------------|  
|New column|Save the data in a new column. Assign the column name under **Output Alias**.|  
|In\-place change|Save the modified data in the existing column.|  
  
 **Operation**  
 Select from the list the string functions to apply to column data.  
  
|Value|Description|  
|-----------|-----------------|  
|Lowercase|Convert to lower case.|  
|Uppercase|Convert to upper case.|  
|Byte reversal|Convert by reversing byte order.|  
|Hiragana|Convert Japanese katakana characters to hiragana.|  
|Katakana|Convert Japanese hiragana characters to katakana.|  
|Half width|Convert full\-width characters to half width.|  
|Full width|Convert half\-width characters to full width.|  
|Linguistic casing|Apply linguistic rules of casing \(Unicode simple case mapping for Turkic and other locales\) instead of the system rules.|  
|Simplified Chinese|Convert traditional Chinese characters to simplified Chinese.|  
|Traditional Chinese|Convert simplified Chinese characters to traditional Chinese.|  
  
 **Output Alias**  
 Type an alias for each output column. The default is **Copy of** followed by the input column name; however, you can choose any unique, descriptive name.  
  
 **Configure Error Output**  
 Use the [Configure Error Output](../../Topics\TopicNameNotContainA/Configure-Error-Output.md) dialog box to specify error handling options for this transformation.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)  
  
  