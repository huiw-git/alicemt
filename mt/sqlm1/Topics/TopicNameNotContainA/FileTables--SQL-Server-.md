---
title: FileTables (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-blob
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a57b629c-e9ed-48fd-9a48-ed3787d80c8f
---
# FileTables (SQL Server)
  The FileTable feature brings support for the Windows file namespace and compatibility with Windows applications to the file data stored in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. FileTable lets an application integrate its storage and data management components, and provides integrated [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] services \- including full\-text search and semantic search \- over unstructured data and metadata.  
  
 In other words, you can store files and documents in special tables in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] called FileTables, but access them from Windows applications as if they were stored in the file system, without making any changes to your client applications.  
  
 The FileTable feature builds on top of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] FILESTREAM technology. To learn more about FILESTREAM, see [FILESTREAM &#40;SQL Server&#41;](../Topic/FILESTREAM%20\(SQL%20Server\).md).  
  
##  <a name="Goals"></a> Benefits of the FileTable Feature  
 The goals of the FileTable feature include the following:  
  
-   Windows API compatibility for file data stored within a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database. Windows API compatibility includes the following:  
  
    -   Non\-transactional streaming access and in\-place updates to FILESTREAM data.  
  
    -   A hierarchical namespace of directories and files.  
  
    -   Storage of file attributes, such as created date and modified date.  
  
    -   Support for Windows file and directory management APIs.  
  
-   Compatibility with other [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] features including management tools, services, and relational query capabilities over FILESTREAM and file attribute data.  
  
 Thus FileTables remove a significant barrier to the use of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] for the storage and management of unstructured data that is currently residing as files on file servers. Enterprises can move this data from file servers into FileTables to take advantage of integrated administration and services provided by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. At the same time, they can maintain Windows application compatibility for their existing Windows applications that see this data as files in the file system.  
  
 [In This Topic](#TOP)  
  
##  <a name="Description"></a> What Is a FileTable?  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provides a special **table of files**, also referred to as a **FileTable**, for applications that require file and directory storage in the database, with Windows API compatibility and non\-transactional access. A FileTable is a specialized user table with a pre\-defined schema that stores FILESTREAM data, as well as file and directory hierarchy information and file attributes.  
  
 A FileTable provides the following functionality:  
  
-   A FileTable represents a hierarchy of directories and files. It stores data related to all the nodes in that hierarchy, for both directories and the files they contain. This hierarchy starts from a root directory that you specify when you create the FileTable.  
  
-   Every row in a FileTable represents a file or a directory.  
  
-   Every row contains the following items. For more information about the schema of a FileTable, see [FileTable Schema](../../Topics\TopicNameNotContainA/FileTable-Schema.md).  
  
    -   A**file\_stream** column for stream data and a **stream\_id** \(GUID\) identifier. \(The **file\_stream** column is NULL for a directory.\)  
  
    -   Both **path\_locator** and **parent\_path\_locator** columns for representing and maintaining the file and directory hierarchy.  
  
    -   10 file attributes such as created date and modified date that are useful with file I\/O APIs.  
  
    -   A type column that supports full\-text search and semantic search over files and documents.  
  
-   A FileTable enforces certain system\-defined constraints and triggers to maintain file namespace semantics.  
  
-   When the database is configured for non\-transactional access, the file and directory hierarchy represented in the FileTable is exposed under the FILESTREAM share configured for the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance. This provides file system access for Windows applications.  
  
 Some additional characteristics of FileTables include the following:  
  
-   The file and directory data stored in a FileTable is exposed through a Windows share for non\-transactional file access for Windows API based applications. For a Windows application, this looks like a normal share with its files and directories. Applications can use a rich set of Windows APIs to manage the files and directories under this share.  
  
-   The directory hierarchy surfaced through the share is a purely logical directory structure that is maintained within the FileTable.  
  
-   Calls to create or change a file or directory through the Windows share are intercepted by a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] component and reflected in the corresponding relational data in the FileTable.  
  
