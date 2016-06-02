---
title: Import Domains from an Excel File in Knowledge Discovery
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - data-quality-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d3a3940-6c2a-4dc4-90eb-86f26012c165
---
# Import Domains from an Excel File in Knowledge Discovery
  This topic describes how to import one or more domains from an Excel file in the [!INCLUDE[ssDQSnoversion](../../Token\Other/ssDQSnoversion_md.md)] \(DQS\) knowledge discovery activity. The import process simplifies the knowledge generation process, saving time and effort. It enables people who have data in an Excel file or a text file to create a knowledge base with that data. \(See [Import Values from an Excel File into a Domain](../../Topics\TopicNameContainA/Import-Values-from-an-Excel-File-into-a-Domain.md) for more information about importing values into a domain of an existing knowledge base.\) Exporting to an Excel file is not supported.  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Prerequisites"></a> Prerequisites  
 To import domains from an Excel file, Excel must be installed on the computer that the [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] is installed on; you must have created an Excel file with domain values \(see [How the import works](#How)\); and you must have created and opened a knowledge base to import the domain into.  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Permissions  
 You must have the dqs\_kb\_editor or the dqs\_administrator role on the DQS\_MAIN database to import domains from an Excel file.  
  
##  <a name="Import"></a> Import domains from an Excel file into a knowledge base  
  
1.  [!INCLUDE[ssDQSInitialStep](../../Token\Other/ssDQSInitialStep_md.md)] [Run the Data Quality Client Application](../../Topics\TopicNameNotContainA/Run-the-Data-Quality-Client-Application.md).  
  
2.  In the [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] home screen, do one of the following:  
  
    -   Create a new knowledge base to import into by clicking **New knowledge base**, entering a name for the knowledge base, selecting **None** for **Create knowledge base from**, selecting the **Knowledge Discovery** activity, and then clicking **Create**.  
  
    -   Open an existing knowledge base to import into by clicking **Open knowledge base**, selecting the knowledge base, selecting **Knowledge Discovery**, and then clicking **Next**.  
  
3.  In the **Map** page, select **Excel File** for **Data Source**.  
  
4.  Click **Browse** on the **Excel File** line.  
  
5.  In the **Select an Excel File** dialog box, move to the folder that contains the Excel file that you want to import from, select the Excel file, and then click **Open**.  
  
6.  From the **Worksheet** drop\-down list, select the worksheet in the Excel file that you want to import from.  
  
7.  Select **Use First Row as header** if you want the first row to be considered a data header, and if you want the values in the first row to be used as column names. Deselect **Use First Row as header** if you want the first row to be considered a data value, in which case DQS will use the Excel header names \(alphabetical letters\) for the column.  
  
8.  Select a column, and then either map an existing domain to the column, or create a new domain by clicking the **Create a Domain** icon, creating a domain in the **Create a domain** dialog box, and then mapping the domain to the column. The data type of the domain must match the data type of the column. Repeat for all columns of the spreadsheet.  
  
9. Click **Next**.  
  
10. In the **Discover** page, click **Start** to analyze the data in the Excel spreadsheet.  
  
    > [!NOTE]  
    >  If you leave the page before the data has been uploaded, the file upload process will be terminated.  
  
11. Verify that the analysis completed successfully, and then click **Next**.  
  
12. In the **Manage Domain Values** page, verify that the correct domains are listed in the **Domains** list and that values are entered in the domain table.  
  
13. Click **Finish**, and then click **Publish** to publish the knowledge base, or **No** not to publish.  
  
14. Verify that the knowledge base was published, and then click **OK**.  
  
##  <a name="FollowUp"></a> Follow Up: After Importing Domains from an Excel File  
 After you import domains from an Excel file, you can add knowledge to the domains or use the domains in a cleansing or matching project, depending on the contents of the domains. For more information, see [Perform Knowledge Discovery](../../Topics\TopicNameNotContainA/Perform-Knowledge-Discovery.md), [Managing a Domain](../../Topics\TopicNameContainA/Managing-a-Domain.md), [Managing a Composite Domain](../../Topics\TopicNameContainA/Managing-a-Composite-Domain.md), [Create a Matching Policy](../../Topics\TopicNameContainA/Create-a-Matching-Policy.md), [Data Cleansing](../../Topics\TopicNameNotContainA/Data-Cleansing.md), or [Data Matching](../../Topics\TopicNameNotContainA/Data-Matching.md).  
  
##  <a name="How"></a> How the import works  
 In the import operation, DQS interprets an Excel file as follows:  
  
-   A column represents a domain  
  
-   A row represents a data record  
  
-   The first row either represents domain names or is the first data value or record, depending upon the setting of the **Use First Row as header** checkbox.  
  
 The following rules apply to the import operation:  
  
-   This operation imports domain values into a knowledge base. It does not import domain rules or a matching policy.  
  
-   The Excel file can have the extension .xlsx, .xls, or .csv. Microsoft Excel must be installed on the [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] computer to import domain values or a complete domain. Excel versions 2003 and later are supported. If the 64\-bit version of Excel is used, only Excel 2003 files will be supported; Excel 2007 or 2010 files will not be supported.  
  
-   Excel files of type .xlsx are not supported for an Excel 64\-bit installation. If you are using 64\-bit Excel, save the spreadsheet file as an .xls file.  
  
-   In .xlsx and .xls files, the data type of the column is determined by the most prevalent data type in the first eight rows. If a cell does not conform to that data type, it will be given a null value.  
  
-   In .csv files, the data type is determined by the most prevalent data type in the first eight rows.  
  
-   A value in an Excel spreadsheet that does not conform to a domain rule will be imported as an invalid value.  
  
-   If the Excel file is not in the right format or is corrupted, the import operation will result in an error.  
  
  