---
title: "Import and Export Bulk Data by Using the bcp Utility (SQL Server)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-bulk-import-export
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 73e949de-67a3-4c84-9735-7da1ad4ba34a
caps.latest.revision: 20
caps.handback.revision: 0
manager: jhubbard
---
# Import and Export Bulk Data by Using the bcp Utility (SQL Server)
This topic provides an overview for using the [bcp utility](../../Topics/TopicNameNotContainA/bcp-Utility.md) to export data from anywhere in a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] database where a SELECT statement works, including partitioned views.  
  
 The bcp utility (Bcp.exe) is a command-line tool that uses the Bulk Copy Program (BCP) API. The bcp utility performs the following tasks:  
  
-   Bulk exports data from a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] table into a data file.  
  
-   Bulk exports data from a query.  
  
-   Bulk imports data from a data file into a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] table.  
  
-   Generates format files.  
  
 The bcp utility is accessed by the **bcp** command. To use the **bcp** command to bulk import data, you must understand the schema of the table and the data types of its columns, unless you are using a pre-existing format file.  
  
 The bcp utility can export data from a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] table to a data file for use in other programs. The utility can also import data into a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] table from another program, usually another database management system (DBMS). The data is first exported from the source program to a data file and then, in a separate operation, copied from the data file into a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] table.  
  
 The **bcp** command provides switches that you use to specify the data type of the data file and other information. If these switches are not specified, the command prompts for formatting information, such as the type of data fields in a data file. The command then asks whether you want to create a format file that contains your interactive responses. If you want flexibility for future bulk-import or bulk-export operations, a format file is often useful. You can specify the format file on later **bcp** commands for equivalent data files. For more information, see [Specify Data Formats for Compatibility when Using bcp (SQL Server)](../../Topics/TopicNameNotContainA/Specify-Data-Formats-for-Compatibility-when-Using-bcp--SQL-Server-.md).  
  
> [!NOTE]  
>  The bcp utility is written by using the ODBC bulk-copy  
  
 For a description of the **bcp** command syntax, see [bcp Utility](../../Topics/TopicNameNotContainA/bcp-Utility.md).  
  
## Examples  
 For **bcp** examples, see:  
  
-   [bcp Utility](../../Topics/TopicNameNotContainA/bcp-Utility.md)  
  
-   [Create a Format File (SQL Server)](../../Topics/TopicNameContainA/Create-a-Format-File--SQL-Server-.md)  
  
-   [Examples of Bulk Import and Export of XML Documents (SQL Server)](../../Topics/TopicNameNotContainA/Examples-of-Bulk-Import-and-Export-of-XML-Documents--SQL-Server-.md)  
  
-   [Keep Identity Values When Bulk Importing Data (SQL Server)](../../Topics/TopicNameNotContainA/Keep-Identity-Values-When-Bulk-Importing-Data--SQL-Server-.md)  
  
-   [Keep Nulls or Use Default Values During Bulk Import (SQL Server)](../../Topics/TopicNameNotContainA/Keep-Nulls-or-Use-Default-Values-During-Bulk-Import--SQL-Server-.md)  
  
-   [Specify Field and Row Terminators (SQL Server)](../../Topics/TopicNameNotContainA/Specify-Field-and-Row-Terminators--SQL-Server-.md)  
  
-   [Use a Format File to Bulk Import Data (SQL Server)](../../Topics/TopicNameContainA/Use-a-Format-File-to-Bulk-Import-Data--SQL-Server-.md)  
  
-   [Use Character Format to Import or Export Data (SQL Server)](../../Topics/TopicNameNotContainA/Use-Character-Format-to-Import-or-Export-Data--SQL-Server-.md)  
  
-   [Use Native Format to Import or Export Data (SQL Server)](../../Topics/TopicNameNotContainA/Use-Native-Format-to-Import-or-Export-Data--SQL-Server-.md)  
  
-   [Use Unicode Character Format to Import or Export Data (SQL Server)](../../Topics/TopicNameNotContainA/Use-Unicode-Character-Format-to-Import-or-Export-Data--SQL-Server-.md)  
  
-   [Use Unicode Native Format to Import or Export Data (SQL Server)](../../Topics/TopicNameNotContainA/Use-Unicode-Native-Format-to-Import-or-Export-Data--SQL-Server-.md)  
  
## See Also  
 [INSERT (Transact-SQL)](assetId:///1054c76e-0fd5-4131-8c07-a6c5d024af50)   
 [SELECT Clause (Transact-SQL)](assetId:///2616d800-4853-4cf1-af77-d32d68d8c2ef)   
 [bcp Utility](../../Topics/TopicNameNotContainA/bcp-Utility.md)   
 [Prepare to Bulk Import Data (SQL Server)](../../Topics/TopicNameNotContainA/Prepare-to-Bulk-Import-Data--SQL-Server-.md)   
 [BULK INSERT (Transact-SQL)](assetId:///be3984e1-5ab3-4226-a539-a9f58e1e01e2)   
 [Bulk Import and Export of Data (SQL Server)](../../Topics/TopicNameNotContainA/Bulk-Import-and-Export-of-Data--SQL-Server-.md)   
 [OPENROWSET (Transact-SQL)](assetId:///f47eda43-33aa-454d-840a-bb15a031ca17)   
 [Create a Format File (SQL Server)](../../Topics/TopicNameContainA/Create-a-Format-File--SQL-Server-.md)