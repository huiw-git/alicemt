---
title: DatabaseQueryTimeout Property (WMI MSReportServer_ConfigurationSetting)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - DatabaseQueryTimeout Property
apilocation: 
  - reportingservices.mof
apitype: MOFDef
ms.assetid: 96faed97-9799-4bbf-a66f-fdd532d3eace
---
# DatabaseQueryTimeout Property (WMI MSReportServer_ConfigurationSetting)
  Specifies the number of seconds that must elapse before the report server assumes the command failed or took too much time to perform. The report server is timing the querying against the SQL catalog, not a data source for the report. Read\/write.  
  
## Syntax  
  
```vb#  
Public Dim DatabaseQueryTimeout As UInt32  
```  
  
```c#  
public UInt32 DatabaseQueryTimeout;  
```  
  
## Property Values  
 A 32\-bit unsigned **integer** object that represents the number of seconds that the query is allowed to run.  
  
## Example Code  
 [MSReportServer_ConfigurationSetting Class](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Class.md)  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Token\Other/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [MSReportServer_ConfigurationSetting Members](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Members.md)  
  
  