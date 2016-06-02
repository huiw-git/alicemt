---
title: GenerateDatabaseCreationScript Method (WMI MSReportServer_ConfigurationSetting)
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
  - GenerateDatabaseCreationScript (WMI MSReportServer_ConfigurationSetting Class)
apilocation: 
  - reportingservices.mof
apitype: MOFDef
ms.assetid: 25232dc7-00fe-4cd1-8a1c-7e36d552de00
---
# GenerateDatabaseCreationScript Method (WMI MSReportServer_ConfigurationSetting)
  Generates a SQL Script that can be used to create a report server database.  
  
## Syntax  
  
```vb#  
Public Sub GenerateDatabaseCreationScript(ByVal DatabaseName As String, _  
    ByVal Lcid As Int32, ByVal IsSharePointMode As Boolean, ByRef Script As String, _  
    ByRef HRESULT As Int32)  
```  
  
```c#  
public void GenerateDatabaseCreationScript(string DatabaseName, Int32 Lcid,   
    Boolean IsSharePointMode, out string Script, out Int32 HRESULT);  
```  
  
## Parameters  
 *Databasename*  
 A string containing the name of the report server database to create.  
  
 *Lcid*  
 Value used for localization of role names.  
  
 *IsSharePointMode*  
 Indicates whether to create database in native mode or SharePoint mode.  
  
> [!IMPORTANT]  
>  Beginning in [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], *IsSharePointMode*\=**True** is not supported because in SharePoint mode, [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] is a SharePoint shared service and is not controlled by the WMI provider. You should always set this parameter to **False**.  
  
 *Script*  
 \[out\] A string containing the generated SQL script.  
  
 *HRESULT*  
 \[out\] Value indicating whether the call succeeded or failed.  
  
## Return Value  
 Returns an *HRESULT* indicating success or failure of the method call. A value of 0 indicates that the method call was successful. A non\-zero value indicates that an error has occurred.  
  
## Remarks  
 This method generates an SQL script that creates report server databases for the version of the report server currently connected to.  
  
 The value supplied in the *DatabaseName* parameter must conform to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database naming conventions.  
  
 The method does not check the existence of the database when generating the script.  
  
 This method does not check for the existence of the report server database when generating the script.  
  
 The generated script supports [!INCLUDE[ssVersion2000](../../Token\Other/ssVersion2000_md.md)], [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] 2005, and [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)].  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Token\Other/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [MSReportServer_ConfigurationSetting Members](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Members.md)  
  
  