-   Windows API operations are non\-transactional in nature, and are not associated with user transactions. However, transactional access to FILESTREAM data stored in a FileTable is fully supported, as is the case for any FILESTREAM column in a regular table.  
  
-   FileTables can also be queried and updated through normal [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] access. They are also integrated with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] management tools, and features such as backup.  
  
 [In This Topic](#TOP)  
  
##  <a name="additional"></a> Additional Considerations for Using FileTables  
  
###  <a name="DBA"></a> Administrative Considerations  
 **About FILESTREAM and FileTables**  
  
-   You configure FileTables separately from FILESTREAM. Therefore you can continue to use the FILESTREAM feature without enabling non\-transactional access or creating FileTables.  
  
-   There is no non\-transactional access to FILESTREAM data except through FileTables. Therefore, when you enable non\-transactional access, the behavior of existing FILESTREAM columns and applications is not affected.  
  
 **About FileTables and non\-transactional access**  
  
-   You can enable or disable non\-transactional access at the database level.  
  
-   You can configure or fine\-tune non\-transactional access at the database level by turning it off, or by enabling read only or full read\/write access.  
  
 [In This Topic](#TOP)  
  
###  <a name="memory"></a> FileTables Do Not Support Memory\-Mapped Files  
 FileTables do not support memory\-mapped files. Notepad and Paint are two common examples of applications that use memory\-mapped files. You cannot use these applications on the same computer as [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to open files that are stored in a FileTable. However you can use these applications from a remote computer to open files that are stored in a FileTable, because in these circumstances the memory\-mapping feature is not used.  
  
 [In This Topic](#TOP)  
  
##  <a name="reltasks"></a> Related Tasks  
 [Enable the Prerequisites for FileTable](../../Topics\TopicNameNotContainA/Enable-the-Prerequisites-for-FileTable.md)  
 Describes how to enable the prerequisites for creating and using FileTables.  
  
 [Create, Alter, and Drop FileTables](../../Topics\TopicNameNotContainA/Create,-Alter,-and-Drop-FileTables.md)  
 Describes how to create a new FileTable, or alter or drop an existing FileTable.  
  
 [Load Files into FileTables](../../Topics\TopicNameNotContainA/Load-Files-into-FileTables.md)  
 Describes how to load or migrate files into FileTables.  
  
 [Work with Directories and Paths in FileTables](../../Topics\TopicNameNotContainA/Work-with-Directories-and-Paths-in-FileTables.md)  
 Describes the directory structure in which the files are stored in FileTables.  
  
 [Access FileTables with Transact-SQL](../../Topics\TopicNameNotContainA/Access-FileTables-with-Transact-SQL.md)  
 Describes how Transact\-SQL data manipulation language \(DML\) commands work with FileTables.  
  
 [Access FileTables with File Input-Output APIs](../../Topics\TopicNameNotContainA/Access-FileTables-with-File-Input-Output-APIs.md)  
 Describes how file system I\/O works on a FileTable.  
  
 [Manage FileTables](../../Topics\TopicNameNotContainA/Manage-FileTables.md)  
 Describes common administrative tasks for managing FileTables.  
  
 [In This Topic](#TOP)  
  
##  <a name="relcontent"></a> Related Content  
 [FileTable Schema](../../Topics\TopicNameNotContainA/FileTable-Schema.md)  
 Describes the pre\-defined and fixed schema of a FileTable.  
  
 [FileTable Compatibility with Other SQL Server Features](../../Topics\TopicNameNotContainA/FileTable-Compatibility-with-Other-SQL-Server-Features.md)  
 Describes how FileTables work with other features of SQL Server.  
  
 [FileTable DDL, Functions, Stored Procedures, and Views](../../Topics\TopicNameNotContainA/FileTable-DDL,-Functions,-Stored-Procedures,-and-Views.md)  
 Lists the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements and the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database objects that have been added or changed to support the FileTable feature.  
  
 [In This Topic](#TOP)  
  
  