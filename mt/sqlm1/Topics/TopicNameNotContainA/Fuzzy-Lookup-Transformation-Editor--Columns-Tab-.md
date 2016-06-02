---
title: Fuzzy Lookup Transformation Editor (Columns Tab)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aaf45327-79e9-4760-9b4d-546ace91b5b4
---
# Fuzzy Lookup Transformation Editor (Columns Tab)
  Use the **Columns** tab of the **Fuzzy Lookup Transformation Editor** dialog box to set properties for input and output columns.  
  
 To learn more about the Fuzzy Lookup transformation, see [Fuzzy Lookup Transformation](../../Topics\TopicNameNotContainA/Fuzzy-Lookup-Transformation.md).  
  
## Options  
 **Available Input Columns**  
 Drag input columns to connect them to available lookup columns. These columns must have matching, supported data types. Select a mapping line and right\-click to edit the mappings in the [Create Relationships](../../Topics\TopicNameNotContainA/Create-Relationships.md) dialog box.  
  
 **Name**  
 View the names of the available input columns.  
  
 **Pass Through**  
 Specify whether to include the input columns in the output of the transformation.  
  
 **Available Lookup Columns**  
 Use the check boxes to select columns on which to perform fuzzy lookup operations.  
  
 **Lookup Column**  
 Select lookup columns from the list of available reference table columns. Your selections are reflected in the check box selections in the **Available Lookup Columns** table. Selecting a column in the **Available Lookup Columns** table creates an output column that contains the reference table column value for each matching row returned.  
  
 **Output Alias**  
 Type an alias for the output for each lookup column. The default is the name of the lookup column with a numeric index value appended; however, you can choose any unique, descriptive name.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Fuzzy Lookup Transformation Editor &#40;Reference Table Tab&#41;](../Topic/Fuzzy%20Lookup%20Transformation%20Editor%20\(Reference%20Table%20Tab\).md)   
 [Fuzzy Lookup Transformation Editor &#40;Advanced Tab&#41;](../Topic/Fuzzy%20Lookup%20Transformation%20Editor%20\(Advanced%20Tab\).md)  
  
  