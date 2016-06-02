---
title: Import and Export Bulk Data by Using the bcp Utility (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-bulk-import-export
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 73e949de-67a3-4c84-9735-7da1ad4ba34a
---
# Import and Export Bulk Data by Using the bcp Utility (SQL Server)
  This topic provides an overview for using the [bcp utility](../../Topics\TopicNameNotContainA/bcp-Utility.md) to export data from anywhere in a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database where a SELECT statement works, including partitioned views.  
  
 The bcp utility \(Bcp.exe\) is a command\-line tool that uses the Bulk Copy Program \(BCP\) API. The bcp utility performs the following tasks:  
  
-   Bulk exports data from a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] table into a data file.  
  
-   Bulk exports data from a query.  
  
-   Bulk imports data from a data file into a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] table.  
  
-   Generates format files.  
  
 The bcp utility is accessed by the **bcp** command. To use the **bcp** command to bulk import data, you must understand the schema of the table and the data types of its columns, unless you are using a pre\-existing format file.  
  
 The bcp utility can export data from a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] table to a data file for use in other programs. The utility can also import data into a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] table from another program, usually another database management system \(DBMS\). The data is first exported from the source program to a data file and then, in a separate operation, copied from the data file into a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] table.  
  
 The **bcp** command provides switches that you use to specify the data type of the data file and other information. If these switches are not specified, the command prompts for formatting information, such as the type of data fields in a data file. The command then asks whether you want to create a format file that contains your interactive responses. If you want flexibility for future bulk\-import or bulk\-export operations, a format file is often useful. You can specify the format file on later **bcp** commands for equivalent data files. For more information, see [Specify Data Formats for Compatibility when Using bcp &#40;SQL Server&#41;](../Topic/Specify%20Data%20Formats%20for%20Compatibility%20when%20Using%20bcp%20\(SQL%20Server\).md).  
  
> [!NOTE]  
>  The bcp utility is written by using the ODBC bulk\-copy  
  
 For a description of the **bcp** command syntax, see [bcp Utility](../../Topics\TopicNameNotContainA/bcp-Utility.md).  
  
## Examples  
 For **bcp** examples, see:  
  
-   [bcp Utility](../../Topics\TopicNameNotContainA/bcp-Utility.md)  
  
-   [Create a Format File &#40;SQL Server&#41;](../Topic/Create%20a%20Format%20File%20\(SQL%20Server\).md)  
  
-   [Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;](../Topic/Examples%20of%20Bulk%20Import%20and%20Export%20of%20XML%20Documents%20\(SQL%20Server\).md)  
  
-   [Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;](../Topic/Keep%20Identity%20Values%20When%20Bulk%20Importing%20Data%20\(SQL%20Server\).md)  
  
-   [Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;](../Topic/Keep%20Nulls%20or%20Use%20Default%20Values%20During%20Bulk%20Import%20\(SQL%20Server\).md)  
  
-   [Specify Field and Row Terminators &#40;SQL Server&#41;](../Topic/Specify%20Field%20and%20Row%20Terminators%20\(SQL%20Server\).md)  
  
-   [Use a Format File to Bulk Import Data &#40;SQL Server&#41;](../Topic/Use%20a%20Format%20File%20to%20Bulk%20Import%20Data%20\(SQL%20Server\).md)  
  
-   [Use Character Format to Import or Export Data &#40;SQL Server&#41;](../Topic/Use%20Character%20Format%20to%20Import%20or%20Export%20Data%20\(SQL%20Server\).md)  
  
-   [Use Native Format to Import or Export Data &#40;SQL Server&#41;](../Topic/Use%20Native%20Format%20to%20Import%20or%20Export%20Data%20\(SQL%20Server\).md)  
  
-   [Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;](../Topic/Use%20Unicode%20Character%20Format%20to%20Import%20or%20Export%20Data%20\(SQL%20Server\).md)  
  
-   [Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;](../Topic/Use%20Unicode%20Native%20Format%20to%20Import%20or%20Export%20Data%20\(SQL%20Server\).md)  
  
## See Also  
 [INSERT &#40;Transact-SQL&#41;](../Topic/INSERT%20\(Transact-SQL\).md)   
 [SELECT Clause &#40;Transact-SQL&#41;](../Topic/SELECT%20Clause%20\(Transact-SQL\).md)   
 [bcp Utility](../../Topics\TopicNameNotContainA/bcp-Utility.md)   
 [Prepare to Bulk Import Data &#40;SQL Server&#41;](../Topic/Prepare%20to%20Bulk%20Import%20Data%20\(SQL%20Server\).md)   
 [BULK INSERT &#40;Transact-SQL&#41;](../Topic/BULK%20INSERT%20\(Transact-SQL\).md)   
 [Bulk Import and Export of Data &#40;SQL Server&#41;](../Topic/Bulk%20Import%20and%20Export%20of%20Data%20\(SQL%20Server\).md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../Topic/OPENROWSET%20\(Transact-SQL\).md)   
 [Create a Format File &#40;SQL Server&#41;](../Topic/Create%20a%20Format%20File%20\(SQL%20Server\).md)  
  
  