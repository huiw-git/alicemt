---
title: View the Size of the Sparse File of a Database Snapshot (Transact-SQL)
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1867c5f8-d57c-46d3-933d-3642ab0a8e24
---
# View the Size of the Sparse File of a Database Snapshot (Transact-SQL)
  This topic describes how to use [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] to verify that a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database file is a sparse file and to find out its actual and maximum sizes. Sparse files, which are a feature of the NTFS file system, are used by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database snapshots.  
  
> [!NOTE]  
>  During database snapshot creation, sparse files are created by using the file names in the CREATE DATABASE statement. These file names are stored in **sys.master\_files** in the **physical\_name** column. In **sys.database\_files** \(whether in the source database or in a snapshot\), the **physical\_name** column always contains the names of the source database files.  
  
## Verify that a Database File is a Sparse File  
  
1.  On the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]:  
  
     Select the **is\_sparse** column from either **sys.database\_files** in the database snapshot or from **sys.master\_files**. The value indicates whether the file is a sparse file, as follows:  
  
     1 \= File is a sparse file.  
  
     0 \= File is not a sparse file.  
  
## Find Out the Actual Size of a Sparse File  
  
> [!NOTE]  
>  Sparse files grow in 64\-kilobyte \(KB\) increments; thus, the size of a sparse file on disk is always a multiple of 64 KB.  
  
 To view the number of bytes that each sparse file of a snapshot is currently using on disk, query the **size\_on\_disk\_bytes** column of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)][sys.dm\_io\_virtual\_file\_stats](../Topic/sys.dm_io_virtual_file_stats%20\(Transact-SQL\).md) dynamic management view.  
  
 To view the disk space used by a sparse file, right\-click the file in Microsoft Windows, click **Properties**, and look at the **Size on disk** value.  
  
## Find Out the Maximum Size of a Sparse File  
 The maximum size to which a sparse can grow is the size of the corresponding source database file at the time of the snapshot creation. To learn this size, you can use one of the following alternatives:  
  
-   Using Windows Command Prompt:  
  
    1.  Use Windows **dir** commands.  
  
    2.  Select the sparse file, open the file **Properties** dialog box in Windows, and look at the **Size** value.  
  
-   On the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]:  
  
     Select the **size** column from either **sys.database\_files** in the database snapshot or from **sys.master\_files**. The value of **size** column reflects the maximum space, in SQL pages, that the snapshot can ever use; this value is equivalent to the Windows **Size** field, except that it is represented in terms of the number of SQL pages in the file; the size in bytes is:  
  
     \( *number\_of\_pages* \* 8192\)  
  
## See Also  
 [Database Snapshots &#40;SQL Server&#41;](../Topic/Database%20Snapshots%20\(SQL%20Server\).md)   
 [sys.fn_virtualfilestats &#40;Transact-SQL&#41;](../Topic/sys.fn_virtualfilestats%20\(Transact-SQL\).md)   
 [sys.database_files &#40;Transact-SQL&#41;](../Topic/sys.database_files%20\(Transact-SQL\).md)   
 [sys.master_files &#40;Transact-SQL&#41;](../Topic/sys.master_files%20\(Transact-SQL\).md)  
  
  