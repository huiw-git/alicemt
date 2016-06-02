---
title: Discover Events Data Columns
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 10ec598e-5b51-4767-b4f7-42e261d96a40
---
# Discover Events Data Columns
  The Discover Events category has the following event classes:  
  
-   Discover Begin class  
  
-   Discover End class  
  
 The following tables list the data columns for each of these event classes.  
  
## Discover Begin Class—Data Columns  
  
|||||  
|-|-|-|-|  
|**Column Name**|**Column Id**|**Column Type**|**Column Description**|  
|EventClass|0|1|Event Class is used to categorize events.|  
|EventSubclass|1|1|Event Subclass provides additional information about each event class.  The following are valid **Sub Class Id**\/**Sub Class Name** value pairs:<br /><br /> 0: DBSCHEMA\_CATALOGS<br /><br /> 1: DBSCHEMA\_TABLES<br /><br /> 2: DBSCHEMA\_COLUMNS<br /><br /> 3: DBSCHEMA\_PROVIDER\_TYPES<br /><br /> 4: MDSCHEMA\_CUBES<br /><br /> 5: MDSCHEMA\_DIMENSIONS<br /><br /> 6: MDSCHEMA\_HIERARCHIES<br /><br /> 7: MDSCHEMA\_LEVELS<br /><br /> 8: MDSCHEMA\_MEASURES<br /><br /> 9: MDSCHEMA\_PROPERTIES<br /><br /> 10: MDSCHEMA\_MEMBERS<br /><br /> 11: MDSCHEMA\_FUNCTIONS<br /><br /> 12: MDSCHEMA\_ACTIONS<br /><br /> 13: MDSCHEMA\_SETS<br /><br /> 14: DISCOVER\_INSTANCES<br /><br /> 15: MDSCHEMA\_KPIS<br /><br /> 16: MDSCHEMA\_MEASUREGROUPS<br /><br /> 17: MDSCHEMA\_COMMANDS<br /><br /> 18: DMSCHEMA\_MINING\_SERVICES<br /><br /> 19: DMSCHEMA\_MINING\_SERVICE\_PARAMETERS<br /><br /> 20: DMSCHEMA\_MINING\_FUNCTIONS<br /><br /> 21: DMSCHEMA\_MINING\_MODEL\_CONTENT<br /><br /> 22: DMSCHEMA\_MINING\_MODEL\_XML<br /><br /> 23: DMSCHEMA\_MINING\_MODELS<br /><br /> 24: DMSCHEMA\_MINING\_COLUMNS<br /><br /> 25: DISCOVER\_DATASOURCES<br /><br /> 26: DISCOVER\_PROPERTIES<br /><br /> 27: DISCOVER\_SCHEMA\_ROWSETS<br /><br /> 28: DISCOVER\_ENUMERATORS<br /><br /> 29: DISCOVER\_KEYWORDS<br /><br /> 30: DISCOVER\_LITERALS<br /><br /> 31: DISCOVER\_XML\_METADATA<br /><br /> 32: DISCOVER\_TRACES<br /><br /> 33: DISCOVER\_TRACE\_DEFINITION\_PROVIDERINFO<br /><br /> 34: DISCOVER\_TRACE\_COLUMNS<br /><br /> 35: DISCOVER\_TRACE\_EVENT\_CATEGORIES<br /><br /> 36: DMSCHEMA\_MINING\_STRUCTURES<br /><br /> 37: DMSCHEMA\_MINING\_STRUCTURE\_COLUMNS<br /><br /> 38: DISCOVER\_MASTER\_KEY<br /><br /> 39: MDSCHEMA\_INPUT\_DATASOURCES<br /><br /> 40: DISCOVER\_LOCATIONS<br /><br /> 41: DISCOVER\_PARTITION\_DIMENSION\_STAT<br /><br /> 42: DISCOVER\_PARTITION\_STAT<br /><br /> 43: DISCOVER\_DIMENSION\_STAT<br /><br /> 44: MDSCHEMA\_MEASUREGROUP\_DIMENSIONS<br /><br /> 49: DISCOVER\_XEVENT\_TRACE\_DEFINITION|  
|CurrentTime|2|5|Time at which the event started, when available. For filtering, expected formats are 'YYYY\-MM\-DD' and 'YYYY\-MM\-DD HH:MM:SS'.|  
|StartTime|3|5|Time at which the event started, when available. For filtering, expected formats are 'YYYY\-MM\-DD' and 'YYYY\-MM\-DD HH:MM:SS'.|  
|ConnectionID|25|1|Contains the unique connection ID associated with the discover event.|  
|DatabaseName|28|8|Name of the database in which the statement of the user is running.|  
|NTUserName|32|8|Contains the Windows user name associated with the discover event. The user name is in canonical form. For example, engineering.microsoft.com\/software\/user.|  
|NTDomainName|33|8|Contains the Windows domain associated with the discover event.|  
|ClientProcessID|36|1|Contains the process ID of the client application.|  
|ApplicationName|37|8|Name of the client application that created the connection to the server. This column is populated with the values passed by the application rather than the displayed name of the program.|  
|SessionID|39|8|Contains the session ID associated with the discover event.|  
|NTCanonicalUserName|40|8|Contains the Windows user name associated with the discover event. The user name is in canonical form. For example, engineering.microsoft.com\/software\/user.|  
|SPID|41|1|Contains the server process ID \(SPID\) that uniquely identifies the user session associated with the discover event. The SPID directly corresponds to the session GUID used by XMLA.|  
|TextData|42|9|Contains the text data associated with the event.|  
|ServerName|43|8|Contains the name of the instance of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] on which the discover event occurred.|  
|RequestProperties|45|9|Contains the XML for Analysis \(XMLA\) request properties associated with the discover event.|  
  
## Discover End Class—Data Columns  
  
|||||  
|-|-|-|-|  
|**Column Name**|**Column Id**|**Column Type**|**Column Description**|  
|EventClass|0|1|Contains the event class; this is used to categorize events.|  
|EventSubclass|1|1|Event Subclass provides additional information about each event class. The following are valid **Sub Class Id**\/**Sub Class Name** value pairs:<br /><br /> 0: DBSCHEMA\_CATALOGS<br /><br /> 1: DBSCHEMA\_TABLES<br /><br /> 2: DBSCHEMA\_COLUMNS<br /><br /> 3: DBSCHEMA\_PROVIDER\_TYPES<br /><br /> 4: MDSCHEMA\_CUBES<br /><br /> 5: MDSCHEMA\_DIMENSIONS<br /><br /> 6: MDSCHEMA\_HIERARCHIES<br /><br /> 7: MDSCHEMA\_LEVELS<br /><br /> 8: MDSCHEMA\_MEASURES<br /><br /> 9: MDSCHEMA\_PROPERTIES<br /><br /> 10: MDSCHEMA\_MEMBERS<br /><br /> 11: MDSCHEMA\_FUNCTIONS<br /><br /> 12: MDSCHEMA\_ACTIONS<br /><br /> 13: MDSCHEMA\_SETS<br /><br /> 14: DISCOVER\_INSTANCES<br /><br /> 15: MDSCHEMA\_KPIS<br /><br /> 16: MDSCHEMA\_MEASUREGROUPS<br /><br /> 17: MDSCHEMA\_COMMANDS<br /><br /> 18: DMSCHEMA\_MINING\_SERVICES<br /><br /> 19: DMSCHEMA\_MINING\_SERVICE\_PARAMETERS<br /><br /> 20: DMSCHEMA\_MINING\_FUNCTIONS<br /><br /> 21: DMSCHEMA\_MINING\_MODEL\_CONTENT<br /><br /> 22: DMSCHEMA\_MINING\_MODEL\_XML<br /><br /> 23: DMSCHEMA\_MINING\_MODELS<br /><br /> 24: DMSCHEMA\_MINING\_COLUMNS<br /><br /> 25: DISCOVER\_DATASOURCES<br /><br /> 26: DISCOVER\_PROPERTIES<br /><br /> 27: DISCOVER\_SCHEMA\_ROWSETS<br /><br /> 28: DISCOVER\_ENUMERATORS<br /><br /> 29: DISCOVER\_KEYWORDS<br /><br /> 30: DISCOVER\_LITERALS<br /><br /> 31: DISCOVER\_XML\_METADATA<br /><br /> 32: DISCOVER\_TRACES<br /><br /> 33: DISCOVER\_TRACE\_DEFINITION\_PROVIDERINFO<br /><br /> 34: DISCOVER\_TRACE\_COLUMNS<br /><br /> 35: DISCOVER\_TRACE\_EVENT\_CATEGORIES<br /><br /> 36: DMSCHEMA\_MINING\_STRUCTURES<br /><br /> 37: DMSCHEMA\_MINING\_STRUCTURE\_COLUMNS<br /><br /> 38: DISCOVER\_MASTER\_KEY<br /><br /> 39: MDSCHEMA\_INPUT\_DATASOURCES<br /><br /> 40: DISCOVER\_LOCATIONS<br /><br /> 41: DISCOVER\_PARTITION\_DIMENSION\_STAT<br /><br /> 42: DISCOVER\_PARTITION\_STAT<br /><br /> 43: DISCOVER\_DIMENSION\_STAT<br /><br /> 44: MDSCHEMA\_MEASUREGROUP\_DIMENSIONS<br /><br /> 49: DISCOVER\_XEVENT\_TRACE\_DEFINITION|  
|CurrentTime|2|5|Contains the current time of the discover event, when available. For filtering, expected formats are 'YYYY\-MM\-DD' and 'YYYY\-MM\-DD HH:MM:SS'.|  
|StartTime|3|5|Contains the time \(if available\) at which the discover end event started.. For filtering, expected formats are 'YYYY\-MM\-DD' and 'YYYY\-MM\-DD HH:MM:SS'.|  
|EndTime|4|5|Contains the time at which the event ended. This column is not populated for starting event classes, such as SQL:BatchStarting or SP:Starting. For filtering, expected formats are 'YYYY\-MM\-DD' and 'YYYY\-MM\-DD HH:MM:SS'.|  
|Duration|5|2|Contains the approximate amount of time \(milliseconds\) taken by the discover event.|  
|CPUTime|6|2|Contains the amount of CPU time \(in milliseconds\) used by the event.|  
|Severity|22|1|Contains the severity level of an exception.|  
|Success|23|1|Contains the success or failure of the discover event. Values are:<br /><br /> 0 \= Failure<br /><br /> 1 \= Success|  
|Error|24|1|Contains the error number of any error associated the discover event.|  
|ConnectionID|25|1|Contains the unique connection ID associated with the discover event.|  
|DatabaseName|28|8|Contains the name of the database in which the discover event occurred.|  
|NTUserName|32|8|Contains the Windows user name associated with the object permission event.|  
|NTDomainName|33|8|Contains the Windows domain account associated with the discover event.|  
|ClientProcessID|36|1|Contains the client process ID of the application that initiated the event.|  
|ApplicationName|37|8|Contains the name of the client application that created the connection to the server. This column is populated with the values passed by the application rather than the displayed name of the program.|  
|SessionID|39|8|Contains the session ID associated with the discover event.|  
|NTCanonicalUserName|40|8|Contains the Windows user name associated with the object permission event. The user name is in canonical form. For example, engineering.microsoft.com\/software\/user.|  
|SPID|41|1|Contains the server process ID \(SPID\) that uniquely identifies the user session associated with the discover end event. The SPID directly corresponds to the session GUID used by XMLA.|  
|TextData|42|9|Contains the text data associated with the event.|  
|ServerName|43|8|Contains the name of the instance of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] on which the discover event occurred.|  
|RequestProperties|45|9|Contains the properties in the XMLA request.|  
  
## See Also  
 [Discover Events Event Category](../../Topics\TopicNameNotContainA/Discover-Events-Event-Category.md)  
  
  