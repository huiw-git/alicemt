---
title: Discover Server State Events Data Columns
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fbacb187-a4d1-4aa4-be3b-3ddd175f9e19
---
# Discover Server State Events Data Columns
  The Discover Server State event category has the following event classes:  
  
|**Event ID**|**Event Name**|**Event Description**|  
|------------------|--------------------|---------------------------|  
|33|Server State Discover Begin|Start of Server State Discover.|  
|34|Server State Discover Data|Contents of the Server State Discover Response.|  
|35|Server State Discover End|End of Server State Discover.|  
  
 The following tables list the data columns for each of these event classes.  
  
## Server State Discover Begin Class—Data Columns  
  
|||||  
|-|-|-|-|  
|**Column Name**|**Column Id**|**Column Type**|**Column Description**|  
|EventClass|0|1|Event Class is used to categorize events.|  
|EventSubclass|1|1|Event Subclass provides additional information about each event class:<br /><br /> 1: **DISCOVER\_CONNECTIONS**<br /><br /> 2: **DISCOVER\_SESSIONS**<br /><br /> 3: **DISCOVER\_TRANSACTIONS**<br /><br /> 6: **DISCOVER\_DB\_CONNECTIONS**<br /><br /> 7: **DISCOVER\_JOBS**<br /><br /> 8: **DISCOVER\_LOCKS**<br /><br /> 12: **DISCOVER\_PERFORMANCE\_COUNTERS**<br /><br /> 13: **DISCOVER\_MEMORYUSAGE**<br /><br /> 14: **DISCOVER\_JOB\_PROGRESS**<br /><br /> 15: **DISCOVER\_MEMORYGRANT**|  
|CurrentTime|2|5|Contains the current time of the server state discover event, when available. For filtering, expected formats are 'YYYY\-MM\-DD' and 'YYYY\-MM\-DD HH:MM:SS'.|  
|StartTime|3|5|Contains the time at which the event started, when available. For filtering, expected formats are 'YYYY\-MM\-DD' and 'YYYY\-MM\-DD HH:MM:SS'.|  
|ConnectionID|25|1|Contains the unique connection ID associated with the server state discover event.|  
|NTUserName|32|8|Contains the Windows user account associated with the server state discover event.|  
|NTDomainName|33|8|Contains the Windows domain account associated with the server state discover event.|  
|ClientProcessID|36|1|Contains the process ID of the client application that created the connection to the server.|  
|ApplicationName|37|8|Contains the name of the client application that created the connection to the server. This column is populated with the values passed by the application rather than the displayed name of the program.|  
|SessionID|39|8|Contains the session ID associated with the server state discover event.|  
|NTCanonicalUserName|40|8|Contains the Windows user name associated with the server state discover event. The user name is in canonical form. For example, engineering.microsoft.com\/software\/user.|  
|SPID|41|1|Contains the server process ID \(SPID\) that uniquely identifies the user session associated with the server state discover event. The SPID directly corresponds to the session GUID used by XMLA.|  
|TextData|42|9|Contains the text data associated with the event.|  
|ServerName|43|8|Contains the name of the instance of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] on which the server state discover event occurred.|  
|RequestProperties|45|9|Contains the properties of the current XMLA request.|  
  
## Server State Discover Data Class—Data Columns  
  
