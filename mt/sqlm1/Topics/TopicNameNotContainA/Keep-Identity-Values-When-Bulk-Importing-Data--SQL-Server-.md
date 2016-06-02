---
title: Keep Identity Values When Bulk Importing Data (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-bulk-import-export
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 45894a3f-2d8a-4edd-9568-afa7d0d3061f
---
# Keep Identity Values When Bulk Importing Data (SQL Server)
  Data files that contain identity values can be bulk imported into an instance of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. By default, the values for the identity column in the data file that is imported are ignored and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] assigns unique values automatically. The unique values are based on the seed and increment values that are specified during table creation.  
  
 If the data file does not contain values for the identifier column in the table, use a format file to specify that the identifier column in the table should be skipped when importing data. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] assigns unique values for the column automatically.  
  
 To prevent [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] from assigning identity values while bulk importing data rows into a table, use the appropriate keep\-identity command qualifier. When you specify a keep\-identity qualifier, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] uses the identity values in the data file. These qualifiers are as follows:  
  
|Command|Keep\-identity qualifier|Qualifier type|  
|-------------|------------------------------|--------------------|  
|**bcp**|**\-E**|Switch|  
|BULK INSERT|KEEPIDENTITY|Argument|  
|INSERT ... SELECT \* FROM OPENROWSET\(BULK...\)|KEEPIDENTITY|Table hint|  
  
 For more information, see [bcp Utility](../../Topics\TopicNameNotContainA/bcp-Utility.md), [BULK INSERT &#40;Transact-SQL&#41;](../Topic/BULK%20INSERT%20\(Transact-SQL\).md), [OPENROWSET &#40;Transact-SQL&#41;](../Topic/OPENROWSET%20\(Transact-SQL\).md), [INSERT &#40;Transact-SQL&#41;](../Topic/INSERT%20\(Transact-SQL\).md), [SELECT &#40;Transact-SQL&#41;](../Topic/SELECT%20\(Transact-SQL\).md), and [Table Hints &#40;Transact-SQL&#41;](../Topic/Table%20Hints%20\(Transact-SQL\).md).  
  
> [!NOTE]  
>  To create an automatically incrementing number that can be used in multiple tables or that can be called from applications without referencing any table, see [Sequence Numbers](../../Topics\TopicNameNotContainA/Sequence-Numbers.md).  
  
## Examples  
 The examples in this topic bulk import data using INSERT ... SELECT \* FROM OPENROWSET\(BULK...\) and keeping default values.  
  
### Sample Table  
 The bulk\-import examples require that a table named **myTestKeepNulls** table be created in the **AdventureWorks** sample database under the **dbo** schema. To create this table. in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] Query Editor, execute:  
  
```  
USE AdventureWorks;  
GO  
SELECT * INTO HumanResources.myDepartment   
   FROM HumanResources.Department  
      WHERE 1=0;  
GO  
SELECT * FROM HumanResources.myDepartment;  
```  
  
 The **Department** table on which `myDepartment` is based has IDENTITY\_INSERT is set to OFF. Therefore, to import data into an identity column you must specify KEEPIDENTITY or **\-E**.  
  
### Sample Data File  
 The data file used in the bulk\-import examples contains data bulk exported from the `HumanResources.Department` table in native format. To create the data file, at the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows command prompt, enter:  
  
```  
bcp AdventureWorks.HumanResources.Department out myDepartment-n.Dat -n -T  
```  
  
### Sample Format File  
 This bulk\-import examples use an XML format file, `myDepartment-f-x-n.Xml`, which uses native data formats. This example uses **bcp** to create to generate this format file from the `HumanResources.Department` table of the `AdventureWorks` database. At the Windows command prompt, enter:  
  
```  
bcp AdventureWorks.HumanResources.Department format nul -n -x -f myDepartment-f-n-x.Xml -T  
```  
  
 For more information about creating a format file, see [Create a Format File &#40;SQL Server&#41;](../Topic/Create%20a%20Format%20File%20\(SQL%20Server\).md).  
  
### A. Using bcp and Keeping Identity Values  
 The following example demonstrates how to keep identity values when using **bcp** to bulk import data. The **bcp** command uses the format file, `myDepartment-f-n-x.Xml`, and contains the following switches:  
  
|Qualifiers|Description|  
|----------------|-----------------|  
|**\-E**|Specifies that identity value or values in the data file are to be used for the identity column.|  
|**\-T**|Specifies that the **bcp** utility connects to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] with a trusted connection.|  
  
 At the Windows command prompt, enter.  
  
```  
bcp AdventureWorks.HumanResources.myDepartment in C:\myDepartment-n.Dat -f C:\myDepartment-f-n-x.Xml -E -T  
  
```  
  
### B. Using BULK INSERT and Keeping Identity Values  
 The following example uses BULK INSERT to bulk import data from the `myDepartment-c.Dat` file into the `AdventureWorks.HumanResources.myDepartment` table. The statement uses the `myDepartment-f-n-x.Xml` format file and includes the KEEPIDENTITY option to ensure that any identity values in the data file are retained.  
  
 In the [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] Query Editor, execute:  
  
```  
USE AdventureWorks;  
GO  
DELETE HumanResources.myDepartment;  
GO  
BULK INSERT HumanResources.myDepartment  
   FROM 'C:\myDepartment-n.Dat'  
   WITH (  
      KEEPIDENTITY,  
      FORMATFILE='C:\myDepartment-f-n-x.Xml'  
   );  
GO  
SELECT * FROM HumanResources.myDepartment;  
  
```  
  
### C. Using OPENROWSET and Keeping Identity Values  
 The following example uses the OPENROWSET bulk rowset provider to bulk import data from the `myDepartment-c.Dat` file into the `AdventureWorks.HumanResources.myDepartment` table. The statement uses the `myDepartment-f-n-x.Xml` format file and includes the KEEPIDENTITY hint to ensure that any identity values in the data file are retained.  
  
 In the [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] Query Editor, execute:  
  
```  
USE AdventureWorks;  
GO  
DELETE HumanResources.myDepartment;  
GO  
  
INSERT INTO HumanResources.myDepartment  
   with (KEEPIDENTITY)  
   (DepartmentID, Name, GroupName, ModifiedDate)  
   SELECT *  
      FROM  OPENROWSET(BULK 'C:\myDepartment-n.Dat',  
      FORMATFILE='C:\myDepartment-f-n-x.Xml') as t1;  
GO  
  
```  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
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
 [BACKUP &#40;Transact-SQL&#41;](../Topic/BACKUP%20\(Transact-SQL\).md)   
 [bcp Utility](../../Topics\TopicNameNotContainA/bcp-Utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](../Topic/BULK%20INSERT%20\(Transact-SQL\).md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../Topic/OPENROWSET%20\(Transact-SQL\).md)   
 [Table Hints &#40;Transact-SQL&#41;](../Topic/Table%20Hints%20\(Transact-SQL\).md)  
  
  