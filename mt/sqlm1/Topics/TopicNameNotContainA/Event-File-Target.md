---
title: Event File Target
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4f0ee6ec-a0a8-4c38-aa61-8293ab6ac7fd
---
# Event File Target
  The event file target is a target that writes complete buffers to disk.  
  
 The following table describes the available options for configuring the event file target.  
  
|Option|Allowed values|Description|  
|------------|--------------------|-----------------|  
|filename|Any string up to 260 characters. This value is required.|The file location and filename.<br /><br /> You can use any filename extension.|  
|max\_file\_size|Any 64 bit integer. This value is optional.|The maximum file size in megabytes \(MB\). If max\_file\_size is not specified, the file will grow until the disk is full. The default file size is 1GB.<br /><br /> max\_file\_size must be larger than the current size of the session buffers. If it is not, the file target will fail to initialize, reporting that the max\_file\_size is invalid. To view the current size of the buffers, query the buffer\_size column in the [sys.dm\_xe\_sessions](../Topic/sys.dm_xe_sessions%20\(Transact-SQL\).md) dynamic management view.<br /><br /> If the default file size is smaller than the session buffer size, we recommend setting max\_file\_size to the value specified in the max\_memory column in the [sys.server\_event\_sessions](../Topic/sys.server_event_sessions%20\(Transact-SQL\).md) catalog view.<br /><br /> When max\_file\_size is set to a size larger than the size of the session buffers, it may be rounded down to the nearest multiple of the session buffer size. This may create a target file that is smaller than the specified value of max\_file\_size. For example, if the buffer size is 100MB and max\_file\_size is set to 150MB, the resultant file size is rounded down to 100MB because a second buffer would not fit in the remaining 50MB of space.<br /><br /> If the default file size is smaller than the session buffer size, we recommend setting max\_file\_size to the value in the max\_memory column in the [sys.server\_event\_sessions](../Topic/sys.server_event_sessions%20\(Transact-SQL\).md) catalog view.|  
|max\_rollover\_files|Any 32 bit integer. This value is optional.|The maximum number of files to retain in the file system. The default value is 5.|  
|increment|Any 32 bit integer. This value is optional.|The incremental growth, in megabytes \(MB\), for the file. If unspecified, the default value for increment is twice the session buffer size.|  
  
 The first time that an event file target is created, the filename you specify is appended with \_0\_ and a long integer value. The integer value is calculated as the number of milliseconds between January 1, 1600 and the date and time the file is created. Subsequent rollover files also use this format. From examining the value of the long integer, you can determine the most current file. The following example illustrates how files are named in a scenario where you specify the filename option as C:\\OutputFiles\\MyOutput.xel:  
  
-   first file created \- C:\\OutputFiles\\MyOutput\_0\_128500310259380000.xel  
  
-   first rollover file \- C:\\OutputFiles\\MyOutput\_0\_128505831770890000.xel  
  
-   second rollover file \- C:\\OutputFiles\\MyOutput\_0\_132410772966237000.xel  
  
## Adding the Target to a Session  
 To add the event file target to an Extended Events session, you would include the following statements when you create or alter an event session, replacing *file\_name* with the desired file name and path:  
  
```  
ADD TARGET package0.event_file(  
   SET filename='file_name.xel')  
```  
  
## Reviewing the Target Output  
 To review the output from the file target, you must use the sys.fn\_xe\_file\_target\_read\_file function. We recommend that you cast the data as XML. You can use the following syntax, replacing *file\_name* with the file name and path that you specified when you added the target:  
  
```  
SELECT *, CAST(event_data AS XML) AS 'event_data_XML'  
FROM sys.fn_xe_file_target_read_file('file_name*.xel', NULL, NULL, NULL)  
```  
  
## See Also  
 [SQL Server Extended Events Targets](../../Topics\TopicNameNotContainA/SQL-Server-Extended-Events-Targets.md)   
 [sys.fn_xe_file_target_read_file &#40;Transact-SQL&#41;](../Topic/sys.fn_xe_file_target_read_file%20\(Transact-SQL\).md)   
 [CREATE EVENT SESSION &#40;Transact-SQL&#41;](../Topic/CREATE%20EVENT%20SESSION%20\(Transact-SQL\).md)   
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](../Topic/ALTER%20EVENT%20SESSION%20\(Transact-SQL\).md)  
  
  