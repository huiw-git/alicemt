---
title: ListReservedURLs Method (WMI MSReportServer_ConfigurationSetting)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 32335af1-5eae-4420-a0ef-b1e8a3267166
---
# ListReservedURLs Method (WMI MSReportServer_ConfigurationSetting)
  Lists URLs reserved for all applications on the report server.  
  
## Syntax  
  
```vb#  
Public Sub ListReservedUrls(ByRef Application() as String, ByRef UrlString() as String, _  
    ByRef Account() as String, ByRef AccountSID() as String, _  
    ByRef length() as Int32, ByRef HRESULT as Int32)  
```  
  
```c#  
public void ListReservedUrls(out string[] Application, out string[] UrlString,  
        out string[] Account, out string[] AccountSID,  
        out int[] Length, out int[] HRESULT);  
```  
  
## Parameters  
 *Application\[\]*  
 \[out\] The applications that have URL reservations.  
  
 *UrlString\[\]*  
 \[out\] The URLs that are reserved.  
  
 *Account\[\]*  
 \[out\] The account names associated with the account for the URL reservations.  
  
 *AccountSID\[\]*  
 \[out\] The account SIDs associated with the account for the URL reservations.  
  
 *Length*  
 \[out\] The length of the arrays returned by the method.  
  
 *HRESULT*  
 \[out\] Value indicating whether the call succeeded or failed.  
  
## Return Value  
 Returns an *HRESULT* indicating success or failure of the method call. A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.  
  
## Remarks  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Token\Other/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [MSReportServer_ConfigurationSetting Members](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Members.md)  
  
  