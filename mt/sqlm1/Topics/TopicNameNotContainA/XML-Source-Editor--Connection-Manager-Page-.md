---
title: XML Source Editor (Connection Manager Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e6507403-a3ce-4b6f-91fc-a7de9f7b6283
---
# XML Source Editor (Connection Manager Page)
  Use the **Connection Manager** page of the **XML Source Editor** to specify an XML file and the XSD that transforms the XML data.  
  
 For more information about the XML source, see [XML Source](../../Topics\TopicNameNotContainA/XML-Source.md).  
  
## Static Options  
 **Data access mode**  
 Specify the method for selecting data from the source.  
  
|Value|Description|  
|-----------|-----------------|  
|XML file location|Retrieve data from an XML file.|  
|XML file from variable|Specify the XML file name in a variable.<br /><br /> **Related information**: [Use Variables in Packages](../../Topics\TopicNameNotContainA/Use-Variables-in-Packages.md)|  
|XML data from variable|Retrieve XML data from a variable.|  
  
 **Use inline schema**  
 Specify whether the XML source data itself contains the XSD schema that defines and validates its structure and data.  
  
 **XSD location**  
 Type the path and file name of the XSD schema file, or locate the file by clicking **Browse**.  
  
 **Browse**  
 Use the **Open** dialog box to locate the XSD schema file.  
  
 **Generate XSD**  
 Use the **Save As** dialog box to select a location for the auto\-generated XSD schema file. The editor infers the schema from the structure of the XML data.  
  
## Data Access Mode Dynamic Options  
  
### Data access mode \= XML file location  
 **XML location**  
 Type the path and file name of the XML data file, or locate the file by clicking **Browse**.  
  
 **Browse**  
 Use the **Open** dialog box to locate the XML data file.  
  
### Data access mode \= XML file from variable  
 **Variable name**  
 Select the variable that contains the path and file name of the XML file.  
  
### Data access mode \= XML data from variable  
 **Variable name**  
 Select the variable that contains the XML data.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [XML Source Editor &#40;Columns Page&#41;](../Topic/XML%20Source%20Editor%20\(Columns%20Page\).md)   
 [XML Source Editor &#40;Error Output Page&#41;](../Topic/XML%20Source%20Editor%20\(Error%20Output%20Page\).md)   
 [Extract Data by Using the XML Source](../../Topics\TopicNameNotContainA/Extract-Data-by-Using-the-XML-Source.md)  
  
  