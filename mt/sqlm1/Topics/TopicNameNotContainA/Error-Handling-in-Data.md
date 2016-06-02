---
title: Error Handling in Data
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c61667b4-25cb-4d45-a52f-a733e32863f4
---
# Error Handling in Data
  When a data flow component applies a transformation to column data, extracts data from sources, or loads data into destinations, errors can occur. Errors frequently occur because of unexpected data values. For example, a data conversion fails because a column contains a string instead of a number, an insertion into a database column fails because the data is a date and the column has a numeric data type, or an expression fails to evaluate because a column value is zero, resulting in a mathematical operation that is not valid.  
  
 Errors typically fall into one the following categories:  
  
-   Data conversion errors, which occur if a conversion results in loss of significant digits, the loss of insignificant digits, and the truncation of strings. Data conversion errors also occur if the requested conversion is not supported.  
  
-   Expression evaluation errors, which occur if expressions that are evaluated at run time perform invalid operations or become syntactically incorrect because of missing or incorrect data values.  
  
-   Lookup errors, which occur if a lookup operation fails to locate a match in the lookup table.  
  
 For a list of Integration Services errors, warnings, and other messages, see [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md).  
  
## Use error outputs to capture row\-level errors  
 Many data flow components support error outputs, which let you control how the component handles row\-level errors in both incoming and outgoing data. You specify how the component behaves when truncation or an error occurs by setting options on individual columns in the input or output. For example, you can specify that the component should fail if customer name data is truncated, but ignore errors on another column that contains less important data.  
  
 The error output can be connected to the input of another transformation or loaded into a different destination than the non\-error output. For example, the error output can be a connected to a Derived Column transformation that provides a string for a column that is blank.  
  
 The following diagram shows a simple data flow including an error output.  
  
 ![Data flow with error output](../../Images\Image\ImageNotContaina/MW_DTS_11.gif "MW_DTS_11")  
  
 For more information, see [Data Flow](../../Topics\TopicNameNotContainA/Data-Flow.md) and [Integration Services Paths](../../Topics\TopicNameNotContainA/Integration-Services-Paths.md).  
  