|||||  
|-|-|-|-|  
|**Column Name**|**Column Id**|**Column Type**|**Column Description**|  
|EventClass|0|1|Event Class is used to categorize events.|  
|EventSubclass|1|1|Event Subclass provides additional information about each event class:<br /><br /> 1: **DISCOVER\_CONNECTIONS**<br /><br /> 2: **DISCOVER\_SESSIONS**<br /><br /> 3: **DISCOVER\_TRANSACTIONS**<br /><br /> 6: **DISCOVER\_DB\_CONNECTIONS**<br /><br /> 7: **DISCOVER\_JOBS**<br /><br /> 8: **DISCOVER\_LOCKS**<br /><br /> 12: **DISCOVER\_PERFORMANCE\_COUNTERS**<br /><br /> 13: **DISCOVER\_MEMORYUSAGE**<br /><br /> 14: **DISCOVER\_JOB\_PROGRESS**<br /><br /> 15: **DISCOVER\_MEMORYGRANT**|  
|CurrentTime|2|5|Contains the current time of the server state discover event, when available. For filtering, expected formats are 'YYYY\-MM\-DD' and 'YYYY\-MM\-DD HH:MM:SS'.|  
|StartTime|3|5|Contains the time at which the event started, when available. For filtering, expected formats are 'YYYY\-MM\-DD' and 'YYYY\-MM\-DD HH:MM:SS'.|  
|ConnectionID|25|1|Contains the unique connection ID associated with the server state discover event.|  
|SessionID|39|8|Contains the session ID associated with the server state discover event.|  
|SPID|41|1|Contains the server process ID \(SPID\) that uniquely identifies the user session associated with the server state discover event. The SPID directly corresponds to the session GUID used by XMLA.|  
|TextData|42|9|Contains the text data associated with server response to the discover request.|  
|ServerName|43|8|Contains the name of the instance of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] on which the server state discover event occurred.|  
  
## Server State Discover End Class—Data Columns  
  
|||||  
|-|-|-|-|  
|**Column Name**|**Column Id**|**Column Type**|**Column Description**|  
|EventClass|0|1|Event Class is used to categorize events.|  
|EventSubclass|1|1|Event Subclass provides additional information about each event class:<br /><br /> 1: **DISCOVER\_CONNECTIONS**<br /><br /> 2: **DISCOVER\_SESSIONS**<br /><br /> 3: **DISCOVER\_TRANSACTIONS**<br /><br /> 6: **DISCOVER\_DB\_CONNECTIONS**<br /><br /> 7: **DISCOVER\_JOBS**<br /><br /> 8: **DISCOVER\_LOCKS**<br /><br /> 12: **DISCOVER\_PERFORMANCE\_COUNTERS**<br /><br /> 13: **DISCOVER\_MEMORYUSAGE**<br /><br /> 14: **DISCOVER\_JOB\_PROGRESS**<br /><br /> 15: **DISCOVER\_MEMORYGRANT**|  
|CurrentTime|2|5|Contains the current time of the server state discover event, when available. For filtering, expected formats are 'YYYY\-MM\-DD' and 'YYYY\-MM\-DD HH:MM:SS'.|  
|StartTime|3|5|Contains the time at which the event started, when available. For filtering, expected formats are 'YYYY\-MM\-DD' and 'YYYY\-MM\-DD HH:MM:SS'.|  
|EndTime|4|5|Contains the time at which the event ended. This column is not populated for starting event classes, such as SQL:BatchStarting or SP:Starting. For filtering, expected formats are 'YYYY\-MM\-DD' and 'YYYY\-MM\-DD HH:MM:SS'.|  
|Duration|5|2|Contains the amount of time \(in milliseconds\) taken by the event.|  
|CPUTime|6|2|Contains the amount of CPU time \(in milliseconds\) used by the server state discover event.|  
|ConnectionID|25|1|Contains the unique connection ID associated with the server state discover event.|  
|NTUserName|32|8|Contains the Windows user account associated with the server state discover event.|  
|NTDomainName|33|8|Contains the Windows domain account associated with the server state discover event.|  
|ClientProcessID|36|1|Contains the process ID of the client application that initiated the XMLA request.|  
|ApplicationName|37|8|Contains the name of the client application that created the connection to the server. This column is populated with the values passed by the application rather than the displayed name of the program.|  
|SessionID|39|8|Contains the Windows domain account associated with the server state discover event.|  
|NTCanonicalUserName|40|8|Contains the Windows user name associated with the server state discover event. The user name is in canonical form. For example, engineering.microsoft.com\/software\/user.|  
|SPID|41|1|Contains the server process ID \(SPID\) that uniquely identifies the user session associated with the server state discover event. The SPID directly corresponds to the session GUID used by XMLA.|  
|TextData|42|9|Contains the text data associated with server response to the discover request.|  
|ServerName|43|8|Contains the name of the instance of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] on which the server state discover event occurred.|  
  
## See Also  
 [Discover Server State Event Category](../../Topics\TopicNameNotContainA/Discover-Server-State-Event-Category.md)  
  
  