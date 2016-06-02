---
title: GenerateDatabaseUpgradeScript Method (WMI MSReportServer_ConfigurationSetting)
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
  - GenerateDatabaseUpgradeScript (WMI MSReportServer_ConfigurationSetting Class)
apilocation: 
  - reportingservices.mof
apitype: MOFDef
ms.assetid: 88534e8e-2877-41cd-b5c2-b1d33a0fd203
---
# GenerateDatabaseUpgradeScript Method (WMI MSReportServer_ConfigurationSetting)
  Generates a script that can be used to upgrade the report server database to the [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] schema.  
  
## Syntax  
  
```vb#  
Public Sub GenerateDatabaseUpgradeScript(DatabaseName as String, _  
    ServerVersion as String, ByRef Script as String, _  
    ByRef HRESULT as Int32)  
```  
  
```c#  
public void GenerateDatabaseUpgradeScript (string DatabaseName,   
    string ServerVersion, out string Script,   
    out Int32 HRESULT);  
```  
  
## Parameters  
 *Databasename*  
 A string containing the name of the report server database to upgrade.  
  
 *ServerVersion*  
 A string containing the version of the report server.  
  
 *Script*  
 \[out\] A string containing the generated SQL script.  
  
 *HRESULT*  
 \[out\] Value indicating whether the call succeeded or failed.  
  
## Return Value  
 Returns an *HRESULT* indicating success or failure of the method call. A value of 0 indicates that the method call was successful. A non\-zero value indicates that an error has occurred.  
  
## Remarks  
 The generated script supports [!INCLUDE[ssVersion2000](../../Token\Other/ssVersion2000_md.md)], [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)], and [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)].  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Token\Other/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [MSReportServer_ConfigurationSetting Members](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Members.md)  
  
  