## Errors are either failures or truncations  
 Errors fall into one of two categories: errors or truncations.  
  
 **Errors**. An error indicates an unequivocal failure, and generates a NULL result. Such errors can include data conversion errors or expression evaluation errors. For example, an attempt to convert a string that contains alphabetical characters to a number causes an error. Data conversions, expression evaluations, and assignments of expression results to variables, properties, and data columns may fail because of illegal casts and incompatible data types. For more information see, [Cast &#40;SSIS Expression&#41;](../Topic/Cast%20\(SSIS%20Expression\).md), [Integration Services Data Types in Expressions](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types-in-Expressions.md), and [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
 **Truncations**. A truncation is less serious than an error. A truncation generates results that might be usable or even desirable. You can elect to treat truncations as errors or as acceptable conditions. For example, if you are inserting a 15\-character string into a column that is only one character wide, you can elect to truncate the string.  
  
## Select an error handling option  
 You can configure how sources, transformations, and destinations handle errors and truncations. The following table describes the options.  
  
|Option|Description|  
|------------|-----------------|  
|Fail Component|The Data Flow task fails when an error or a truncation occurs. Failure is the default option for an error and a truncation.|  
|Ignore Failure|The error or the truncation is ignored and the data row is directed to the output of the transformation or source.|  
|Redirect Row|The error or the truncation data row is directed to the error output of the source, transformation, or destination.|  
  
## Get more info about the error  
 In addition to the data columns, the error output includes the **ErrorCode** and **ErrorColumn** columns. The **ErrorCode** column identifies the error and the **ErrorColumn** contains the lineage identifier of the error column.  
  
 Under some circumstances, the value of the **ErrorColumn** column is set to zero. This occurs when the error condition affects the entire row instead of a single column. An example is when a lookup fails in the Lookup transformation.  
  
 These two numeric values may be of limited use without the corresponding error description and column name. Here are some ways to get the error description and column name.  
  
-   You can see both error descriptions and column names by attaching a Data Viewer to the error output. In SSIS Designer, right\-click on the red arrow leading to an error output and select **Enable Data Viewer**.  
  
-   You can find column names by enabling logging and selecting the **DiagnosticEx** event. This event writes a data flow column map to the log. You can then look up the column name from its identifier in this column map. Note that the **DiagnosticEx** event does not preserve whitespace in its XML output to reduce the size of the log. To improve readability, copy the log into an XML editor \- in Visual Studio, for example \- that supports XML formatting and syntax highlighting. For more info about logging, see [Integration Services &#40;SSIS&#41; Logging](../Topic/Integration%20Services%20\(SSIS\)%20Logging.md).  
  
     Here is an example of a data flow column map.  
  
    ```xml  
  
    <DTS:PipelineColumnMap xmlns:DTS="www.microsoft.com/SqlServer/Dts">  
        <DTS:Pipeline DTS:Path="\Package\Data Flow Task">  
            <DTS:Column DTS:ID="11" DTS:IdentificationString="ADO NET Source.Outputs[ADO NET Source Output].Columns[Customer]"/>  
            <DTS:Column DTS:ID="12" DTS:IdentificationString="ADO NET Source.Outputs[ADO NET Source Output].Columns[Product]"/>  
            <DTS:Column DTS:ID="13" DTS:IdentificationString="ADO NET Source.Outputs[ADO NET Source Output].Columns[Price]"/>  
            <DTS:Column DTS:ID="14" DTS:IdentificationString="ADO NET Source.Outputs[ADO NET Source Output].Columns[Timestamp]"/>  
            <DTS:Column DTS:ID="20" DTS:IdentificationString="ADO NET Source.Outputs[ADO NET Source Error Output].Columns[Customer]"/>  
            <DTS:Column DTS:ID="21" DTS:IdentificationString="ADO NET Source.Outputs[ADO NET Source Error Output].Columns[Product]"/>  
            <DTS:Column DTS:ID="22" DTS:IdentificationString="ADO NET Source.Outputs[ADO NET Source Error Output].Columns[Price]"/>  
            <DTS:Column DTS:ID="23" DTS:IdentificationString="ADO NET Source.Outputs[ADO NET Source Error Output].Columns[Timestamp]"/>  
            <DTS:Column DTS:ID="24" DTS:IdentificationString="ADO NET Source.Outputs[ADO NET Source Error Output].Columns[ErrorCode]"/>  
            <DTS:Column DTS:ID="25" DTS:IdentificationString="ADO NET Source.Outputs[ADO NET Source Error Output].Columns[ErrorColumn]"/>  
            <DTS:Column DTS:ID="31" DTS:IdentificationString="Flat File Destination.Inputs[Flat File Destination Input].Columns[Customer]"/>  
            <DTS:Column DTS:ID="32" DTS:IdentificationString="Flat File Destination.Inputs[Flat File Destination Input].Columns[Product]"/>  
            <DTS:Column DTS:ID="33" DTS:IdentificationString="Flat File Destination.Inputs[Flat File Destination Input].Columns[Price]"/>  
            <DTS:Column DTS:ID="34" DTS:IdentificationString="Flat File Destination.Inputs[Flat File Destination Input].Columns[Timestamp]"/>  
        </DTS:Pipeline>  
    </DTS:PipelineColumnMap>  
  
    ```  
  
-   You can also use the Script component to include the error description and the column name in additional columns of the error output. For an example, see [Enhancing an Error Output with the Script Component](../Topic/Enhancing%20an%20Error%20Output%20with%20the%20Script%20Component.md).  
  
    -   Include the error description in an additional column by using a single line of script to call the [GetErrorDescription](assetId:///M:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription(System.Int32)) method of the [IDTSComponentMetaData100](assetId:///T:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100) interface.  
  
    -   Include the column name in an additional column by using a single line of script to call the [GetIdentificationStringByID](assetId:///M:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetIdentificationStringByID(System.Int32)) method of the [IDTSComponentMetaData100](assetId:///T:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100) interface.  
  
     You can add the Script component to the error segment of the data flow anywhere downstream from the data flow components whose errors you want to capture. Typically you place the Script component immediately before the error rows are written to a destination. This way, the script looks up descriptions only for error rows that are written. The error segment of the data flow may correct some errors and not write those rows to an error destination.  
  
### To configure an error output  
  
-   [Configure an Error Output in a Data Flow Component](../../Topics\TopicNameContainA/Configure-an-Error-Output-in-a-Data-Flow-Component.md)  
  
## See Also  
 [Data Flow](../../Topics\TopicNameNotContainA/Data-Flow.md)   
 [Transform Data with Transformations](../../Topics\TopicNameNotContainA/Transform-Data-with-Transformations.md)   
 [Connect Components with Paths](../../Topics\TopicNameNotContainA/Connect-Components-with-Paths.md)   
 [Data Flow Task](../../Topics\TopicNameNotContainA/Data-Flow-Task.md)   
 [Data Flow](../../Topics\TopicNameNotContainA/Data-Flow.md)  
  
  