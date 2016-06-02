---
title: ListIPAddresses Method (WMI MSReportServer_ConfigurationSetting)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7e7cf182-fba0-4604-a474-098461e23e9d
---
# ListIPAddresses Method (WMI MSReportServer_ConfigurationSetting)
  Lists the IP addresses for the report server computer.  
  
## Syntax  
  
```vb#  
Public Sub ListIPAddresses (ByRef IPAddress() as String, _  
    ByRef IPVersion()as String, ByRef IsDhcpEnabled () as Boolean, _   
    ByRef Length as Int32, ByRef HRESULT as Int32)  
```  
  
```c#  
public void ListIPAddresses (out string[] IPAddress,   
    out string[] IPVersion, out bool[] isDhcpEnabled, out int length,   
    out int HRESULT);  
```  
  
## Parameters  
 *IPAddress\[\]*  
 \[out\] The list of IP address for the computer.  
  
 *IPVersion\[\]*  
 \[out\] The version for the IP addresses.  
  
 *IsDhcpEnabled\[\]*  
 \[out\] Indicates whether the IP addresses are DHCP enabled.  
  
 *Length*  
 \[out\] The length of the array returned by the method.  
  
 *HRESULT*  
 \[out\] Value indicating whether the call succeeded or failed.  
  
## Return Value  
 Returns an *HRESULT* indicating success or failure of the method call. A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.  
  
## Remarks  
 *IPVersion* strings are V4, V6.  
  
 If *IsDhcpEnabled* is **True**, the *IPAddress* is dynamic. It should not be used for SSL bindings.  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Token\Other/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [MSReportServer_ConfigurationSetting Members](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Members.md)  
  
  