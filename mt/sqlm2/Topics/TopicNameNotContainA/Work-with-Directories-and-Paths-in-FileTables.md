---
title: Work with Directories and Paths in FileTables
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-blob
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f1e45900-bea0-4f6f-924e-c11e1f98ab62
---
# Work with Directories and Paths in FileTables
  Describes the directory structure in which the files are stored in FileTables.  
  
##  <a name="HowToDirectories"></a> How To: Work with Directories and Paths in FileTables  
 You can use the following 3 functions to work with FileTable directories in [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]:  
  
|To get this result|Use this function|  
|------------------------|-----------------------|  
|Get the root\-level UNC path for a specific FileTable or for the current database.|[FileTableRootPath &#40;Transact-SQL&#41;](../Topic/FileTableRootPath%20\(Transact-SQL\).md)|  
|Get an absolute or relative UNC path for a file or directory in a FileTable.|[GetFileNamespacePath &#40;Transact-SQL&#41;](../Topic/GetFileNamespacePath%20\(Transact-SQL\).md)|  
|Get the path locator ID value for the specified file or directory in a FileTable, by providing the path.|[GetPathLocator &#40;Transact-SQL&#41;](../Topic/GetPathLocator%20\(Transact-SQL\).md)|  
  
##  <a name="BestPracticeRelativePaths"></a> How to: Use Relative Paths for Portable Code  
 To keep code and applications independent of the current computer and database, avoid writing code that relies on absolute file paths. Instead, get the complete path for a file at run time by using the [FileTableRootPath &#40;Transact-SQL&#41;](../Topic/FileTableRootPath%20\(Transact-SQL\).md) and [GetFileNamespacePath &#40;Transact-SQL&#41;](../Topic/GetFileNamespacePath%20\(Transact-SQL\).md)\) functions together, as shown in the following example. By default, the **GetFileNamespacePath** function returns the relative path of the file under the root path for the database.  
  
```tsql  
USE database_name;  
DECLARE @root nvarchar(100);  
DECLARE @fullpath nvarchar(1000);  
  
SELECT @root = FileTableRootPath();  
SELECT @fullpath = @root + file_stream.GetFileNamespacePath()  
    FROM filetable_name  
    WHERE name = N'document_name';  
  
PRINT @fullpath;  
GO  
```  
  
##  <a name="restrictions"></a> Important restrictions  
  
###  <a name="nesting"></a> Nesting level  
  
> [!IMPORTANT]  
>  You cannot store more than 15 levels of subdirectories in the FileTable directory. When you store 15 levels of subdirectories, then the lowest level cannot contain files, since these files would represent an additional level.  
  
###  <a name="fqnlength"></a> Length of full path name  
  
> [!IMPORTANT]  
>  The NTFS file system supports path names that are much longer than the 260\-character limit of the Windows shell and most Windows APIs. Therefore it is possible to create files in the file hierarchy of a FileTable by using Transact\-SQL that you cannot view or open with Windows Explorer or many other Windows applications, because the full path name exceeds 260 characters. However you can continue to access these files by using Transact\-SQL.  
  
##  <a name="fullpath"></a> The full path to an item stored in a FileTable  
 The full path to a file or directory stored in a FileTable begins with the following elements:  
  
1.  The share enabled for FILESTREAM file I\/O access at the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance level.  
  
2.  The **DIRECTORY\_NAME** specified at the database level.  
  
3.  The **FILETABLE\_DIRECTORY** specified at the FileTable level.  
  
 The resulting hierarchy looks like this:  
  
 `\\<machine>\<instance-level FILESTREAM share>\<database-level directory>\<FileTable directory>\`  
  
 This directory hierarchy forms the root of the FileTable’s file namespace. Under this directory hierarchy, the FILESTREAM data for the FileTable is stored as files, and as subdirectories which can also contain files and subdirectories.  
  
 It is important to keep in mind that the directory hierarchy created under the instance\-level FILESTREAM share is a virtual directory hierarchy. This hierarchy is stored in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database and is not represented physically in the NTFS file system. All operations that access files and directories under the FILESTREAM share and in the FileTables that it contains are intercepted and handled by a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] component embedded in the file system.  
  
##  <a name="roots"></a> The semantics of the root directories at the instance, database, and FileTable levels  
 This directory hierarchy observes the following semantics:  
  
-   The instance\-level FILESTREAM share is configured by an administrator and stored as a property of the server. You can rename this share by using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager. A renaming operation does not take effect until the server is restarted.  
  
-   The database\-level **DIRECTORY\_NAME** is null by default when you create a new database. An administrator can set or change this name by using the **ALTER DATABASE** statement. The name must be unique \(in a case\-insensitive comparison\) in that instance.  
  
-   You typically provide the **FILETABLE\_DIRECTORY** name as part of the **CREATE TABLE** statement when you create a FileTable. You can change this name by using the **ALTER TABLE** command.  
  
-   You cannot rename these root directories through file I\/O operations.  
  
-   You cannot open these root directories with exclusive file handles.  
  
##  <a name="is_directory"></a> The is\_directory column in the FileTable schema  
 The following table describes the interaction between the **is\_directory** column and the **file\_stream** column that contains the FILESTREAM data in a FileTable.  
  
||||  
|-|-|-|  
|*is\_directory* **value**|*file\_stream* **value**|**Behavior**|  
|FALSE|NULL|This is an invalid combination that will be caught by a system\-defined constraint.|  
|FALSE|\<value\>|The item represents a file.|  
|TRUE|NULL|The item represents a directory.|  
|TRUE|\<value\>|This is an invalid combination that will be caught by a system\-defined constraint.|  
  
##  <a name="alwayson"></a> Using Virtual Network Names \(VNNs\) with AlwaysOn Availability Groups  
 When the database that contains FILESTREAM or FileTable data belongs to an AlwaysOn availability group:  
  
-   The FILESTREAM and FileTable functions accept or return virtual network names \(VNNs\) instead of computer names. For more information about these functions, see [Filestream and FileTable Functions &#40;Transact-SQL&#41;](../Topic/Filestream%20and%20FileTable%20Functions%20\(Transact-SQL\).md).  
  
-   All access to FILESTREAM or FileTable data through the file system APIs should use VNNs instead of computer names. For more information, see [FILESTREAM and FileTable with AlwaysOn Availability Groups &#40;SQL Server&#41;](../Topic/FILESTREAM%20and%20FileTable%20with%20AlwaysOn%20Availability%20Groups%20\(SQL%20Server\).md).  
  
## See Also  
 [Enable the Prerequisites for FileTable](../../Topics\TopicNameNotContainA/Enable-the-Prerequisites-for-FileTable.md)   
 [Create, Alter, and Drop FileTables](../../Topics\TopicNameNotContainA/Create,-Alter,-and-Drop-FileTables.md)   
 [Access FileTables with Transact-SQL](../../Topics\TopicNameNotContainA/Access-FileTables-with-Transact-SQL.md)   
 [Access FileTables with File Input-Output APIs](../../Topics\TopicNameNotContainA/Access-FileTables-with-File-Input-Output-APIs.md)  
  
  