---
title: "Keep Identity Values When Bulk Importing Data (SQL Server)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-bulk-import-export
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 45894a3f-2d8a-4edd-9568-afa7d0d3061f
caps.latest.revision: 20
caps.handback.revision: 0
manager: jhubbard
---
# Keep Identity Values When Bulk Importing Data (SQL Server)
Data files that contain identity values can be bulk imported into an instance of [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. By default, the values for the identity column in the data file that is imported are ignored and [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] assigns unique values automatically. The unique values are based on the seed and increment values that are specified during table creation.  
  
 If the data file does not contain values for the identifier column in the table, use a format file to specify that the identifier column in the table should be skipped when importing data. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] assigns unique values for the column automatically.  
  
 To prevent [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] from assigning identity values while bulk importing data rows into a table, use the appropriate keep-identity command qualifier. When you specify a keep-identity qualifier, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] uses the identity values in the data file. These qualifiers are as follows:  
  
|Command|Keep-identity qualifier|Qualifier type|  
|-------------|------------------------------|--------------------|  
|**bcp**|**-E**|Switch|  
|BULK INSERT|KEEPIDENTITY|Argument|  
|INSERT ... SELECT * FROM OPENROWSET(BULK...)|KEEPIDENTITY|Table hint|  
  
 For more information, see [bcp Utility](../../Topics/TopicNameNotContainA/bcp-Utility.md), [BULK INSERT](assetId:///be3984e1-5ab3-4226-a539-a9f58e1e01e2), [OPENROWSET (Transact-SQL)](assetId:///f47eda43-33aa-454d-840a-bb15a031ca17), [INSERT (Transact-SQL)](assetId:///1054c76e-0fd5-4131-8c07-a6c5d024af50), [SELECT (Transact-SQL)](assetId:///dc85caea-54d1-49af-b166-f3aa2f3a93d0), and [Table Hint](assetId:///8bf1316f-c0ef-49d0-90a7-3946bc8e7a89).  
  
> [!NOTE]  
>  To create an automatically incrementing number that can be used in multiple tables or that can be called from applications without referencing any table, see [Sequence Numbers](../../Topics/TopicNameNotContainA/Sequence-Numbers.md).  
  
## Examples  
 The examples in this topic bulk import data using INSERT ... SELECT * FROM OPENROWSET(BULK...) and keeping default values.  
  
### Sample Table  
 The bulk-import examples require that a table named **myTestKeepNulls** table be created in the **AdventureWorks** sample database under the **dbo** schema. To create this table. in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] Query Editor, execute:  
  
```  
USE AdventureWorks;  
GO  
SELECT * INTO HumanResources.myDepartment   
   FROM HumanResources.Department  
      WHERE 1=0;  
GO  
SELECT * FROM HumanResources.myDepartment;  
```  
  
 The **Department** table on which `myDepartment` is based has IDENTITY_INSERT is set to OFF. Therefore, to import data into an identity column you must specify KEEPIDENTITY or **-E**.  
  
### Sample Data File  
 The data file used in the bulk-import examples contains data bulk exported from the `HumanResources.Department` table in native format. To create the data file, at the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows command prompt, enter:  
  
```  
bcp AdventureWorks.HumanResources.Department out myDepartment-n.Dat -n -T  
```  
  
### Sample Format File  
 This bulk-import examples use an XML format file, `myDepartment-f-x-n.Xml`, which uses native data formats. This example uses **bcp** to create to generate this format file from the `HumanResources.Department` table of the `AdventureWorks` database. At the Windows command prompt, enter:  
  
```  
bcp AdventureWorks.HumanResources.Department format nul -n -x -f myDepartment-f-n-x.Xml -T  
```  
  
 For more information about creating a format file, see [Create a Format File (SQL Server)](../../Topics/TopicNameContainA/Create-a-Format-File--SQL-Server-.md).  
  
### A. Using bcp and Keeping Identity Values  
 The following example demonstrates how to keep identity values when using **bcp** to bulk import data. The **bcp** command uses the format file, `myDepartment-f-n-x.Xml`, and contains the following switches:  
  
|Qualifiers|Description|  
|----------------|-----------------|  
|**-E**|Specifies that identity value or values in the data file are to be used for the identity column.|  
|**-T**|Specifies that the **bcp** utility connects to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] with a trusted connection.|  
  
 At the Windows command prompt, enter.  
  
```  
bcp AdventureWorks.HumanResources.myDepartment in C:\myDepartment-n.Dat -f C:\myDepartment-f-n-x.Xml -E -T  
  
```  
  
### B. Using BULK INSERT and Keeping Identity Values  
 The following example uses BULK INSERT to bulk import data from the `myDepartment-c.Dat` file into the `AdventureWorks.HumanResources.myDepartment` table. The statement uses the `myDepartment-f-n-x.Xml` format file and includes the KEEPIDENTITY option to ensure that any identity values in the data file are retained.  
  
 In the [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] Query Editor, execute:  
  
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
  
 In the [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] Query Editor, execute:  
  
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
 [BACKUP](assetId:///89a4658a-62f1-4289-8982-f072229720a1)   
 [bcp Utility](../../Topics/TopicNameNotContainA/bcp-Utility.md)   
 [BULK INSERT](assetId:///be3984e1-5ab3-4226-a539-a9f58e1e01e2)   
 [OPENROWSET (Transact-SQL)](assetId:///f47eda43-33aa-454d-840a-bb15a031ca17)   
 [Table Hint](assetId:///8bf1316f-c0ef-49d0-90a7-3946bc8e7a89)