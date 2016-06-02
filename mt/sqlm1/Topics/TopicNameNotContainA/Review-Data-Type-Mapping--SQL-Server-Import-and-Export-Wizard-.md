---
title: Review Data Type Mapping (SQL Server Import and Export Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0625c4f9-b8ff-4593-b884-39398b9d43af
---
# Review Data Type Mapping (SQL Server Import and Export Wizard)
  If you specified a mapping that's not valid in the **Mappings** list of the **Column Mappings** dialog box, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard shows the **Review Data Type Mapping** page. On this page, you can review detailed information about data type conversions that the wizard has to perform to make the source data compatible with the destination. This information includes visual cues to distinguish conversions that are expected to succeed from conversions that might cause errors or truncations. For each conversion, you can decide whether to accept the conversion that the wizard suggests, and you can specify how to handle any errors that occur.  
    
  > [!TIP]  
>  You can't change data type mappings on the **Review Data Type Mapping** page. However, you can click **Back** to return to the **Select Source Tables and Views** page, and then click **Edit Mappings** to open the **Column Mappings** dialog box again. In the **Column Mappings** dialog box  you can specify data type mappings that are more likely to succeed.  
  
 For more info about how the wizard maps data types from source columns to destination columns, see [How the Wizard maps data types from source to destination](../../Topics\TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md).  
  
 For more info about the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard and how it works, see [SQL Server Import and Export Wizard](../../Topics\TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md).  
  
## Screen shot  
 The following screen shot shows the **Review Data Type Mapping** page of the Wizard after the user has specified an invalid mapping in the **Column Mappings** dialog box. To take another look at the **Column Mappings** dialog box, see [Column Mappings &#40;SQL Server Import and Export Wizard&#41;](Column%20Mappings%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).  
  
 ![Review Data Type Mapping page of the Import and Export Wizard](../../Images\Image\ImageNotContaina/Review-mapping.png "Review mapping")  
  
## Options on this page  
 The **Review Data Type Mapping** page consists of a **Table** list, a **Data type mapping** list, and error handling options.  
  
### Table list  
 The upper part of the **Review Data Type Mapping** page is a **Table** list that lists the tables to be copied from the source to the destination. To see conversion information about an individual table, select a table in the **Table** list. The conversion information for the selected table appears in the columns in the **Data type mapping** grid in the lower part of the page.  
  
 The following table describes the columns in the **Table** list.  
  
|Column|Description|  
|------------|-----------------|  
|Source icon|Indicates the probability of success for the data type conversions:<br /><br /> -   A green check mark icon indicates that the wizard expects all data type conversions for this table to succeed.<br />-   A yellow warning icon indicates that you should review the individual conversions that the wizard will perform. To review these conversions, select the table, and then review the conversions for individual columns in the **Data type mapping** list.<br />-   A red error icon indicates that the wizard is not able to perform some of the conversions for this table reliably.|  
|**Source**|Displays the name of the source table.|  
|Destination icon|Indicates whether the destination already exists or will be created by the wizard:<br /><br /> -   A table icon indicates that the destination is an existing table.<br />-   A table icon with a sunburst indicates that the destination is a new table that the wizard will create.|  
|**Destination**|Displays the name of the destination table.|  
  
### Data type mapping list  
 The lower part of the **Review Data Type Mapping** page is the **Data type mapping** list. This grid provides detailed conversion information about the columns in the table that is selected in the **Table** list.  
  
 The following table describes the columns in the **Data type mapping** list.  
  
|Column|Description|  
|------------|-----------------|  
|Conversion icon|Indicates the probability of success for the data type conversions:<br /><br /> -   A green check mark icon indicates that the wizard expects that the data type conversion for this column to succeed.<br />-   A yellow warning icon indicates that you should review the conversion that the wizard will perform. To review the conversion, double\-click on the column to view the **Column Conversion Details** dialog box.<br />-   A red error icon indicates that the wizard is not able to perform the conversion reliably.|  
|**Source Column**|Displays the name of the source column.|  
|**Source Type**|Displays the data type of the source column.|  
|**Destination Column**|Displays the name of the destination column.|  
|**Destination Type**|Displays the data type of the destination column.|  
|**Convert**|Specify whether the planned conversion should continue:<br /><br /> -   Select the check box to have the wizard continue with the planned conversion.<br />-   Clear the check box to cancel the data type conversion.|  
|**On Error**|Specify how the wizard handles errors:<br /><br /> -   Use the **On Error \(global\)** setting, which you can specify at the bottom of this page.<br />-   Fail with an error, and stop the import or export process.<br />-   Ignore the error.|  
|**On Truncation**|Specify how the wizard handles truncation:<br /><br /> -   Use the **On Truncation \(global\)** setting, which you can specify at the bottom of this page.<br />-   Fail with an error, and stop the import or export process<br />-   Ignore the truncation.|  
  
 To view detailed information about the conversion of a particular column of data, double\-click any row in the list. The **Column Conversion Details** dialog box opens and displays more detailed conversion information for the column.  
  
### Error handling options  
 **On Error \(global\)**  
 Specify how the wizard handles errors:  
  
-   Fail with an error, and stop the import or export process.  
  
-   Ignore the error, and continue the import or export process.  
  
 This setting applies to all conversions that have **Use Global** selected in the **On Error** column of the **Data type mapping** list.  
  
 **On Truncation \(global\)**  
 Specify how the wizard handles data truncation:  
  
-   Fail with an error, and stop the import or export process.  
  
-   Ignore the truncation, and continue the import or export process.  
  
 This setting applies to all conversions that have **Use Global** selected in the **On Truncation** column of the **Data type mapping** list.  
  
## What's next?  
 After you review the warnings, specify conversion options, and specify how to handle errors, the **Review Data Type Mapping** page takes you back to the **Column Mappings** dialog box. For more info, see [Column Mappings &#40;SQL Server Import and Export Wizard&#41;](Column%20Mappings%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).  
  
 If you If you double\-click the row for an individual column in the **Data type mapping** list, then the **Review Data Type Mapping** dialog box opens the **Column Conversion Details** dialog box. On this page, you can review detailed conversion information for an individual column. For more info, see [Column Conversion Details Dialog Box &#40;SQL Server Import and Export Wizard&#41;](../Topic/Column%20Conversion%20Details%20Dialog%20Box%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).  
  
  