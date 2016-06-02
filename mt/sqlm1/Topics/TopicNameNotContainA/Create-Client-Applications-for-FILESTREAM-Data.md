---
title: Create Client Applications for FILESTREAM Data
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-blob
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8a02aff6-e54c-40c6-a066-2083e9b090aa
---
# Create Client Applications for FILESTREAM Data
  You can use Win32 to read and write data to a FILESTREAM BLOB. The following steps are required:  
  
-   Read the FILESTREAM file path.  
  
-   Read the current transaction context.  
  
-   Obtain a Win32 handle and use the handle to read and write data to the FILESTREAM BLOB.  
  
> [!NOTE]  
>  The examples in this topic require the FILESTREAM\-enabled database and table that are created in [Create a FILESTREAM-Enabled Database](../../Topics\TopicNameContainA/Create-a-FILESTREAM-Enabled-Database.md) and [Create a Table for Storing FILESTREAM Data](../../Topics\TopicNameContainA/Create-a-Table-for-Storing-FILESTREAM-Data.md).  
  
##  <a name="func"></a> Functions for Working with FILESTREAM Data  
 When you use FILESTREAM to store binary large object \(BLOB\) data, you can use Win32 APIs to work with the files. To support working with FILESTREAM BLOB data in Win32 applications, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provides the following functions and API:  
  
-   [PathName](../Topic/PathName%20\(Transact-SQL\).md) returns a path as a token to a BLOB. An application uses this token to obtain a Win32 handle and operate on BLOB data.  
  
     When the database that contains FILESTREAM data belongs to an Always On availability group, then the PathName function returns a virtual network name \(VNN\) instead of a computer name.  
  
-   [GET\_FILESTREAM\_TRANSACTION\_CONTEXT\(\)](../Topic/GET_FILESTREAM_TRANSACTION_CONTEXT%20\(Transact-SQL\).md) returns a token that represents the current transaction of a session. An application uses this token to bind FILESTREAM file system streaming operations to the transaction.  
  
