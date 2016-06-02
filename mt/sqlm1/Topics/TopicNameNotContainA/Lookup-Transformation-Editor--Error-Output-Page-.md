---
title: Lookup Transformation Editor (Error Output Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 15d53bb0-8be1-46fb-b459-04a397e75fac
---
# Lookup Transformation Editor (Error Output Page)
  Use the **Error Output** page of the **Lookup Transformation Editor** dialog box to specify error handling options.  
  
 To learn more about the Lookup transformation, see [Lookup Transformation](../../Topics\TopicNameNotContainA/Lookup-Transformation.md).  
  
## Options  
 **Input\/Output**  
 View the name of the input.  
  
 **Column**  
 Not used.  
  
 **Error**  
 Specify what type of error should occur when handling rows without matching entries in the reference dataset:  
  
-   Ignore the failure and direct the rows to an output.  
  
-   Redirect the rows to an error output.  
  
-   Fail the component.  
  
 This option is not available when you select **Redirect rows to no match output** in the **Specify how to handle rows with no matching entries** list. This list is on the **General** page of the **Lookup Transformation Editor** dialog box.  
  
 **Related Topics:** [Error Handling in Data](../../Topics\TopicNameNotContainA/Error-Handling-in-Data.md)  
  
 **Truncation**  
 Specify what should happen when data truncation occurs:  
  
-   Ignore the failure.  
  
-   Redirect the row.  
  
-   Fail the component.  
  
 **Description**  
 View the description of the operation.  
  
 **Set selected cells to this value**  
 Specify what should happen to all the selected cells when an error or truncation occurs:  
  
-   Ignore the failure.  
  
-   Redirect the row.  
  
-   Fail the component.  
  
 **Apply**  
 Apply the error handling option to the selected cells.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)  
  
  