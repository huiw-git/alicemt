---
title: Access FILESTREAM Data with OpenSqlFilestream
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-blob
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - OpenSqlFilestream
apilocation: 
  - sqlncli11.dll
apitype: dllExport
ms.assetid: d8205653-93dd-4599-8cdf-f9199074025f
---
# Access FILESTREAM Data with OpenSqlFilestream
  The OpenSqlFilestream API obtains a Win32 compatible file handle for a FILESTREAM binary large object \(BLOB\) stored in the file system. The handle can be passed to any of the following Win32 APIs: [ReadFile](http://go.microsoft.com/fwlink/?LinkId=86422), [WriteFile](http://go.microsoft.com/fwlink/?LinkId=86423), [TransmitFile](http://go.microsoft.com/fwlink/?LinkId=86424), [SetFilePointer](http://go.microsoft.com/fwlink/?LinkId=86425), [SetEndOfFile](http://go.microsoft.com/fwlink/?LinkId=86426), or [FlushFileBuffers](http://go.microsoft.com/fwlink/?LinkId=86427). If you pass this handle to any other Win32 API, the error ERROR\_ACCESS\_DENIED is returned. The handle must be closed by passing it to the Win32 [CloseHandle](http://go.microsoft.com/fwlink/?LinkId=86428) API before the transaction is committed or rolled back. Failing to close the handle will cause server\-side resource leaks.  
  
 You must perform All FILESTREAM data container access in a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] transaction. [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statements can also be executed in the same transaction. This maintains consistency between the SQL data and FILESTREAM BLOB data.  
  
 To access the FILESTREAM BLOB by using Win32, [Windows Authorization](../../Topics\TopicNameNotContainA/Choose-an-Authentication-Mode.md) must be enabled.  
  
> [!IMPORTANT]  
>  When the file is opened for write access, the transaction is owned by the FILESTREAM agent. Only Win32 file I\/O is allowed until the transaction is released. To release the transaction, the write handle must be closed.  
  
## Syntax  
  
```  
  
HANDLE OpenSqlFilestream (  
    LPCWSTR FilestreamPath,  
    SQL_FILESTREAM_DESIRED_ACCESS DesiredAccess,  
    ULONG OpenOptions,  
    LPBYTE FilestreamTransactionContext,  
    SIZE_T FilestreamTransactionContextLength,  
    PLARGE_INTEGER AllocationSize);  
```  
  
#### Parameters  
 *FilestreamPath*  
 \[in\] Is the **nvarchar\(max\)** path that is returned by the [PathName](../Topic/PathName%20\(Transact-SQL\).md) function. PathName must be called from the context of an account that has [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] SELECT or UPDATE permissions on the FILESTREAM table and column.  
  
 *DesiredAccess*  
 \[in\] Sets the mode used to access FILESTREAM BLOB data. This value is passed to the [DeviceIoControl Function](http://go.microsoft.com/fwlink/?LinkId=105527).  
  
|Name|Value|Meaning|  
|----------|-----------|-------------|  
|SQL\_FILESTREAM\_READ|0|Data can be read from the file.|  
|SQL\_FILESTREAM\_WRITE|1|Data can be written to the file.|  
|SQL\_FILESTREAM\_READWRITE|2|Data can be read and written from the file.|  
  
> [!NOTE]  
>  These values are defined in the SQL\_FILESTREAM\_DESIRED\_ACCESS enumeration in sqlncli.h.  
  
 *OpenOptions*  
 \[in\] The file attributes and flags. This parameter can also include any combination of the following flags.  
  
|Flag|Value|Meaning|  
|----------|-----------|-------------|  
|SQL\_FILESTREAM\_OPEN\_NONE|0x00000000:|The file is being opened or created with no special options.|  
|SQL\_FILESTREAM\_OPEN\_FLAG\_ASYNC|0x00000001L|The file is being opened or created for asynchronous I\/O.|  
|SQL\_FILESTREAM\_OPEN\_FLAG\_NO\_BUFFERING|0x00000002L|The system opens the file by using no system caching.|  
|SQL\_FILESTREAM\_OPEN\_FLAG\_NO\_WRITE\_THROUGH|0x00000004L|The system does not write through an intermediate cache. Writes go directly to disk.|  
|SQL\_FILESTREAM\_OPEN\_FLAG\_SEQUENTIAL\_SCAN|0x00000008L|A file is accessed sequentially from beginning to end. The system can use this as a hint to optimize file caching. If an application moves the file pointer for random access, optimal caching may not occur.|  
|SQL\_FILESTREAM\_OPEN\_FLAG\_RANDOM\_ACCESS|0x00000010L|A file is accessed randomly. The system can use this as a hint to optimize file caching.|  
  
 *FilestreamTransactionContext*  
 \[in\] The value that is returned by the [GET\_FILESTREAM\_TRANSACTION\_CONTEXT](../Topic/GET_FILESTREAM_TRANSACTION_CONTEXT%20\(Transact-SQL\).md) function.  
  
 *FilestreamTransactionContextLength*  
 \[in\] Number of bytes in the **varbinary\(max\)** data that is returned by the GET\_FILESTREAM\_TRANSACTION\_CONTEXT function. The function returns an array of N bytes. N is determined by the function and is a property of the byte array that is returned.  
  
 *AllocationSize*  
 \[in\] Specifies the initial allocation size of the data file in bytes. It is ignored in read mode. This parameter can be NULL, in which case the default file system behavior is used.  
  
## Return Value  
 If the function succeeds, the return value is an open handle to a specified file. If the function fails, the return value is INVALID\_HANDLE\_VALUE. For extended error information, call GetLastError\(\).  
  
## Examples  
 The following examples show you how to use the `OpenSqlFilestream` API to obtain a Win32 handle.  
  
 [!CODE [FILESTREAM#FS_CS_ReadAndWriteBLOB](../CodeSnippet/SQL15/tsql/filestream#fs_cs_readandwriteblob)]  
  
 [!CODE [FILESTREAM#FS_VB_ReadAndWriteBLOB](../CodeSnippet/SQL15/tsql/filestream#fs_vb_readandwriteblob)]  
  
 [!CODE [FILESTREAM#FS_CPP_WriteBLOB](../CodeSnippet/SQL15/tsql/filestream#fs_cpp_writeblob)]  
  
## Remarks  
 The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Native Client must be installed to use this API. The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Native Client is installed with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] client tools. For more information, see [Installing SQL Server Native Client](../Topic/Installing%20SQL%20Server%20Native%20Client.md).  
  
## See Also  
 [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../Topic/Binary%20Large%20Object%20\(Blob\)%20Data%20\(SQL%20Server\).md)   
 [Make Partial Updates to FILESTREAM Data](../../Topics\TopicNameNotContainA/Make-Partial-Updates-to-FILESTREAM-Data.md)   
 [Avoid Conflicts with Database Operations in FILESTREAM Applications](../../Topics\TopicNameNotContainA/Avoid-Conflicts-with-Database-Operations-in-FILESTREAM-Applications.md)  
  
  