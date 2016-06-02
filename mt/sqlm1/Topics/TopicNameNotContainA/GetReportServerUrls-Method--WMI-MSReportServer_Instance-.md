---
title: GetReportServerUrls Method (WMI MSReportServer_Instance)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4865e32c-0114-465a-be8c-be223a7bc09e
---
# GetReportServerUrls Method (WMI MSReportServer_Instance)
  Returns a list of URLs users can use to access the report server and report manager.  
  
## Syntax  
  
```vb#  
Public Sub GetReportServerUrls (ByRef ApplicationName() As String, ByRef URLs()_  
    As String, ByRef Length As Int32, ByRef HRESULT As Int32)  
```  
  
```c#  
public void GetReportServerUrls(out string[] applicationName,   
    out string[] URLs, out int length, out int HRESULT);  
```  
  
## Parameters  
 *ApplicationName\[\]*  
 An array that contains the applications that are installed. Values are either **ReportServerWebService** or **ReportManager**.  
  
 *URLs\[\]*  
 An array that contains the successfully registered Urls.  
  
 *Length*  
 An integer value that contains the length of the arrays returned.  
  
 *HRESULT*  
 A value that indicates success or an error code.  
  
## Return Values  
  
## Remarks  
 Methods exposed by WMI management objects are called through the InvokeMethod function. For more information, please see "Executing Methods on Management Objects" in the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] .NET Framework WMI documentation.  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspc](../../Token\Other/ssRSWMInmspc_md.md)]  
  
## See Also  
 [MSReportServer_ConfigurationSetting Members](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Members.md)  
  
  