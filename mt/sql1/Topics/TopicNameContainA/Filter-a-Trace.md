---
title: "Filter a Trace"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 019c10ab-68f6-4e40-a5e8-735b2e1270db
caps.latest.revision: 29
manager: jhubbard
---
# Filter a Trace
Filters limit the events collected in a trace. If a filter is not set, all events of the selected event classes are returned in the trace output. For example, limiting the Windows user names in a trace to specific users reduces the output data to those users only.  
  
 It is not mandatory to set a filter for a trace. However, a filter minimizes the overhead that is incurred during a trace. A filter returns focused data and thus makes performance analysis and audits easier.  
  
 To filter the event data captured within a trace, select trace event criteria that return only relevant data from the trace. For example, you can include or exclude monitoring the activity of a specific application from the trace.  
  
> [!NOTE]  
>  When [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)] creates traces, it filters out its own activity by default.  
  
 As an additional example, if you monitor queries to determine the batches that take the longest time to execute, set the trace event criteria to monitor only those batches that take longer than 30 seconds to execute (a CPU minimum value of 30,000 milliseconds).  
  
## Filter Creation Guidelines  
 In general, follow these steps to filter a trace.  
  
1.  Identify the events that you want to include in the trace.  
  
2.  Identify the data and data columns that contain the information you need.  
  
3.  Identify a subset of the data you need and define filters based on that subset of data.  
  
 For example, you may be interested only in events that take longer than a certain length of time. You could create a trace that includes events where the **Duration** data column is greater than 300 milliseconds. Your trace will not include events that finish in less than 300 milliseconds.  
  
 You can create filters by using SQL Server Profiler or Transact-SQL stored procedures.  
  
 **To filter events in a trace template**  
  
 [Filter Events in a Trace (SQL Server Profiler)](../../Topics/TopicNameContainA/Filter-Events-in-a-Trace--SQL-Server-Profiler-.md)  
  
 [Set a Trace Filter (Transact-SQL)](../../Topics/TopicNameContainA/Set-a-Trace-Filter--Transact-SQL-.md)  
  
 **To modify filters**  
  
 [Modify a Filter (SQL Server Profiler)](../../Topics/TopicNameContainA/Modify-a-Filter--SQL-Server-Profiler-.md)  
  
 Filter availability depends on the data column. Some data columns cannot be filtered. The data columns that can be filtered are filterable only by certain relational operators, as shown in the following table.  
  
|Relational operator|Operator symbol|Description|  
|-------------------------|---------------------|-----------------|  
|Like|LIKE|Specifies that the trace event data must be like the text entered. Allows multiple values.|  
|Not like|NOT LIKE|Specifies that the trace event data must not be like the text entered. Allows multiple values.|  
|Equals|=|Specifies that the trace event data must equal the value entered. Allows multiple values.|  
|Not equal to|<>|Specifies that the trace event data must not equal the value entered. Allows multiple values.|  
|Greater than|>|Specifies that the trace event data must be greater than the value entered.|  
|Greater than or equal to|>=|Specifies that the trace event data must be greater than or equal to the value entered.|  
|Less than|<|Specifies that the trace event data must be less than the value entered.|  
|Less than or equal to|<=|Specifies that the trace event data must be less than or equal to the value entered.|  
  
 The following table lists the filterable data columns and the available relational operators.  
  
