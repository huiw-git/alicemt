---
title: Use Unicode Character Format to Import or Export Data (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-bulk-import-export
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 74342a11-c1c0-4746-b482-7f3537744a70
---
# Use Unicode Character Format to Import or Export Data (SQL Server)
  Unicode character format is recommended for bulk transfer of data between multiple instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] by using a data file that contains extended\/DBCS characters. The Unicode character data format allows data to be exported from a server by using a code page that differs from the code page used by the client that is performing the operation. In such cases, use of Unicode character format has the following advantages:  
  
-   If the source and destination data are Unicode data types, use of Unicode character format preserves all of the character data.  
  
-   if the source and destination data are not Unicode data types, use of Unicode character format minimizes the loss of extended characters in the source data that cannot be represented at the destination.  
  
 Unicode character format data files follow the conventions for Unicode files. The first two bytes of the file are hexadecimal numbers, 0xFFFE. These bytes serve as byte\-order marks, specifying whether the high\-order byte is stored first or last in the file.  
  
> [!IMPORTANT]  
>  For a format file to work with a Unicode character data file, all the input fields must be Unicode text strings \(that is, either fixed\-size or character\-terminated Unicode strings\).  
  
 The **sql\_variant** data that is stored in a Unicode character\-format data file operates in the same way it operates in a character\-format data file, except that the data is stored as **nchar** instead of **char** data. For more information about character format, see [Collation and Unicode Support](../../Topics\TopicNameNotContainA/Collation-and-Unicode-Support.md).  
  
 To use a field or row terminator other than the default that is provided with Unicode character format, see [Specify Field and Row Terminators &#40;SQL Server&#41;](../Topic/Specify%20Field%20and%20Row%20Terminators%20\(SQL%20Server\).md).  
  
## Command Options for Unicode Character Format  
 You can import Unicode character format data into a table using **bcp**, BULK INSERT or INSERT ... SELECT \* FROM OPENROWSET\(BULK...\). For a **bcp** command or BULK INSERT statement, you can specify the data format on the command line. For an INSERT ... SELECT \* FROM OPENROWSET\(BULK...\) statement, you must specify the data format in a format file.  
  
 Unicode character format is supported by the following command line options:  
  
|Command|Option|Description|  
|-------------|------------|-----------------|  
|**bcp**|**\-w**|Uses the Unicode character format.|  
|BULK INSERT|DATAFILETYPE **\='**widechar**'**|Uses Unicode character format when bulk importing data.|  
  
 For more information, see [bcp Utility](../../Topics\TopicNameNotContainA/bcp-Utility.md), [BULK INSERT &#40;Transact-SQL&#41;](../Topic/BULK%20INSERT%20\(Transact-SQL\).md), or [OPENROWSET &#40;Transact-SQL&#41;](../Topic/OPENROWSET%20\(Transact-SQL\).md).  
  
> [!NOTE]  
>  Alternatively, you can specify formatting on a per\-field basis in a format file. For more information, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](../Topic/Format%20Files%20for%20Importing%20or%20Exporting%20Data%20\(SQL%20Server\).md).  
  
## Examples  
 The following examples demonstrate how to bulk export Unicode character data using **bcp** and to bulk import the same data using BULK INSERT.  
  
### Sample Table  
 The examples require that a table named `myTestUniCharData` table be created in the [!INCLUDE[ssSampleDBnormal](../../Token\Other/ssSampleDBnormal_md.md)] sample database under the `dbo` schema. Before you can run the examples, you must create this table. To create this table, in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] Query Editor, execute:  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestUniCharData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 To populate this table and view the resulting contents execute the following statements:  
  
```  
INSERT INTO myTestUniCharData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3')   
        ,(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestUniCharData;  
  
```  
  
### Using bcp to Bulk Export Unicode Character Data  
 To export data from the table to the data file, use **bcp** with the **out** option and the following qualifiers:  
  
|Qualifiers|Description|  
|----------------|-----------------|  
|**\-w**|Specifies Unicode character format.|  
|**\-t** `,`|Specifies a comma \(`,`\) as the field terminator.<br /><br /> Note that the default field terminator is the Unicode tab character \(\\t\). For more information, see [Specify Field and Row Terminators &#40;SQL Server&#41;](../Topic/Specify%20Field%20and%20Row%20Terminators%20\(SQL%20Server\).md).|  
|**\-T**|Specifies that the **bcp** utility connects to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] with a trusted connection using integrated security. If **\-T** is not specified, you need to specify **\-U** and **\-P** to successfully log in.|  
  
 The following example bulk exports data in Unicode character format from the `myTestUniCharData` table into a new data file named `myTestUniCharData-w.Dat` data file that uses the comma \(`,`\) as the field terminator. At the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows command prompt, enter:  
  
```  
bcp AdventureWorks2012..myTestUniCharData out C:\myTestUniCharData-w.Dat -w -t, -T  
  
```  
  
### Using BULK INSERT to Bulk Import Unicode Character Data  
 The following example uses `BULK INSERT` to import the data in the `myTestUniCharData-w.Dat` data file into the `myTestUniCharData` table. The nondefault field terminator \(`,`\) must be declared in the statement. In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] Query Editor, execute:  
  
```  
USE AdventureWorks2012;  
GO  
BULK INSERT myTestUniCharData   
   FROM 'C:\myTestUniCharData-w.Dat'   
   WITH (  
      DATAFILETYPE='widechar',  
      FIELDTERMINATOR=','  
   );   
GO  
SELECT Col1,Col2,Col3 FROM myTestUniCharData;  
GO  
  
```  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To use data formats for bulk import or bulk export**  
  
-   [Import Native and Character Format Data from Earlier Versions of SQL Server](../../Topics\TopicNameNotContainA/Import-Native-and-Character-Format-Data-from-Earlier-Versions-of-SQL-Server.md)  
  
-   [Use Character Format to Import or Export Data &#40;SQL Server&#41;](../Topic/Use%20Character%20Format%20to%20Import%20or%20Export%20Data%20\(SQL%20Server\).md)  
  
-   [Use Native Format to Import or Export Data &#40;SQL Server&#41;](../Topic/Use%20Native%20Format%20to%20Import%20or%20Export%20Data%20\(SQL%20Server\).md)  
  
-   [Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;](../Topic/Use%20Unicode%20Native%20Format%20to%20Import%20or%20Export%20Data%20\(SQL%20Server\).md)  
  
## See Also  
 [bcp Utility](../../Topics\TopicNameNotContainA/bcp-Utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](../Topic/BULK%20INSERT%20\(Transact-SQL\).md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../Topic/OPENROWSET%20\(Transact-SQL\).md)   
 [Data Types &#40;Transact-SQL&#41;](../Topic/Data%20Types%20\(Transact-SQL\).md)   
 [Collation and Unicode Support](../../Topics\TopicNameNotContainA/Collation-and-Unicode-Support.md)  
  
  