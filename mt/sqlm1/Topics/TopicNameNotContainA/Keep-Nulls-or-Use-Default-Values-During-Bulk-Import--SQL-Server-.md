---
title: Keep Nulls or Use Default Values During Bulk Import (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-bulk-import-export
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6b91d762-337b-4345-a159-88abb3e64a81
---
# Keep Nulls or Use Default Values During Bulk Import (SQL Server)
  By default, when data is imported into a table, the **bcp** command and BULK INSERT statement observe any defaults that are defined for the columns in the table. For example, if there is a null field in a data file, the default value for the column is loaded instead. The **bcp** command and BULK INSERT statement both allow you to specify that nulls values be retained.  
  
 In contrast, a regular INSERT statement retains the null value instead of inserting a default value. The INSERT ... SELECT \* FROM OPENROWSET\(BULK...\) statement provides the same basic behavior as regular INSERT but additionally supports a table hint for inserting the default values.  
  
> [!NOTE]  
>  For sample format files that skip a table column, see [Use a Format File to Skip a Table Column &#40;SQL Server&#41;](../Topic/Use%20a%20Format%20File%20to%20Skip%20a%20Table%20Column%20\(SQL%20Server\).md).  
  
## Sample Table and Data File  
 To run the examples in this topic, you need to create a sample table and data file.  
  
### Sample Table  
 The examples require that a table named **MyTestDefaultCol2** be created in the **AdventureWorks** sample database under the **dbo** schema. To create this table, in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] Query Editor, execute:  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE MyTestDefaultCol2   
(Col1 smallint,  
Col2 nvarchar(50) DEFAULT 'Default value of Col2',  
Col3 nvarchar(50)   
);  
GO  
  
```  
  
 Notice that the second table column, `Col2`, has a default value.  
  
### Sample Format File  
 Some of the bulk\-import examples use a non\-XML format file, `MyTestDefaultCol2-f-c.Fmt` that corresponds exactly to the `MyTestDefaultCol2` table. To create this format file, at the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows command prompt, enter:  
  
```  
bcp AdventureWorks..MyTestDefaultCol2 format nul -c -f C:\MyTestDefaultCol2-f-c.Fmt -t, -r\n -T  
  
```  
  
 For more information about creating format files, see [Create a Format File &#40;SQL Server&#41;](../Topic/Create%20a%20Format%20File%20\(SQL%20Server\).md).  
  
### Sample Data File  
 The example uses a sample data file, `MyTestEmptyField2-c.Dat`, that contains no values in the second field. The `MyTestEmptyField2-c.Dat` data file contains the following records.  
  
```  
1,,DataField3  
2,,DataField3  
  
```  
  
## Keeping Null Values with bcp or BULK INSERT  
 The following qualifiers specify that an empty field in the data file retains its null value during the bulk\-import operation, rather than inheriting a default value \(if any\) for the table columns.  
  
|Command|Qualifier|Qualifier type|  
|-------------|---------------|--------------------|  
|**bcp**|**\-k**|Switch|  
|BULK INSERT|KEEPNULLS\*|Argument|  
  
 \*For BULK INSERT, if default values are not available, the table column must be defined to allow null values.  
  
> [!NOTE]  
>  These qualifiers disable checking of DEFAULT definitions on a table by these bulk\-import commands. However, for any concurrent INSERT statements, DEFAULT definitions are expected.  
  
 For more information, see [bcp Utility](../../Topics\TopicNameNotContainA/bcp-Utility.md) and [BULK INSERT &#40;Transact-SQL&#41;](../Topic/BULK%20INSERT%20\(Transact-SQL\).md).  
  
### Examples  
 The examples in this section bulk import using **bcp** or BULK INSERT and keep null values.  
  
 The second table column, **Col2**, has a default value. The corresponding field of the data file contains an empty string. By default, when **bcp** or BULK INSERT is used to import data from this data file into the **MyTestDefaultCol2** table, the default value of **Col2** is inserted, producing the following result:  
  
||||  
|-|-|-|  
|`1`|`Default value of Col2`|`DataField3`|  
|`2`|`Default value of Col2`|`DataField3`|  
  
 To insert "`NULL`" instead of "`Default value of Col2`", you need to use the **\-k** switch or KEEPNULL option, as demonstrated in the following **bcp** and BULK INSERT examples.  
  
#### Using bcp and Keeping Null Values  
 The following example demonstrates how to keep null values in a **bcp** command. The **bcp** command contains the following switches:  
  
|Switch|Description|  
|------------|-----------------|  
|**\-f**|Specifies that the command is using a format file..|  
|**\-k**|Specifies that empty columns should retain a null value during the operation, rather than have any default values for the columns inserted.|  
|**\-T**|Specifies that the bcp utility connects to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] with a trusted connection.|  
  
 At the Windows command prompt, enter.  
  
```  
bcp AdventureWorks..MyTestDefaultCol2 in C:\MyTestEmptyField2-c.Dat -f C:\MyTestDefaultCol2-f-c.Fmt -k -T  
  
```  
  
#### Using BULK INSERT and Keeping Null Values  
 The following example demonstrates how to use the KEEPNULLS option in a BULK INSERT statement. From a query tool, such as [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] Query Editor, execute:  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT MyTestDefaultCol2  
   FROM 'C:\MyTestEmptyField2-c.Dat'  
   WITH (  
      DATAFILETYPE = 'char',  
      FIELDTERMINATOR = ',',  
      KEEPNULLS  
   );  
GO  
  
```  
  
## Keeping Default Values with INSERT ... SELECT \* FROM OPENROWSET\(BULK...\)  
 By default, any columns that are not specified in the bulk\-load operation are set to NULL by INSERT ... SELECT \* FROM OPENROWSET\(BULK...\). However, you can specify that for an empty field in the data file, the corresponding table column uses its default value \(if any\). To use default values, specify the following table hint:  
  
|Command|Qualifier|Qualifier Type|  
|-------------|---------------|--------------------|  
|INSERT ... SELECT \* FROM OPENROWSET\(BULK...\)|WITH\(KEEPDEFAULTS\)|Table hint|  
  
> [!NOTE]  
>  for more information, see [INSERT &#40;Transact-SQL&#41;](../Topic/INSERT%20\(Transact-SQL\).md), [SELECT &#40;Transact-SQL&#41;](../Topic/SELECT%20\(Transact-SQL\).md), [OPENROWSET &#40;Transact-SQL&#41;](../Topic/OPENROWSET%20\(Transact-SQL\).md), and [Table Hints &#40;Transact-SQL&#41;](../Topic/Table%20Hints%20\(Transact-SQL\).md)  
  
### Examples  
 The following INSERT ... SELECT \* FROM OPENROWSET\(BULK...\) example bulk imports data and keeps the default values.  
  
 To run the examples, you need to create the **MyTestDefaultCol2** sample table, the `MyTestEmptyField2-c.Dat` data file, and use a format file, `MyTestDefaultCol2-f-c.Fmt`. For information on creating these samples, see "Sample Table and Data File," earlier in this topic.  
  
 The second table column, **Col2**, has a default value. The corresponding field of the data file contains an empty string. When INSERT ... SELECT \* FROM OPENROWSET\(BULK...\) import the fields of this data file into the **MyTestDefaultCol2** table, by default, NULL is inserted into **Col2** instead of the default value. This default behavior produces the following result:  
  
||||  
|-|-|-|  
|`1`|`NULL`|`DataField3`|  
|`2`|`NULL`|`DataField3`|  
  
 To insert the default value, "`Default value of Col2`", instead of "`NULL`", you need to use KEEPDEFAULTS table hint, as demonstrated in the following example. From a query tool, such as [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] Query Editor, execute:  
  
```  
USE AdventureWorks;  
GO  
INSERT INTO MyTestDefaultCol2  
    WITH (KEEPDEFAULTS)  
    SELECT *  
      FROM OPENROWSET(BULK  'C:\MyTestEmptyField2-c.Dat',  
      FORMATFILE='C:\MyTestDefaultCol2-f-c.Fmt'       
      ) as t1 ;  
GO  
  
```  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Keep Identity Values When Bulk Importing Data &#40;SQL Server&#41;](../Topic/Keep%20Identity%20Values%20When%20Bulk%20Importing%20Data%20\(SQL%20Server\).md)  
  
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
  
-   [Specify Field and Row Terminators &#40;SQL Server&#41;](../Topic/Specify%20Field%20and%20Row%20Terminators%20\(SQL%20Server\).md)  
  
-   [Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;](../Topic/Specify%20Prefix%20Length%20in%20Data%20Files%20by%20Using%20bcp%20\(SQL%20Server\).md)  
  
-   [Specify File Storage Type by Using bcp &#40;SQL Server&#41;](../Topic/Specify%20File%20Storage%20Type%20by%20Using%20bcp%20\(SQL%20Server\).md)  
  
## See Also  
 [BACKUP &#40;Transact-SQL&#41;](../Topic/BACKUP%20\(Transact-SQL\).md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../Topic/OPENROWSET%20\(Transact-SQL\).md)   
 [bcp Utility](../../Topics\TopicNameNotContainA/bcp-Utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](../Topic/BULK%20INSERT%20\(Transact-SQL\).md)   
 [Table Hints &#40;Transact-SQL&#41;](../Topic/Table%20Hints%20\(Transact-SQL\).md)  
  
  