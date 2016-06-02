---
title: Bulk Import and Export of Data (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-bulk-import-export
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 19049021-c048-44a2-b38d-186d9f9e4a65
---
# Bulk Import and Export of Data (SQL Server)
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] supports exporting data in bulk \(*bulk data*\) from a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] table and importing bulk data into a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] table or nonpartitioned view. Bulk importing and bulk exporting are essential to efficient transfer data between [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and heterogeneous data sources. *Bulk exporting* refers to copying data from a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] table to a data file. *Bulk importing* refers to loading data from a data file into a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] table. For example, you can export data from a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Excel application to a data file and then bulk import that data into a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] table.  
  
 **In this Topic:**  
  
-   [Introduction to Bulk Import and Bulk Export Operations](#Intro)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="Intro"></a> Bulk Import and Bulk Export Overview  
 This section lists and briefly compares the various methods that are available for bulk importing and exporting data. The section also introduces format files.  
  
 **In This Topic:**  
  
-   [Methods for Bulk Importing and Exporting Data](#MethodsForBuliIE)  
  
-   [Format Files](#FFs)  
  
###  <a name="MethodsForBuliIE"></a> Methods for Bulk Importing and Exporting Data  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] supports bulk exporting data from a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] table and for bulk importing data into a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] table or nonpartitioned view. The following basic methods are available.  
  
|Method|Description|Imports data|Exports data|  
|------------|-----------------|------------------|------------------|  
|[bcp utility](../Topic/Import%20and%20Export%20Bulk%20Data%20by%20Using%20the%20bcp%20Utility%20\(SQL%20Server\).md)|A command\-line utility \(Bcp.exe\) that bulk exports and bulk imports data and generates format files.|Yes|Yes|  
|[BULK INSERT statement](../Topic/Import%20Bulk%20Data%20by%20Using%20BULK%20INSERT%20or%20OPENROWSET\(BULK...\)%20\(SQL%20Server\).md)|A [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement that imports data directly from a data file into a database table or nonpartitioned view.|Yes|No|  
|[INSERT ... SELECT \* FROM OPENROWSET\(BULK...\) statement](../Topic/Import%20Bulk%20Data%20by%20Using%20BULK%20INSERT%20or%20OPENROWSET\(BULK...\)%20\(SQL%20Server\).md)|A [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement that uses the OPENROWSET bulk rowset provider to bulk import data into a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] table by specifying the OPENROWSET\(BULK…\) function to select data in an INSERT statement.|Yes|No|  
  
> [!IMPORTANT]  
>  Comma\-separated value \(CSV\) files are not supported by SQL Server bulk\-import operations. However, in some cases, a CSV file can be used as the data file for a bulk import of data into SQL Server. Note that the field terminator of a CSV file does not have to be a comma. For more information, see [Prepare Data for Bulk Export or Import &#40;SQL Server&#41;](../Topic/Prepare%20Data%20for%20Bulk%20Export%20or%20Import%20\(SQL%20Server\).md).  
  
###  <a name="FFs"></a> Format Files  
 The **bcp** utility, BULK INSERT, and INSERT ... SELECT \* FROM OPENROWSET\(BULK...\) all support the use of a specialized *format file* that stores format information for each field in a data file. A format file might also contain information about the corresponding [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] table. The format file can be used to provide all the format information that is required to bulk export data from and bulk import data to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
 Format files provide a flexible way to interpret data as it is in the data file during import, and also to format data in the data file during export. This flexibility eliminates the need to write special\-purpose code to interpret the data or reformat the data to the specific requirements of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or the external application. For example, if you are bulk exporting data to be loaded into an application that requires comma\-separated values, you can use a format file to insert commas as field terminators in the exported data.  
  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] supports two kinds of format files: XML format files and non\-XML format files.  
  
 The **bcp** utility is the only tool that can generate a format file. For more information, see [Create a Format File &#40;SQL Server&#41;](../Topic/Create%20a%20Format%20File%20\(SQL%20Server\).md). For more information about format files, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](../Topic/Format%20Files%20for%20Importing%20or%20Exporting%20Data%20\(SQL%20Server\).md).  
  
> [!NOTE]  
>  In cases when a format file is not supplied during a bulk export or import operations, you can override the default formatting at the command line.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Import and Export Bulk Data by Using the bcp Utility &#40;SQL Server&#41;](../Topic/Import%20and%20Export%20Bulk%20Data%20by%20Using%20the%20bcp%20Utility%20\(SQL%20Server\).md)  
  
-   [Import Bulk Data by Using BULK INSERT or OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;](../Topic/Import%20Bulk%20Data%20by%20Using%20BULK%20INSERT%20or%20OPENROWSET\(BULK...\)%20\(SQL%20Server\).md)  
  
-   [Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;](../Topic/Keep%20Identity%20Values%20When%20Bulk%20Importing%20Data%20\(SQL%20Server\).md)  
  
-   [Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;](../Topic/Keep%20Nulls%20or%20Use%20Default%20Values%20During%20Bulk%20Import%20\(SQL%20Server\).md)  
  
-   [Prepare Data for Bulk Export or Import &#40;SQL Server&#41;](../Topic/Prepare%20Data%20for%20Bulk%20Export%20or%20Import%20\(SQL%20Server\).md)  
  
 **To use a format file**  
  
-   [Create a Format File &#40;SQL Server&#41;](../Topic/Create%20a%20Format%20File%20\(SQL%20Server\).md)  
  
-   [Use a Format File to Bulk Import Data &#40;SQL Server&#41;](../Topic/Use%20a%20Format%20File%20to%20Bulk%20Import%20Data%20\(SQL%20Server\).md)  
  
-   [Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;](../Topic/Use%20a%20Format%20File%20to%20Map%20Table%20Columns%20to%20Data-File%20Fields%20\(SQL%20Server\).md)  
  
-   [Use a Format File to Skip a Data Field &#40;SQL Server&#41;](../Topic/Use%20a%20Format%20File%20to%20Skip%20a%20Data%20Field%20\(SQL%20Server\).md)  
  
-   [Use a Format File to Skip a Table Column &#40;SQL Server&#41;](../Topic/Use%20a%20Format%20File%20to%20Skip%20a%20Table%20Column%20\(SQL%20Server\).md)  
  
 **To use data formats for bulk import or bulk export**  
  
-   [Import Native and Character Format Data from Earlier Versions of SQL Server](../../Topics\TopicNameNotContainA/Import-Native-and-Character-Format-Data-from-Earlier-Versions-of-SQL-Server.md)  
  
-   [Use Character Format to Import or Export Data &#40;SQL Server&#41;](../Topic/Use%20Character%20Format%20to%20Import%20or%20Export%20Data%20\(SQL%20Server\).md)  
  
-   [Use Native Format to Import or Export Data &#40;SQL Server&#41;](../Topic/Use%20Native%20Format%20to%20Import%20or%20Export%20Data%20\(SQL%20Server\).md)  
  
-   [Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;](../Topic/Use%20Unicode%20Character%20Format%20to%20Import%20or%20Export%20Data%20\(SQL%20Server\).md)  
  
-   [Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;](../Topic/Use%20Unicode%20Native%20Format%20to%20Import%20or%20Export%20Data%20\(SQL%20Server\).md)  
  
 **To specify data formats for compatibility when using bcp**  
  
1.  [Specify Field and Row Terminators &#40;SQL Server&#41;](../Topic/Specify%20Field%20and%20Row%20Terminators%20\(SQL%20Server\).md)  
  
2.  [Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;](../Topic/Specify%20Prefix%20Length%20in%20Data%20Files%20by%20Using%20bcp%20\(SQL%20Server\).md)  
  
3.  [Specify File Storage Type by Using bcp &#40;SQL Server&#41;](../Topic/Specify%20File%20Storage%20Type%20by%20Using%20bcp%20\(SQL%20Server\).md)  
  
## See Also  
 [Prerequisites for Minimal Logging in Bulk Import](../../Topics\TopicNameNotContainA/Prerequisites-for-Minimal-Logging-in-Bulk-Import.md)   
 [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](../Topic/Format%20Files%20for%20Importing%20or%20Exporting%20Data%20\(SQL%20Server\).md)   
 [Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;](../Topic/Examples%20of%20Bulk%20Import%20and%20Export%20of%20XML%20Documents%20\(SQL%20Server\).md)   
 [SQL Server Integration Services](../../Topics\TopicNameNotContainA/SQL-Server-Integration-Services.md)   
 [Copy Databases to Other Servers](../../Topics\TopicNameNotContainA/Copy-Databases-to-Other-Servers.md)   
 [Performing Bulk Load of XML Data &#40;SQLXML 4.0&#41;](../Topic/Performing%20Bulk%20Load%20of%20XML%20Data%20\(SQLXML%204.0\).md)   
 [Performing Bulk Copy Operations](../Topic/Performing%20Bulk%20Copy%20Operations.md)   
 [bcp Utility](../../Topics\TopicNameNotContainA/bcp-Utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](../Topic/BULK%20INSERT%20\(Transact-SQL\).md)   
 [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](../Topic/Format%20Files%20for%20Importing%20or%20Exporting%20Data%20\(SQL%20Server\).md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../Topic/OPENROWSET%20\(Transact-SQL\).md)  
  
  