-   The [OpenSqlFilestream API](../../Topics\TopicNameNotContainA/Access-FILESTREAM-Data-with-OpenSqlFilestream.md) obtains a Win32 file handle. The application uses the handle to stream the FILESTREAM data, and can then pass the handle to the following Win32 APIs: [ReadFile](http://go.microsoft.com/fwlink/?LinkId=86422), [WriteFile](http://go.microsoft.com/fwlink/?LinkId=86423), [TransmitFile](http://go.microsoft.com/fwlink/?LinkId=86424), [SetFilePointer](http://go.microsoft.com/fwlink/?LinkId=86425), [SetEndOfFile](http://go.microsoft.com/fwlink/?LinkId=86426), or [FlushFileBuffers](http://go.microsoft.com/fwlink/?LinkId=86427). If the application calls any other API by using the handle, an ERROR\_ACCESS\_DENIED error is returned. The application should close the handle by using [CloseHandle](http://go.microsoft.com/fwlink/?LinkId=86428).  
  
 All FILESTREAM data container access is performed in a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] transaction. [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements can be executed in the same transaction to maintain consistency between SQL data and FILESTREAM data.  
  
##  <a name="steps"></a> Steps for Accessing FILESTREAM Data  
  
###  <a name="path"></a> Reading the FILESTREAM File Path  
 Each cell in a FILESTREAM table has a file path that is associated with it. To read the path, use the **PathName** property of a **varbinary\(max\)** column in a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement. The following example shows how to read the file path of a **varbinary\(max\)** column.  
  
 [!CODE [FILESTREAM#FS_PathName](../CodeSnippet/SQL15/tsql/filestream#fs_pathname)]  
  
###  <a name="trx"></a> Reading the Transaction Context  
 To obtain the current transaction context, use the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] [GET\_FILESTREAM\_TRANSACTION\_CONTEXT\(\)](../Topic/GET_FILESTREAM_TRANSACTION_CONTEXT%20\(Transact-SQL\).md) function. The following example shows how to begin a transaction and read the current transaction context.  
  
 [!CODE [FILESTREAM#FS_GET_TRANSACTION_CONTEXT](../CodeSnippet/SQL15/tsql/filestream#fs_get_transaction_context)]  
  
###  <a name="handle"></a> Obtaining a Win32 File Handle  
 To obtain a Win32 file handle, call the OpenSqlFilestream API. This API is exported from the sqlncli.dll file. The returned handle can be passed to any of the following Win32 APIs: [ReadFile](http://go.microsoft.com/fwlink/?LinkId=86422), [WriteFile](http://go.microsoft.com/fwlink/?LinkId=86423), [TransmitFile](http://go.microsoft.com/fwlink/?LinkId=86424), [SetFilePointer](http://go.microsoft.com/fwlink/?LinkId=86425), [SetEndOfFile](http://go.microsoft.com/fwlink/?LinkId=86426), or [FlushFileBuffers](http://go.microsoft.com/fwlink/?LinkId=86427). The following examples show you how to obtain a Win32 File handle and use it to read and write data to a FILESTREAM BLOB.  
  
 [!CODE [FILESTREAM#FS_CS_ReadAndWriteBLOB](../CodeSnippet/SQL15/tsql/filestream#fs_cs_readandwriteblob)]  
  
 [!CODE [FILESTREAM#FS_VB_ReadAndWriteBLOB](../CodeSnippet/SQL15/tsql/filestream#fs_vb_readandwriteblob)]  
  
 [!CODE [FILESTREAM#FS_CPP_WriteBLOB](../CodeSnippet/SQL15/tsql/filestream#fs_cpp_writeblob)]  
  
##  <a name="best"></a> Best Practices for Application Design and Implementation  
  
-   When you are designing and implementing applications that use FILESTREAM, consider the following guidelines:  
  
-   Use NULL instead of 0x to represent a non\-initialized FILESTREAM column. The 0x value causes a file to be created, and NULL does not.  
  
-   Avoid insert and delete operations in tables that contain nonnull FILESTREAM columns. Insert and delete operations can modify the FILESTREAM tables that are used for garbage collection. This can cause an application's performance to decrease over time.  
  
-   In applications that use replication, use NEWSEQUENTIALID\(\) instead of NEWID\(\). NEWSEQUENTIALID\(\) performs better than NEWID\(\) for GUID generation in these applications.  
  
-   The FILESTREAM API is designed for Win32 streaming access to data. Avoid using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] to read or write FILESTREAM binary large objects \(BLOBs\) that are larger than 2 MB. If you must read or write BLOB data from [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], make sure that all BLOB data is consumed before you try to open the FILESTREAM BLOB from Win32. Failure to consume all the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] data might cause any successive FILESTREAM open or close operations to fail.  
  
-   Avoid [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements that update, append or prepend data to the FILESTREAM BLOB. This causes the BLOB data to be spooled into the tempdb database and then back into a new physical file.  
  
-   Avoid appending small BLOB updates to a FILESTREAM BLOB. Each append causes the underlying FILESTREAM files to be copied. If an application has to append small BLOBs, write the BLOBs into a **varbinary\(max\)** column, and then perform a single write operation to the FILESTREAM BLOB when the number of BLOBs reaches a predetermined limit.  
  
-   Avoid retrieving the data length of lots of BLOB files in an application. This is a time\-consuming operation because the size is not stored in the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]. If you must determine the length of a BLOB file, use the [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] DATALENGTH\(\) function to determine the size of the BLOB if it is closed. DATALENGTH\(\) does not open the BLOB file to determine its size.  
  
-   If an application uses Message Block1 \(SMB1\) protocol, FILESTREAM BLOB data should be read in 60\-KB multiples to optimize performance.  
  
## See Also  
 [Avoid Conflicts with Database Operations in FILESTREAM Applications](../../Topics\TopicNameNotContainA/Avoid-Conflicts-with-Database-Operations-in-FILESTREAM-Applications.md)   
 [Access FILESTREAM Data with OpenSqlFilestream](../../Topics\TopicNameNotContainA/Access-FILESTREAM-Data-with-OpenSqlFilestream.md)   
 [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../Topic/Binary%20Large%20Object%20\(Blob\)%20Data%20\(SQL%20Server\).md)   
 [Make Partial Updates to FILESTREAM Data](../../Topics\TopicNameNotContainA/Make-Partial-Updates-to-FILESTREAM-Data.md)  
  
  