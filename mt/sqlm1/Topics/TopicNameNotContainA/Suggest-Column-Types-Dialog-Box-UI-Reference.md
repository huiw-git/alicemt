---
title: Suggest Column Types Dialog Box UI Reference
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8d5652e0-cf57-483f-828b-10f00c08418b
---
# Suggest Column Types Dialog Box UI Reference
  Use the **Suggest Column Types** dialog box to identify the data type and length of columns in a Flat File Connection Manager based on a sampling of the file content.  
  
 To learn more about the data types used by [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)], see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
## Options  
 **Number of rows**  
 Type or select the number of rows in the sample that the algorithm uses.  
  
 **Suggest the smallest integer data type**  
 Clear this check box to skip the assessment. If selected, determines the smallest possible integer data type for columns that contain integral numeric data.  
  
 **Suggest the smallest real data type**  
 Clear this check box to skip the assessment. If selected, determines whether columns that contain real numeric data can use the smaller real data type, DT\_R4.  
  
 **Identify Boolean columns using the following values**  
 Type the two values that you want to use as the Boolean values true and false. The values must be separated by a comma, and the first value represents True.  
  
 **Pad string columns**  
 Select this check box to enable string padding.  
  
 **Percent padding**  
 Type or select the percentage of the column lengths by which to increase the length of columns for character data types. The percentage must be an integer.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Flat File Connection Manager](../../Topics\TopicNameNotContainA/Flat-File-Connection-Manager.md)  
  
  