---
title: Excel Destination
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 37c07446-1264-4814-b4f5-9c66d333bb24
---
# Excel Destination
  The Excel destination loads data into worksheets or ranges in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Excel workbooks.  
  
## Access Modes  
 The Excel destination provides three different data access modes for loading data:  
  
-   A table or view.  
  
-   A table or view specified in a variable.  
  
-   The results of an SQL statement. The query can be a parameterized query.  
  
> [!IMPORTANT]  
>  In Excel, a worksheet or range is the equivalent of a table or view. The lists of available tables in the Excel Source and Destination editors display only existing worksheets \(identified by the $ sign appended to the worksheet name, such as Sheet1$\) and named ranges \(identified by the absence of the $ sign, such as MyRange\).  
  
## Usage Considerations  
 The Excel Connection Manager uses the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] OLE DB Provider for Jet 4.0 and its supporting Excel ISAM \(Indexed Sequential Access Method\) driver to connect and read and write data to Excel data sources.  
  
 Many existing [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Knowledge Base articles document the behavior of this provider and driver, and although these articles are not specific to [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] or its predecessor Data Transformation Services, you may want to know about certain behaviors that can lead to unexpected results. For general information on the use and behavior of the Excel driver, see [HOWTO: Use ADO with Excel Data from Visual Basic or VBA](http://support.microsoft.com/kb/257819).  
  
 The following behaviors of the Jet provider that is included with the Excel driver can lead to unexpected results when saving data to an Excel destination.  
  
-   **Saving text data**. When the Excel driver saves text data values to an Excel destination, the driver precedes the text in each cell with the single quote character \('\) to ensure that the saved values will be interpreted as text values. If you have or develop other applications that read or process the saved data, you may need to include special handling for the single quote character that precedes each text value.  
  
     For information on how to avoid including the single quote, see this blog post, [Single quote is appended to all strings when data is transformed to excel when using Excel destination data flow component in SSIS package](http://go.microsoft.com/fwlink/?LinkId=400876), on msdn.com.  
  
-   **Saving memo \(ntext\) da**ta. Before you can successfully save strings longer than 255 characters to an Excel column, the driver must recognize the data type of the destination column as **memo** and not **string**. If the destination table already contains rows of data, then the first few rows that are sampled by the driver must contain at least one instance of a value longer than 255 characters in the memo column. If the destination table is created during package design or at run time, then the CREATE TABLE statement must use LONGTEXT \(or one of its synonyms\) as the data type of the the memo column.  
  
-   **Data types**. The Excel driver recognizes only a limited set of data types. For example, all numeric columns are interpreted as doubles \(DT\_R8\), and all string columns \(other than memo columns\) are interpreted as 255\-character Unicode strings \(DT\_WSTR\). [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] maps the Excel data types as follows:  
  
    -   Numeric    double\-precision float \(DT\_R8\)  
  
    -   Currency     currency \(DT\_CY\)  
  
    -   Boolean     Boolean \(DT\_BOOL\)  
  
    -   Date\/time     **datetime** \(DT\_DATE\)  
  
    -   String     Unicode string, length 255 \(DT\_WSTR\)  
  
    -   Memo     Unicode text stream \(DT\_NTEXT\)  
  
-   **Data type and length conversions**. [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] does not implicitly convert data types. As a result, you may need to use the Derived Column or Data Conversion transformations to convert Excel data explicitly before loading it into a non\-Excel destination, or to convert non\-Excel data before loading it into an Excel destination. In this case, it may be useful to create the initial package by using the Import and Export Wizard, which configures the necessary conversions for you. Some examples of the conversions that may be required include the following:  
  
    -   Conversion between Unicode Excel string columns and non\-Unicode string columns with specific codepages.  
  
    -   Conversion between 255\-character Excel string columns and string columns of different lengths.  
  
    -   Conversion between double\-precision Excel numeric columns and numeric columns of other types.  
  
## Configuration of the Excel Destination  
 The Excel destination uses an Excel connection manager to connect to a data source, and the connection manager specifies the workbook file to use. For more information, see [Excel Connection Manager](../../Topics\TopicNameNotContainA/Excel-Connection-Manager.md).  
  
 The Excel destination has one regular input and one error output.  
  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in the **Excel Destination Editor** dialog box, click one of the following topics:  
  
-   [Excel Destination Editor &#40;Connection Manager Page&#41;](../Topic/Excel%20Destination%20Editor%20\(Connection%20Manager%20Page\).md)  
  
-   [Excel Destination Editor &#40;Mappings Page&#41;](../Topic/Excel%20Destination%20Editor%20\(Mappings%20Page\).md)  
  
-   [Excel Destination Editor &#40;Error Output Page&#41;](../Topic/Excel%20Destination%20Editor%20\(Error%20Output%20Page\).md)  
  
 The **Advanced Editor** dialog box reflects all the properties that can be set programmatically. For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:  
  
-   [Common Properties](../../Topics\TopicNameNotContainA/Common-Properties.md)  
  
-   [Excel Custom Properties](../../Topics\TopicNameNotContainA/Excel-Custom-Properties.md)  
  
 For more information about how to set properties, see [Set the Properties of a Data Flow Component](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Data-Flow-Component.md).  
  
## Related Tasks  
  
-   [Connect to an Excel Workbook](../../Topics\TopicNameNotContainA/Connect-to-an-Excel-Workbook.md)  
  
-   [Loop through Excel Files and Tables by Using a Foreach Loop Container](../../Topics\TopicNameContainA/Loop-through-Excel-Files-and-Tables-by-Using-a-Foreach-Loop-Container.md)  
  
-   [Set the Properties of a Data Flow Component](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Data-Flow-Component.md)  
  
## Related Content  
  
-   Blog entry, [Excel in Integration Services, Part 1 of 3: Connections and Components](http://go.microsoft.com/fwlink/?LinkId=217674), on dougbert.com  
  
-   Blog entry, [Excel in Integration Services, Part 2 of 3: Tables and Data Types](http://go.microsoft.com/fwlink/?LinkId=217675), on dougbert.com.  
  
-   Blog entry, [Excel in Integration Services, Part 3 of 3: Issues and Alternatives](http://go.microsoft.com/fwlink/?LinkId=217676), on dougbert.com.  
  
## See Also  
 [Excel Source](../../Topics\TopicNameNotContainA/Excel-Source.md)   
 [Integration Services &#40;SSIS&#41; Variables](../Topic/Integration%20Services%20\(SSIS\)%20Variables.md)   
 [Data Flow](../../Topics\TopicNameNotContainA/Data-Flow.md)   
 [Working with Excel Files with the Script Task](../Topic/Working%20with%20Excel%20Files%20with%20the%20Script%20Task.md)  
  
  