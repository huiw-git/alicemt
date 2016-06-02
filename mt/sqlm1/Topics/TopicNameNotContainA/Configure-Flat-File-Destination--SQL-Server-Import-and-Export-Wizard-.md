---
title: Configure Flat File Destination (SQL Server Import and Export Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 318e8da0-37d3-46cd-943a-fc5d66aad93a
---
# Configure Flat File Destination (SQL Server Import and Export Wizard)
  If you selected a flat file destination, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard shows **Configure Flat File Destination** after you specify that  you want to copy an entire table or after you provide a query. On this page, you specify formatting options for the destination flat file. Optionally you choose columns and preview sample data.  
  
> [!TIP]  
>  There is no option to specify a custom row delimiter or column delimiter on this page. If your flat file contains a custom delimiter, and you want to continue to use the wizard, consider whether you can do a global search and replace operation in the flat file to replace the existing delimiter with one of the delimiters recognized by the wizard.  
  
 For more info about the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard and how it works, see [SQL Server Import and Export Wizard](../../Topics\TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md).  
  
## Screen shot  
 The following screen shot shows the **Configure Flat File Destination** page of the Wizard.  
  
 ![Configure flat file page of the Import and Export Wizard](../../Images\Image\ImageNotContaina/Flat-file.png "Flat file")  
  
## Options on this page  
 **Source table or view**  
 The name of the table or view.  
  
 **Row delimiter**  
 Select from the list of delimiters for rows. There is no option to specify a custom row delimiter.  
  
|Value|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|The row is delimited by a carriage return\-line feed combination.|  
|**{CR}**|The row is delimited by a carriage return.|  
|**{LF}**|The row is delimited by a line feed.|  
|**Semicolon {;}**|The row is delimited by a semicolon.|  
|**Colon {:}**|The row is delimited by a colon.|  
|**Comma {,}**|The row is delimited by a comma.|  
|**Tab {t}**|The row is delimited by a tab.|  
|**Vertical bar {&#124;}**|The row is delimited by a vertical bar.|  
  
 **Column delimiter**  
 Select from the list of delimiters for columns. There is no option to specify a custom column delimiter.  
  
|Value|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|The columns are delimited by a carriage return\-line feed combination.|  
|**{CR}**|The columns are delimited by a carriage return.|  
|**{LF}**|The columns are delimited by a line feed.|  
|**Semicolon {;}**|The columns are delimited by a semicolon.|  
|**Colon {:}**|The columns are delimited by a colon.|  
|**Comma {,}**|The columns are delimited by a comma.|  
|**Tab {t}**|The columns are delimited by a tab.|  
|**Vertical bar {&#124;}**|The columns are delimited by a vertical bar.|  
  
## What's next?  
 After you specify formatting options for the destination flat file, the next page depends on the option that you choose.  
  
-   Optionally click **Edit mappings** to display the **Column Mappings** dialog box. Use the **Column Mappings** dialog box to specify destination columns to receive the source data. You can copy only a subset of columns by selecting **ignore** in the **Destination** column of the **Column Mappings** dialog box for columns that you don't want to copy. For more info, see [Column Mappings &#40;SQL Server Import and Export Wizard&#41;](Column%20Mappings%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).  
  
-   Optionally click **Preview** to preview up to 200 rows of sample data in the **Preview Data** dialog box. This helps you to confirm that the wizard is going to copy the data that you want to copy. For more info, see [Preview Data &#40;SQL Server Import and Export Wizard&#41;](Preview%20Data%20Dialog%20Box%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).  
  
     After you preview the data, you may want to change the options that you selected on previous pages of the wizard. To make these changes, on the **Select Source Tables and Views** page, click **Back** to return to previous pages where you can change your selections.  
  
-   If you don't display one of the optional dialog boxes, the next page is **Save and Execute Package**. On this page, you specify whether you want to run the copy operation immediately. Depending on your configuration, you may also be able to save the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)][!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package created by the wizard  to customize it and to reuse it. For more info, see [Save and Run Package &#40;SQL Server Import and Export Wizard&#41;](../Topic/Save%20and%20Run%20Package%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).  
  
  