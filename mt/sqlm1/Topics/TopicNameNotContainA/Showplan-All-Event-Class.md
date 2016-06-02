---
title: Showplan All Event Class
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ee341319-c34a-43e3-ad33-6bfb1f85e314
---
# Showplan All Event Class
  The Showplan All event class occurs when [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] executes an SQL statement. The information included is a subset of the information available in the Showplan XML Statistics Profile or Showplan XML event class.  
  
 The Showplan All event class displays complete, compile\-time data, and so traces that contain Showplan All may incur significant performance overhead. To minimize this, limit use of this event class to traces that monitor specific problems for brief periods of time.  
  
 When the Showplan All event class is included in a trace, the BinaryData data column must be selected. If it is not, information for this event class will not be displayed in the trace.  
  
## Showplan All Event Class Data Columns  
  
|Data column name|Data type|Description|Column ID|Filterable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|**nvarchar**|Name of the client application that created the connection to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. This column is populated with the values passed by the application rather than the displayed name of the program.|10|Yes|  
|BinaryData|**image**|Estimated cost of the Showplan text.|2|No|  
|ClientProcessID|**int**|ID assigned by the host computer to the process where the client application is running. This data column is populated if the client process ID is provided by the client.|9|Yes|  
|DatabaseID|**Int**|ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance. [!INCLUDE[ssSqlProfiler](../../Token\Other/ssSqlProfiler_md.md)] displays the name of the database if the ServerName data column is captured in the trace and the server is available. Determine the value for a database by using the DB\_ID function.|3|Yes|  
|DatabaseName|**nvarchar**|Name of the database in which the user statement is running.|35|Yes|  
|Event Class|**Int**|Type of Event \= 97.|27|No|  
|EventSequence|**int**|Sequence of a given event within the request.|51|No|  
|GroupID|**int**|ID of the workload group where the SQL Trace event fires.|66|Yes|  
|HostName|**nvarchar**|Name of the computer on which the client is running. This data column is populated if the host name is provided by the client. To determine the host name, use the HOST\_NAME function.|8|Yes|  
|Integer Data|**Integer**|Estimated number of rows returned.|25|Yes|  
|IsSystem|**int**|Indicates whether the event occurred on a system process or a user process. 1 \= system, 0 \= user.|60|Yes|  
|LineNumber|**int**|Displays the number of the line containing the error.|5|Yes|  
|LoginName|**nvarchar**|Name of the login of the user \(either the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] security login or the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows login credentials in the form of DOMAIN\\username\).|11|Yes|  
|LoginSID|**image**|Security identification number \(SID\) of the logged\-in user. You can find this information in the sys.server\_principals catalog view. Each SID is unique for each login in the server.|41|No|  
|NestLevel|**int**|Integer representing the data returned by @@NESTLEVEL.|29|Yes|  
|NTDomainName|**nvarchar**|Windows domain to which the user belongs.|7|Yes|  
|ObjectID|**int**|System\-assigned ID of the object.|22|Yes|  
|ObjectName|**nvarchar**|Name of the object being referenced.|34|Yes|  
|ObjectType|**int**|Value representing the type of the object involved in the event. This value corresponds to the type column in sys.objects. For values, see [ObjectType Trace Event Column](../../Topics\TopicNameNotContainA/ObjectType-Trace-Event-Column.md).|28|Yes|  
|RequestID|**int**|ID of the request containing the statement.|49|Yes|  
|ServerName|**nvarchar**|Name of the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] being traced.|26|No|  
|SessionLoginName|**nvarchar**|Login name of the user who originated the session. For example, if you connect to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] using Login1 and execute a statement as Login2, SessionLoginName shows Login1 and LoginName shows Login2. This column displays both [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and Windows logins.|64|Yes|  
|SPID|**int**|ID of the session on which the event occurred.|12|Yes|  
|StartTime|**datetime**|Time at which the event started, if available.|14|Yes|  
|TransactionID|**bigint**|System\-assigned ID of the transaction.|4|Yes|  
|XactSequence|**bigint**|Token used to describe the current transaction.|50|Yes|  
  
## See Also  
 [SQL Server Profiler](../../Topics\TopicNameNotContainA/SQL-Server-Profiler.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../Topic/sp_trace_setevent%20\(Transact-SQL\).md)   
 [Showplan Logical and Physical Operators Reference](../../Topics\TopicNameNotContainA/Showplan-Logical-and-Physical-Operators-Reference.md)   
 [Showplan XML Statistics Profile Event Class](../../Topics\TopicNameNotContainA/Showplan-XML-Statistics-Profile-Event-Class.md)   
 [Showplan XML Event Class](../../Topics\TopicNameNotContainA/Showplan-XML-Event-Class.md)  
  
  