|Data columns|Relational operators|  
|------------------|--------------------------|  
|**ApplicationName**|LIKE, NOT LIKE|  
|**BigintData1**|=, <>, >=, <=|  
|**BigintData2**|=, <>, >=, <=|  
|**BinaryData**|Use [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)] to filter events in this data column. For more information, see [Filter Traces with SQL Server Profiler](../../Topics/TopicNameNotContainA/Filter-Traces-with-SQL-Server-Profiler.md).|  
|**ClientProcessID**|=, <>, >=, <=|  
|**ColumnPermissions**|=, <>, >=, <=|  
|**CPU**|=, <>, >=, <=|  
|**DatabaseID**|=, <>, >=, <=|  
|**DatabaseName**|LIKE, NOT LIKE|  
|**DBUserName**|LIKE, NOT LIKE|  
|**Duration**|=, <>, >=, <=|  
|**EndTime**|>=, <=|  
|**Error**|=, <>, >=, <=|  
|**EventSubClass**|=, <>, >=, <=|  
|**FileName**|LIKE, NOT LIKE|  
|**GUID**|Use [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)] to filter events in this data column. For more information, see [Filter Traces with SQL Server Profiler](../../Topics/TopicNameNotContainA/Filter-Traces-with-SQL-Server-Profiler.md).|  
|**Handle**|=, <>, >=, <=|  
|**HostName**|LIKE, NOT LIKE|  
|**IndexID**|=, <>, >=, <=|  
|**IntegerData**|=, <>, >=, <=|  
|**IntegerData2**|=, <>, >=, <=|  
|**IsSystem**|=, <>, >=, <=|  
|**LineNumber**|=, <>, >=, <=|  
|**LinkedServerName**|LIKE, NOT LIKE|  
|**LoginName**|LIKE, NOT LIKE|  
|**LoginSid**|Use [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)] to filter events in this data column. For more information, see [Filter Traces with SQL Server Profiler](../../Topics/TopicNameNotContainA/Filter-Traces-with-SQL-Server-Profiler.md).|  
|**MethodName**|LIKE, NOT LIKE|  
|**Mode**|=, <>, >=, <=|  
|**NestLevel**|=, <>, >=, <=|  
|**NTDomainName**|LIKE, NOT LIKE|  
|**NTUserName**|LIKE, NOT LIKE|  
|**ObjectID**|=, <>, >=, <=|  
|**ObjectID2**|=, <>, >=, <=|  
|**ObjectName**|LIKE, NOT LIKE|  
|**ObjectType**|=, <>, >=, <=|  
|**Offset**|=, <>, >=, <=|  
|**OwnerID**|=, <>, >=, <=|  
|**OwnerName**|LIKE, NOT LIKE|  
|**ParentName**|LIKE, NOT LIKE|  
|**Permissions**|=, <>, >=, <=|  
|**ProviderName**|LIKE, NOT LIKE|  
|**Reads**|=, <>, >=, <=|  
|**RequestID**|=, <>, >=, <=|  
|**RoleName**|LIKE, NOT LIKE|  
|**RowCounts**|=, <>, >=, <=|  
|**SessionLoginName**|LIKE, NOT LIKE|  
|**Severity**|=, <>, >=, <=|  
|**SourceDatabaseID**|=, <>, >=, <=|  
|**SPID**|=, <>, >=, <=|  
|**SqlHandle**|Use [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)] to filter events in this data column. For more information, see [Filter Traces with SQL Server Profiler](../../Topics/TopicNameNotContainA/Filter-Traces-with-SQL-Server-Profiler.md).|  
|**StartTime**|>=, <=|  
|**State**|=, <>, >=, <=|  
|**Success**|=, <>, >=, <=|  
|**TargetLoginName**|LIKE, NOT LIKE|  
|**TargetLoginSid**|Use [!INCLUDE[ssSqlProfiler](../../Topics/TopicNameContainA/tokens/ssSqlProfiler_md.md)] to filter events in this data column. For more information, see [Filter Traces with SQL Server Profiler](../../Topics/TopicNameNotContainA/Filter-Traces-with-SQL-Server-Profiler.md).|  
|**TargetUserName**|LIKE, NOT LIKE|  
|**TextData** *|LIKE, NOT LIKE|  
|**TransactionID**|=, <>, >=, <=|  
|**Type**|=, <>, >=, <=|  
|**Writes**|=, <>, >=, <=|  
|**XactSequence**|=, <>, >=, <=|  
  
 \* If tracing events from the **osql** utility or the **sqlcmd** utility, always append **%** to filters on the **TextData** data column.  
  
 As a security precaution, SQL Trace automatically omits from the trace any information from security-related stored procedures that affect passwords. This security mechanism is nonconfigurable and is always in effect. It prevents users, who otherwise have permissions to trace all activity on [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], from capturing passwords.  
  
 The following security-related stored procedures are monitored, but no output is written to the **TextData** data column:  
  
 [sp_addapprole (Transact-SQL)](assetId:///24200295-9a54-4cab-9922-fb2e88632721)  
  
 [sp_adddistpublisher (Transact-SQL)](assetId:///04e15011-a902-4074-b38c-3ec2fc73b838)  
  
 [sp_adddistributiondb (Transact-SQL)](assetId:///e9bad56c-d2b3-44ba-a4d7-ff2fd842e32d)  
  
 [sp_adddistributor (Transact-SQL)](assetId:///35415502-68d0-40f6-993c-180e50004f1e)  
  
 [sp_addlinkedserver (Transact-SQL)](assetId:///fed3adb0-4c15-4a1a-8acd-1b184aff558f)  
  
 [sp_addlinkedsrvlogin (Transact-SQL)](assetId:///eb69f303-1adf-4602-b6ab-f62e028ed9f6)  
  
 [sp_addlogin (Transact-SQL)](assetId:///030f19c3-a5e3-4b53-bfc4-de4bfca0fddc)  
  
 [sp_addmergepullsubscription_agent (Transact-SQL)](assetId:///a2f4b086-078d-49b5-8971-8a1e3f6a6feb)  
  
 [sp_addpullsubscription_agent (Transact-SQL)](assetId:///b9c2eaed-6d2d-4b78-ae9b-73633133180b)  
  
 [sp_addremotelogin (Transact-SQL)](assetId:///71b7cd36-a17d-4b12-b102-10aeb0f9268b)  
  
 [sp_addsubscriber (Transact-SQL)](assetId:///b8a584ea-2a26-4936-965b-b84f026e39c0)  
  
 [sp_approlepassword (Transact-SQL)](assetId:///7967dc0b-bee2-4c63-b8e9-1c3ce2f5db2a)  
  
 [sp_changedistpublisher (Transact-SQL)](assetId:///7ef5c89d-faaa-4f8e-aef7-00649ebc8bc9)  
  
 [sp_changesubscriber (Transact-SQL)](assetId:///d453c451-e957-490f-b968-5e03aeddaf10)  
  
 [sp_dsninfo (Transact-SQL)](assetId:///34648615-814b-42bc-95a3-50e86b42ec4d)  
  
 [sp_helpsubscription_properties (Transact-SQL)](assetId:///7a76a645-97eb-47ac-b3ea-e2d75012cbed)  
  
 [sp_link_publication (Transact-SQL)](assetId:///1945ed24-f9f1-4af6-94ca-16d8e864706e)  
  
 [sp_password (Transact-SQL)](assetId:///0ecbec81-e637-44a9-a61e-11bf060ef084)  
  
 [sp_setapprole (Transact-SQL)](assetId:///cf0901c0-5f90-42d4-9d5b-8772c904062d)