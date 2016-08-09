---
title: "Use Unicode Native Format to Import or Export Data (SQL Server)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-bulk-import-export
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a6213308-f3d5-406e-9029-19d8bb3367f3
caps.latest.revision: 31
caps.handback.revision: 0
manager: jhubbard
---
# Use Unicode Native Format to Import or Export Data (SQL Server)
Unicode native format is helpful when information must be copied from one [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] installation to another. The use of native format for noncharacter data saves time, eliminating unnecessary conversion of data types to and from character format. The use of Unicode character format for all character data prevents loss of any extended characters during bulk transfer of data between servers using different code pages. A data file in Unicode native format can be read by any bulk-import method.  
  
 Unicode native format is recommended for the bulk transfer of data between multiple instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] by using a data file that contains extended or DBCS characters. For noncharacter data, Unicode native format uses native (database) data types. For character data, such as **char**, **nchar**, **varchar**, **nvarchar**, **text**, **varchar(max)**, **nvarchar(max)**, and **ntext**, the Unicode native format uses Unicode character data format.  
  
 The **sql_variant** data that is stored as a SQLVARIANT in a Unicode native-format data file operates in the same manner as it does in a native-format data file, except that **char** and **varchar** values are converted to **nchar** and **nvarchar**, which doubles the amount of storage required for the affected columns. The original metadata is preserved, and the values are converted back to their original **char** and **varchar** data type when bulk imported into a table column.  
  
## Command Options for Unicode Native Format  
 You can import Unicode native format data into a table using **bcp**, BULK INSERT or INSERT ... SELECT \* FROM OPENROWSET(BULK...). For a **bcp** command or BULK INSERT statement, you can specify the data format on the command line. For an INSERT ... SELECT * FROM OPENROWSET(BULK...) statement, you must specify the data format in a format file.  
  
 Unicode native format is supported by the following options:  
  
|Command|Option|Description|  
|-------------|------------|-----------------|  
|**bcp**|**-N**|Causes the **bcp** utility to use the Unicode native format, which uses native (database) data types for all noncharacter data and Unicode character data format for all character (**char**, **nchar**, **varchar**, **nvarchar**, **text**, and **ntext**) data.|  
|BULK INSERT|DATAFILETYPE **='**widenative**'**|Use Unicode native format when bulk importing data.|  
  
 For more information, see [bcp Utility](../../Topics/TopicNameNotContainA/bcp-Utility.md), [BULK INSERT](assetId:///be3984e1-5ab3-4226-a539-a9f58e1e01e2), or [OPENROWSET (Transact-SQL)](assetId:///f47eda43-33aa-454d-840a-bb15a031ca17).  
  
> [!NOTE]  
>  Alternatively, you can specify formatting on a per-field basis in a format file. For more information, see [Format Files for Importing or Exporting Data (SQL Server)](../../Topics/TopicNameNotContainA/Format-Files-for-Importing-or-Exporting-Data--SQL-Server-.md).  
  
## Examples  
 The following examples demonstrate how to bulk export native data using **bcp** and bulk import the same data using BULK INSERT.  
  
### Sample Table  
 The examples require that a table named **myTestUniNativeData** table be created in the **AdventureWorks** sample database under the **dbo** schema. Before you can run the examples, you must create this table. In [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] Query Editor, execute:  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE myTestUniNativeData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 To populate this table and view the resulting contents execute the following statements:  
  
```  
INSERT INTO myTestUniNativeData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3');  
INSERT INTO myTestUniNativeData(Col1,Col2,Col3)  
   VALUES(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestUniNativeData  
  
```  
  
### Using bcp to Bulk Export Native Data  
 To export data from the table to the data file, use **bcp** with the **out** option and the following qualifiers:  
  
|Qualifiers|Description|  
|----------------|-----------------|  
|**-N**|Specifies native data types.|  
|**-T**|Specifies that the **bcp** utility connects to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] with a trusted connection using integrated security. If **-T** is not specified, you need to specify **-U** and **-P** to successfully log in.|  
  
 The following example bulk exports data in native format from the `myTestUniNativeData` table into a new data file named `myTestUniNativeData-N.Dat` data file. At the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows command prompt, enter:  
  
```  
bcp AdventureWorks..myTestUniNativeData out C:\myTestUniNativeData-N.Dat -N -T  
  
```  
  
### Using BULK INSERT to Bulk Import Native Data  
 The following example uses BULK INSERT to import the data in the `myTestUniNativeData-N.Dat` data file into the `myTestUniNativeData` table. In [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] Query Editor, execute:  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT myTestUniNativeData   
    FROM 'C:\myTestUniNativeData-N.Dat'   
   WITH (DATAFILETYPE='widenative');   
GO  
SELECT Col1,Col2,Col3 FROM myTestUniNativeData;  
GO  
  
```  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To use data formats for bulk import or bulk export**  
  
-   [Import Native and Character Format Data from Earlier Versions of SQL Server](../../Topics/TopicNameNotContainA/Import-Native-and-Character-Format-Data-from-Earlier-Versions-of-SQL-Server.md)  
  
-   [Use Character Format to Import or Export Data (SQL Server)](../../Topics/TopicNameNotContainA/Use-Character-Format-to-Import-or-Export-Data--SQL-Server-.md)  
  
-   [Use Native Format to Import or Export Data (SQL Server)](../../Topics/TopicNameNotContainA/Use-Native-Format-to-Import-or-Export-Data--SQL-Server-.md)  
  
-   [Use Unicode Character Format to Import or Export Data (SQL Server)](../../Topics/TopicNameNotContainA/Use-Unicode-Character-Format-to-Import-or-Export-Data--SQL-Server-.md)  
  
## See Also  
 [bcp Utility](../../Topics/TopicNameNotContainA/bcp-Utility.md)   
 [BULK INSERT](assetId:///be3984e1-5ab3-4226-a539-a9f58e1e01e2)   
 [OPENROWSET (Transact-SQL)](assetId:///f47eda43-33aa-454d-840a-bb15a031ca17)   
 [Data Types (Transact-SQL)](assetId:///a54f7373-b247-4d61-8fb8-7f2ec7a8d0a4)