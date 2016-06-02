---
title: Term Lookup Transformation Editor (Term Lookup Tab)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 245d3466-d51f-4073-978a-694a8d9dfaec
---
# Term Lookup Transformation Editor (Term Lookup Tab)
  Use the **Term Lookup** tab of the **Term Lookup Transformation Editor** dialog box to map an input column to a lookup column in a reference table and to provide an alias for each output column.  
  
 To learn more about the Term Lookup transformation, see [Term Lookup Transformation](../../Topics\TopicNameNotContainA/Term-Lookup-Transformation.md).  
  
## Options  
 **Available Input Columns**  
 Using the check boxes, select input columns to pass through to the output unchanged. Drag an input column to the **Available Reference Columns** list to map it to a lookup column in the reference table. The input and lookup columns must have matching, supported data types, either DT\_NTEXT or DT\_WSTR. Select a mapping line and right\-click to edit the mappings in the [Create Relationships](../../Topics\TopicNameNotContainA/Create-Relationships.md) dialog box.  
  
 **Available Reference Columns**  
 View the available columns in the reference table. Choose the column that contains the list of terms to match.  
  
 **Pass\-Through Column**  
 Select from the list of available input columns. Your selections are reflected in the check box selections in the **Available Input Columns** table.  
  
 **Output Column Alias**  
 Type an alias for each output column. The default is the name of the column; however, you can choose any unique, descriptive name.  
  
 **Configure Error Output**  
 Use the [Configure Error Output](../../Topics\TopicNameNotContainA/Configure-Error-Output.md) dialog box to specify error handling options for rows that cause errors.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Term Lookup Transformation Editor &#40;Reference Table Tab&#41;](../Topic/Term%20Lookup%20Transformation%20Editor%20\(Reference%20Table%20Tab\).md)   
 [Term Lookup Transformation Editor &#40;Advanced Tab&#41;](../Topic/Term%20Lookup%20Transformation%20Editor%20\(Advanced%20Tab\).md)   
 [Term Extraction Transformation](../../Topics\TopicNameNotContainA/Term-Extraction-Transformation.md)  
  
  