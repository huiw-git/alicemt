---
title: RemoveURL Method (WMI MSReportServer_ConfigurationSetting)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3d98bd97-e152-48ce-ab1c-bd2c4f8b7fe9
---
# RemoveURL Method (WMI MSReportServer_ConfigurationSetting)
  Removes a URL reserved for the report server. If there are multiple URLs that need to be removed, this must be done one by one calling this API.  
  
## Syntax  
  
```vb#  
Public Sub RemoveURL(ByVal Application As String, _  
    ByVal UrlString As String, ByVal Lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```c#  
public void RemoveURL(string Application, string UrlString, int Lcid,   
    out string Error, out int HRESULT);  
```  
  
## Parameters  
 *Application*  
 The name of application for which to remove the reservation.  
  
 *URLString*  
 The URL for the reservation.  
  
 *lcid*  
 The locale to use for the error messages returned.  
  
 *Error*  
 [out] The description of the error that occurred.  
  
 *HRESULT*  
 [out] Value indicating whether the call succeeded or failed.  
  
## Return Value  
 Returns an *HRESULT* indicating success or failure of the method call. A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.  
  
## Remarks  
 *UrlString* does not include the Virtual Directory name – the [SetVirtualDirectory Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../Topics/TopicNameNotContainA/SetVirtualDirectory-Method--WMI-MSReportServer_ConfigurationSetting-.md) method is provided for that purpose.  
  
 Before calling the [ReserveURL](../../Topics/TopicNameNotContainA/ReserveURL-Method--WMI-MSReportServer_ConfigurationSetting-.md) method, you must supply a value for the VirtualDirectory configuration property for the *Application* parameter. Use the [SetVirtualDirectory Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../Topics/TopicNameNotContainA/SetVirtualDirectory-Method--WMI-MSReportServer_ConfigurationSetting-.md) method to set the VirtualDirectory property.  
  
 If an SSL Certificate was provisioned by [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] and no other URLs need it, it is removed.  
  
 This method causes all non-configuration app domains to hard recycle and stop during this operation; app domains are restarted after this operation complete.  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Topics/TopicNameNotContainA/includes/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [MSReportServer_ConfigurationSetting Members](../../Topics/TopicNameNotContainA/MSReportServer_ConfigurationSetting-Members.md)  
  
  