---
title: "Bulk Import and Export of Data (SQL Server)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-bulk-import-export
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 19049021-c048-44a2-b38d-186d9f9e4a65
caps.latest.revision: 58
caps.handback.revision: 0
manager: jhubbard
---
# Bulk Import and Export of Data (SQL Server)
[!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] supports exporting data in bulk (*bulk data*) from a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] table and importing bulk data into a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] table or nonpartitioned view. Bulk importing and bulk exporting are essential to efficient transfer data between [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] and heterogeneous data sources. *Bulk exporting* refers to copying data from a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] table to a data file. *Bulk importing* refers to loading data from a data file into a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] table. For example, you can export data from a [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Excel application to a data file and then bulk import that data into a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] table.  
  
 **In this Topic:**  
  
-   [Introduction to Bulk Import and Bulk Export Operations](#Intro)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="Intro"></a> Bulk Import and Bulk Export Overview  
 This section lists and briefly compares the various methods that are available for bulk importing and exporting data. The section also introduces format files.  
  
 **In This Topic:**  
  
-   [Methods for Bulk Importing and Exporting Data](#MethodsForBuliIE)  
  
-   [Format Files](#FFs)  
  
###  <a name="MethodsForBuliIE"></a> Methods for Bulk Importing and Exporting Data  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] supports bulk exporting data from a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] table and for bulk importing data into a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] table or nonpartitioned view. The following basic methods are available.  
  
|Method|Description|Imports data|Exports data|  
|------------|-----------------|------------------|------------------|  
|[bcp utility](../../Topics/TopicNameNotContainA/Import-and-Export-Bulk-Data-by-Using-the-bcp-Utility--SQL-Server-.md)|A command-line utility (Bcp.exe) that bulk exports and bulk imports data and generates format files.|Yes|Yes|  
|[BULK INSERT statement](../../Topics/TopicNameNotContainA/Import-Bulk-Data-by-Using-BULK-INSERT-or-OPENROWSET-BULK...---SQL-Server-.md)|A [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statement that imports data directly from a data file into a database table or nonpartitioned view.|Yes|No|  
|[INSERT ... SELECT * FROM OPENROWSET(BULK...) statement](../../Topics/TopicNameNotContainA/Import-Bulk-Data-by-Using-BULK-INSERT-or-OPENROWSET-BULK...---SQL-Server-.md)|A [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statement that uses the OPENROWSET bulk rowset provider to bulk import data into a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] table by specifying the OPENROWSET(BULK…) function to select data in an INSERT statement.|Yes|No|  
  
> [!IMPORTANT]  
>  Comma-separated value (CSV) files are not supported by SQL Server bulk-import operations. However, in some cases, a CSV file can be used as the data file for a bulk import of data into SQL Server. Note that the field terminator of a CSV file does not have to be a comma. For more information, see [Prepare Data for Bulk Export or Import (SQL Server)](../../Topics/TopicNameNotContainA/Prepare-Data-for-Bulk-Export-or-Import--SQL-Server-.md).  
  
###  <a name="FFs"></a> Format Files  
 The **bcp** utility, BULK INSERT, and INSERT ... SELECT \* FROM OPENROWSET(BULK...) all support the use of a specialized *format file* that stores format information for each field in a data file. A format file might also contain information about the corresponding [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] table. The format file can be used to provide all the format information that is required to bulk export data from and bulk import data to an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
 Format files provide a flexible way to interpret data as it is in the data file during import, and also to format data in the data file during export. This flexibility eliminates the need to write special-purpose code to interpret the data or reformat the data to the specific requirements of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] or the external application. For example, if you are bulk exporting data to be loaded into an application that requires comma-separated values, you can use a format file to insert commas as field terminators in the exported data.  
  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] supports two kinds of format files: XML format files and non-XML format files.  
  
 The **bcp** utility is the only tool that can generate a format file. For more information, see [Create a Format File (SQL Server)](../../Topics/TopicNameContainA/Create-a-Format-File--SQL-Server-.md). For more information about format files, see [Format Files for Importing or Exporting Data (SQL Server)](../../Topics/TopicNameNotContainA/Format-Files-for-Importing-or-Exporting-Data--SQL-Server-.md).  
  
> [!NOTE]  
>  In cases when a format file is not supplied during a bulk export or import operations, you can override the default formatting at the command line.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Import and Export Bulk Data by Using the bcp Utility (SQL Server)](../../Topics/TopicNameNotContainA/Import-and-Export-Bulk-Data-by-Using-the-bcp-Utility--SQL-Server-.md)  
  
-   [Import Bulk Data by Using BULK INSERT or OPENROWSET(BULK...) (SQL Server)](../../Topics/TopicNameNotContainA/Import-Bulk-Data-by-Using-BULK-INSERT-or-OPENROWSET-BULK...---SQL-Server-.md)  
  
-   [Keep Identity Values When Bulk Importing Data (SQL Server)](../../Topics/TopicNameNotContainA/Keep-Identity-Values-When-Bulk-Importing-Data--SQL-Server-.md)  
  
-   [Keep Nulls or Use Default Values During Bulk Import (SQL Server)](../../Topics/TopicNameNotContainA/Keep-Nulls-or-Use-Default-Values-During-Bulk-Import--SQL-Server-.md)  
  
-   [Prepare Data for Bulk Export or Import (SQL Server)](../../Topics/TopicNameNotContainA/Prepare-Data-for-Bulk-Export-or-Import--SQL-Server-.md)  
  
 **To use a format file**  
  
-   [Create a Format File (SQL Server)](../../Topics/TopicNameContainA/Create-a-Format-File--SQL-Server-.md)  
  
-   [Use a Format File to Bulk Import Data (SQL Server)](../../Topics/TopicNameContainA/Use-a-Format-File-to-Bulk-Import-Data--SQL-Server-.md)  
  
-   [Use a Format File to Map Table Columns to Data-File Fields (SQL Server)](../../Topics/TopicNameContainA/Use-a-Format-File-to-Map-Table-Columns-to-Data-File-Fields--SQL-Server-.md)  
  
-   [Use a Format File to Skip a Data Field (SQL Server)](../../Topics/TopicNameContainA/Use-a-Format-File-to-Skip-a-Data-Field--SQL-Server-.md)  
  
-   [Use a Format File to Skip a Table Column (SQL Server)](../../Topics/TopicNameContainA/Use-a-Format-File-to-Skip-a-Table-Column--SQL-Server-.md)  
  
 **To use data formats for bulk import or bulk export**  
  
-   [Import Native and Character Format Data from Earlier Versions of SQL Server](../../Topics/TopicNameNotContainA/Import-Native-and-Character-Format-Data-from-Earlier-Versions-of-SQL-Server.md)  
  
-   [Use Character Format to Import or Export Data (SQL Server)](../../Topics/TopicNameNotContainA/Use-Character-Format-to-Import-or-Export-Data--SQL-Server-.md)  
  
-   [Use Native Format to Import or Export Data (SQL Server)](../../Topics/TopicNameNotContainA/Use-Native-Format-to-Import-or-Export-Data--SQL-Server-.md)  
  
-   [Use Unicode Character Format to Import or Export Data (SQL Server)](../../Topics/TopicNameNotContainA/Use-Unicode-Character-Format-to-Import-or-Export-Data--SQL-Server-.md)  
  
-   [Use Unicode Native Format to Import or Export Data (SQL Server)](../../Topics/TopicNameNotContainA/Use-Unicode-Native-Format-to-Import-or-Export-Data--SQL-Server-.md)  
  
 **To specify data formats for compatibility when using bcp**  
  
1.  [Specify Field and Row Terminators (SQL Server)](../../Topics/TopicNameNotContainA/Specify-Field-and-Row-Terminators--SQL-Server-.md)  
  
2.  [Specify Prefix Length in Data Files by Using bcp (SQL Server)](../../Topics/TopicNameNotContainA/Specify-Prefix-Length-in-Data-Files-by-Using-bcp--SQL-Server-.md)  
  
3.  [Specify File Storage Type by Using bcp (SQL Server)](../../Topics/TopicNameNotContainA/Specify-File-Storage-Type-by-Using-bcp--SQL-Server-.md)  
  
## See Also  
 [Prerequisites for Minimal Logging in Bulk Import](../../Topics/TopicNameNotContainA/Prerequisites-for-Minimal-Logging-in-Bulk-Import.md)   
 [Format Files for Importing or Exporting Data (SQL Server)](../../Topics/TopicNameNotContainA/Format-Files-for-Importing-or-Exporting-Data--SQL-Server-.md)   
 [Examples of Bulk Import and Export of XML Documents (SQL Server)](../../Topics/TopicNameNotContainA/Examples-of-Bulk-Import-and-Export-of-XML-Documents--SQL-Server-.md)   
 [SQL Server Integration Services](../../Topics/TopicNameNotContainA/SQL-Server-Integration-Services.md)   
 [Copy Databases to Other Servers](../../Topics/TopicNameNotContainA/Copy-Databases-to-Other-Servers.md)   
 [Performing Bulk Load of XML Data (SQLXML 4.0)](assetId:///3708b493-322e-4f3c-9b27-441d0c0ee346)   
 [Performing Bulk Copy Operations](assetId:///50d8456b-e6a1-4b25-bc7e-56946ed654a7)   
 [bcp Utility](../../Topics/TopicNameNotContainA/bcp-Utility.md)   
 [BULK INSERT (Transact-SQL)](assetId:///be3984e1-5ab3-4226-a539-a9f58e1e01e2)   
 [Format Files for Importing or Exporting Data (SQL Server)](../../Topics/TopicNameNotContainA/Format-Files-for-Importing-or-Exporting-Data--SQL-Server-.md)   
 [OPENROWSET (Transact-SQL)](assetId:///f47eda43-33aa-454d-840a-bb15a031ca17)