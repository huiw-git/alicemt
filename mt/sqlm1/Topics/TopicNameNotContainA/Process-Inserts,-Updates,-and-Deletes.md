---
title: Process Inserts, Updates, and Deletes
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 13a84d21-2623-4efe-b442-4125a7a2d690
---
# Process Inserts, Updates, and Deletes
  In the data flow of an Integration Services package that performs an incremental load of change data, the second task is to separate inserts, updates, and deletes. Then, you can use appropriate commands to apply them to the destination.  
  
> [!NOTE]  
>  The first task in designing the data flow of a package that performs an incremental load of change data is to configure the source component that runs the query that retrieves the change data. For more information about this component, see [Retrieve and Understand the Change Data](../../Topics\TopicNameNotContainA/Retrieve-and-Understand-the-Change-Data.md). For a description of the overall process for creating a package that performs an incremental load of change data, see [Change Data Capture &#40;SSIS&#41;](../Topic/Change%20Data%20Capture%20\(SSIS\).md).  
  
## Associating Friendly Values to Separate Inserts, Updates, and Deletes  
 In the example query that retrieves change data, the **cdc.fn\_cdc\_get\_net\_changes\_\<capture\_instance\>** function returns only the column of metadata named **\_\_$operation**. This metadata column contains an ordinal value that indicates which operation caused the change.  
  
> [!NOTE]  
>  For more information about the query that uses calls the **cdc.fn\_cdc\_get\_net\_changes\_\<capture\_instance\>** function, see [Create the Function to Retrieve the Change Data](../../Topics\TopicNameNotContainA/Create-the-Function-to-Retrieve-the-Change-Data.md).  
  
 Matching an ordinal value to its corresponding operation is not as easy as using a mnemonic of the operation. For example, 'D' can easily represent a delete operation and 'I' represent an insert operation. The example query that was created in the topic, [Creating the Function to Retrieve the Change Data](../../Topics\TopicNameNotContainA/Create-the-Function-to-Retrieve-the-Change-Data.md), makes this conversion from an ordinal value to a friendly string value that is returned in a new column. The following segment of code shows this conversion:  
  
```  
select   
    ...  
    case __$operation  
        when 1 then 'D'  
        when 2 then 'I'  
        when 4 then 'U'  
        else null  
     end as CDC_OPERATION  
```  
  
## Configuring a Conditional Split Transformation to Direct Inserts, Updates, and Deletes  
 To direct rows of change data to one of three outputs, the Conditional Split transformation is ideal. The transformation just checks the value of the **CDC\_OPERATION** column in each row and determines whether that change was an insert, update, or delete.  
  
> [!NOTE]  
>  The CDC\_OPERATION column contains a friendly string value derived from the numeric value in the **\_\_$operation** column.  
  
#### To split inserts, updates, and deletes for processing by using a Conditional Split transformation  
  
1.  On the **Data Flow** tab, add a Conditional Split transformation.  
  
2.  Connect the output of the OLE DB source to the Conditional Split transformation.  
  
3.  In the **Conditional Split Transformation Editor**, in the lower pane of the editor, enter the following three lines to designate the three outputs  
  
    1.  Enter a line with the condition `CDC_OPERATION == "I"` to direct inserted rows to the output for inserts.  
  
    2.  Enter a line with the condition `CDC_OPERATION == "U"` to direct updated rows to the output for updates.  
  
    3.  Enter a line with the condition `CDC_OPERATION == "D"` to direct deleted rows to the output for deletes.  
  
## Next Step  
 After you split the rows for processing, the next step is to apply the changes to the destination.  
  
 **Next topic:** [Apply the Changes to the Destination](../../Topics\TopicNameNotContainA/Apply-the-Changes-to-the-Destination.md)  
  
## See Also  
 [Conditional Split Transformation](../../Topics\TopicNameNotContainA/Conditional-Split-Transformation.md)   
 [Split a Dataset by Using the Conditional Split Transformation](../../Topics\TopicNameContainA/Split-a-Dataset-by-Using-the-Conditional-Split-Transformation.md)  
  
  