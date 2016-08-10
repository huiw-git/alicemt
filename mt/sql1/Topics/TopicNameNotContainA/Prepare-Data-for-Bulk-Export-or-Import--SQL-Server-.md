---
title: "Prepare Data for Bulk Export or Import (SQL Server)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-bulk-import-export
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 783fd581-2e5f-496b-b79c-d4de1e09ea30
caps.latest.revision: 52
caps.handback.revision: 0
manager: jhubbard
---
# Prepare Data for Bulk Export or Import (SQL Server)
This section discusses the considerations involved in planning for bulk-export operations and the requirements for bulk-import operations.  
  
> [!NOTE]  
>  If you are uncertain about how to format a data file for bulk importing,  use the **bcp** utility to export data from the table into a data file. The formatting of each data field in this file shows the formatting required to bulk import data into the corresponding table column. Use the same data formatting for fields of your data file.  
  
## Data-File Format Considerations for Bulk Export  
 Before you perform a bulk-export operation by using the **bcp** command, consider the following:  
  
-   When data is exported to a file, the **bcp** command creates the data file automatically by using the specified file name. If that file name is already in use, the data that is being bulk copied to the data file overwrites the existing contents of the file.  
  
-   Bulk export from a table or view to a data file requires SELECT permission on the table or view that is being bulk copied.  
  
-   [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] can use parallel scans to retrieve data. Therefore, the table rows that are bulk exported in from an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] are not ordinarily guaranteed to be in any specific order in the data file. To make bulk-exported table rows appear in a specific order in the data file, use the **queryout** option to bulk export from a query, and specify an ORDER BY clause.  
  
## Data-File Format Requirements for Bulk Import  
 To import data from a data file, the file must meet the following basic requirements:  
  
-   The data must be in row and column format.  
  
> [!NOTE]  
>  The structure of the data file does not need to be identical to the structure of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] table because columns can be skipped or reordered during the bulk-import process.  
  
-   The data in the data file must be in a supported format such as character or native format.  
  
-   The data can be in character or native binary format including Unicode.  
  
-   To import data by using a **bcp** command, BULK INSERT statement, or INSERT ... SELECT * FROM OPENROWSET(BULK...) statement, the destination table must already exist.  
  
-   Each field in the data file must be compatible with the corresponding column in the target table. For example, an **int** field cannot be loaded into a **datetime** column. For more information, see [Data Formats for Bulk Import or Bulk Export (SQL Server)](../../Topics/TopicNameNotContainA/Data-Formats-for-Bulk-Import-or-Bulk-Export--SQL-Server-.md) and [Specify Data Formats for Compatibility when Using bcp (SQL Server)](../../Topics/TopicNameNotContainA/Specify-Data-Formats-for-Compatibility-when-Using-bcp--SQL-Server-.md).  
  
    > [!NOTE]  
    >  To specify a subset of rows to import from a data file rather than the entire file, you can use a **bcp** command with the **-F** *first_row* switch and/or **-L** *last_row* switch. For more information, see [bcp Utility](../../Topics/TopicNameNotContainA/bcp-Utility.md).  
  
-   To import data from data files with fixed-length or fixed-width fields, use a format file. For more information, see [XML Format Files (SQL Server)](../../Topics/TopicNameNotContainA/XML-Format-Files--SQL-Server-.md).  
  
-   Comma-separated value (CSV) files are not supported by [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] bulk-import operations. However, in some cases, a CSV file can be used as the data file for a bulk import of data into [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. Note that the field terminator of a CSV file does not have to be a comma. To be usable as a data file for bulk import, a CSV file must comply with the following restrictions:  
  
    -   Data fields never contain the field terminator.  
  
    -   Either none or all of the values in a data field are enclosed in quotation marks ("").  
  
     To bulk import data from a [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] FoxPro or Visual FoxPro table (.dbf) file or a [!INCLUDE[ofprexcel](../../Topics/TopicNameContainA/tokens/ofprexcel_md.md)] worksheet (.xls) file, you would need to convert the data into a CSV file that complies to the preceding restrictions. The file extension will typically be .csv. You can then use the .csv file as a data file in a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] bulk-import operation.  
  
     On 32-bit systems, it is possible to import CSV data into a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] table without bulk-import optimizations by using [OPENROWSET](assetId:///f47eda43-33aa-454d-840a-bb15a031ca17) with the OLE DB Provider for Jet. Jet treats text files as tables, with the schema defined by a schema.ini file that is located in the same directory as the data source.  For a CSV data, one of the parameters in the schema.ini file would be "FORMAT=CSVDelimited". To use this solution, you would need to understand how the Jet Test IISAMm operations—its connection string syntax, schema.ini usage, registry setting options, and so on).  The best sources of this information are Microsoft Access Help and Knowledge Base (KB) articles. For more information, see [Initializing the Text Data Source Driver](http://go.microsoft.com/fwlink/?LinkId=128503), [How To Use a SQL Server 7.0 Distributed Query with a Linked Server to Secured Access Databases](http://go.microsoft.com/fwlink/?LinkId=128504), [HOW TO: Use Jet OLE DB Provider 4.0 to Connect to ISAM Databases](http://go.microsoft.com/fwlink/?LinkId=128505), and [How To Open Delimited Text Files Using the Jet Provider's Text IIsam](http://go.microsoft.com/fwlink/?LinkId=128501).  
  
 In addition, the bulk import of data from a data file into a table requires the following:  
  
-   Users must have INSERT and SELECT permissions on the table. Users also need ALTER TABLE permission when they use options that require data definition language (DDL) operations, such as disabling constraints.  
  
-   When you bulk import data by using BULK INSERT or INSERT ... SELECT * FROM OPENROWSET(BULK...), the data file must be accessible for read operations by either the security profile of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] process (if the user logs in using [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] provided login) or by the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows login that is used under delegated security. Additionally, the user must have ADMINISTER BULK OPERATIONS permission to read the file.  
  
> [!NOTE]  
>  Bulk importing into a partitioned view is unsupported, and attempts to bulk import data into a partitioned view fail.  
  
## External Resources  
 [How to import data from Excel to SQL Server](http://support.microsoft.com/kb/321686)  
  
## Change History  
  
|Updated content|  
|---------------------|  
|Added information about using the OLE DB Provider for Jet to import CSV data.|  
  
## See Also  
 [bcp Utility](../../Topics/TopicNameNotContainA/bcp-Utility.md)   
 [BULK INSERT](assetId:///be3984e1-5ab3-4226-a539-a9f58e1e01e2)   
 [Data Types (Transact-SQL)](assetId:///a54f7373-b247-4d61-8fb8-7f2ec7a8d0a4)   
 [Use Character Format to Import or Export Data (SQL Server)](../../Topics/TopicNameNotContainA/Use-Character-Format-to-Import-or-Export-Data--SQL-Server-.md)   
 [Use Native Format to Import or Export Data (SQL Server)](../../Topics/TopicNameNotContainA/Use-Native-Format-to-Import-or-Export-Data--SQL-Server-.md)