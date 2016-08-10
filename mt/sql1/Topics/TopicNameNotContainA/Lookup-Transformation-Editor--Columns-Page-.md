---
title: "Lookup Transformation Editor (Columns Page)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 690ffef5-fd59-4e95-a27d-4fcf0d6b1c0b
caps.latest.revision: 40
caps.handback.revision: 0
manager: jhubbard
---
# Lookup Transformation Editor (Columns Page)
Use the **Columns** page of the **Lookup Transformation Editor** dialog box to specify the join between the source table and the reference table, and to select lookup columns from the reference table.  
  
 To learn more about the Lookup transformation, see [Lookup Transformation](../../Topics/TopicNameNotContainA/Lookup-Transformation.md).  
  
## Options  
 **Available Input Columns**  
 View the list of available input columns. The input columns are the columns in the data flow from a connected source. The input columns and lookup column must have matching data types.  
  
 Use a drag-and-drop operation to map available input columns to lookup columns.  
  
 You can also map input columns to lookup columns using the keyboard, by highlighting a column in the **Available Input Columns** table, pressing the Application key, and then clicking **Edit Mappings**.  
  
 **Available Lookup Columns**  
 View the list of lookup columns. The lookup columns are columns in the reference table in which you want to look up values that match the input columns.  
  
 Use a drag-and-drop operation to map available lookup columns to input columns.  
  
 Use the check boxes to select lookup columns in the reference table on which to perform lookup operations.  
  
 You can also map lookup columns to input columns using the keyboard, by highlighting a column in the **Available Lookup Columns** table, pressing the Application key, and then clicking **Edit Mappings**.  
  
 **Lookup Column**  
 View the selected lookup columns. The selections are reflected in the check box selections in the **Available Lookup Columns** table.  
  
 **Lookup Operation**  
 Select a lookup operation from the list to perform on the lookup column.  
  
 **Output Alias**  
 Type an alias for the output for each lookup column. The default is the name of the lookup column; however, you can select any unique, descriptive name.  
  
## See Also  
 [Lookup Transformation Editor (General Page)](../../Topics/TopicNameNotContainA/Lookup-Transformation-Editor--General-Page-.md)   
 [Lookup Transformation Editor (Connection Page)](../../Topics/TopicNameNotContainA/Lookup-Transformation-Editor--Connection-Page-.md)   
 [Lookup Transformation Editor (Advanced Page)](../../Topics/TopicNameNotContainA/Lookup-Transformation-Editor--Advanced-Page-.md)   
 [Lookup Transformation Editor (Error Output Page)](../../Topics/TopicNameNotContainA/Lookup-Transformation-Editor--Error-Output-Page-.md)   
 [Fuzzy Lookup Transformation](../../Topics/TopicNameNotContainA/Fuzzy-Lookup-Transformation.md)