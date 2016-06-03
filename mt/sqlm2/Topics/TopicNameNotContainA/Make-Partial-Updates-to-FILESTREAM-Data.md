---
title: Make Partial Updates to FILESTREAM Data
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-blob
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d6f7661e-6c14-4d31-9541-4520ca0f82b2
---
# Make Partial Updates to FILESTREAM Data
  An application uses FSCTL\_SQL\_FILESTREAM\_FETCH\_OLD\_CONTENT to make partial updates to FILESTREAM BLOB data. The [DeviceIoControl](http://go.microsoft.com/fwlink/?LinkId=105527) function passes this value and the handle that is returned from [OpenSqlFilestream](../../Topics\TopicNameNotContainA/Access-FILESTREAM-Data-with-OpenSqlFilestream.md) to the FILESTREAM driver. The driver then forces a server\-side copy of the current FILESTREAM data into the file that is referenced by the handle. If the application issues the FSCTL\_SQL\_FILESTREAM\_FETCH\_OLD\_CONTENT value after the handle has been written to, the last write operation persists and previous write operations that were made to the handle are lost.  
  
> [!NOTE]  
>  FILESTREAM relies on the [SMB protocol](http://go.microsoft.com/fwlink/?LinkId=112454) for remote access.  
  
## Example  
 The following example shows you how to use the `FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT` value to perform a partial update of an inserted FILESTREAM BLOB.  
  
> [!NOTE]  
>  This example requires the FILESTREAM\-enabled database and table that are created in [Create a FILESTREAM-Enabled Database](../../Topics\TopicNameContainA/Create-a-FILESTREAM-Enabled-Database.md) and [Create a Table for Storing FILESTREAM Data](../../Topics\TopicNameContainA/Create-a-Table-for-Storing-FILESTREAM-Data.md).  
  
 [!CODE [FILESTREAM#FS_CPP_FSCTL](../CodeSnippet/SQL15/tsql/filestream#fs_cpp_fsctl)]  
  
## See Also  
 [Access FILESTREAM Data with OpenSqlFilestream](../../Topics\TopicNameNotContainA/Access-FILESTREAM-Data-with-OpenSqlFilestream.md)   
 [Create Client Applications for FILESTREAM Data](../../Topics\TopicNameNotContainA/Create-Client-Applications-for-FILESTREAM-Data.md)  
  
  