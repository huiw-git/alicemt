---
title: RSReportDesigner Configuration File
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fdcc9c58-3bad-45b3-ba8e-c7816d64f14c
---
# RSReportDesigner Configuration File
  The RSReportDesigner.config file stores settings about the rendering and data processing extensions available to Report Designer. Data processing extension information is stored in the **Data** element. Rendering extension information is stored in the **Render** element. The **Designer** element enumerates the query builders that are used in Report Designer.  
  
 Report Designer uses embedded report server functionality to preview reports. Server\-related settings can be specified to support local server\-side processing for preview operations. For more information about report server configuration settings, see [RsReportServer.config Configuration File](../../Topics\TopicNameNotContainA/RsReportServer.config-Configuration-File.md).  
  
## File Location  
 This file is located in the \\Program Files\\Microsoft Visual Studio 8\\Common7\\IDE\\PrivateAssemblies.  
  
## Editing Guidelines  
 Do not modify the settings in this file unless you are deploying or removing a custom extension, disabling caching during preview, or registering a new data processing extension after a Service Pack upgrade.  
  
 Specific instructions for editing configuration files are available if you are customizing rendering extension settings. For more information, see [Customize Rendering Extension Parameters in RSReportServer.Config](../../Topics\TopicNameNotContainA/Customize-Rendering-Extension-Parameters-in-RSReportServer.Config.md).  
  
 For general instructions on how to edit configuration files, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](../Topic/Modify%20a%20Reporting%20Services%20Configuration%20File%20\(RSreportserver.config\).md).  
  
## Example Configuration File  
 The following example illustrates the format of the RSReportDesigner.config file.  
  
```  
<Configuration>  
  <Add Key="SecureConnectionLevel" Value="0" />  
  <Add Key="InstanceName" Value="Microsoft.ReportingServices.PreviewServer" />  
  <Add Key="SessionCookies" Value="true" />  
  <Add Key="SessionTimeoutMinutes" Value="3" />  
  <Add Key="PolicyLevel" Value="rspreviewpolicy.config" />  
  <Add Key="CacheDataForPreview" Value="true" />  
  <Extensions>  
    <Render> . . . </Render>  
    <Data> . . . </Data>  
    <Designer> . . . </Designer>  
```  
  
## Configuration Settings  
  
|Setting|Description|  
|-------------|-----------------|  
|**SecureConnectionLevel**|Specifies the degree of security of the Web service connection. Valid values range from 0 through 3, where 0 is least secure. For more information, see [Using Secure Web Service Methods](../Topic/Using%20Secure%20Web%20Service%20Methods.md).|  
|**InstanceName**|An identifier for the preview server. Do not modify this value.|  
|**SessionCookies**|Specifies whether the report server uses browser cookies to maintain session information. Valid values include **true** and **false**. The default is **true**. If you set this value to false, session data is stored in the **reportservertempdb** database.|  
|**SessionTimeoutMinutes**|Specifies the period for which a session cookie is valid. The default is 3 minutes.|  
|**PolicyLevel**|Specifies the security policy configuration file. The valid value is Rspreviewpolicy.config. For more information, see [Using Reporting Services Security Policy Files](../Topic/Using%20Reporting%20Services%20Security%20Policy%20Files.md).|  
|**CacheDataForPreview**|When set to **True**, the Report Designer stores data in a cache file on the local computer. Valid values are **True** \(default\) and **False**. For more information, see [Previewing Reports](../../Topics\TopicNameNotContainA/Previewing-Reports.md).|  
|**Render**|Enumerates the rendering extensions that are available to Report Designer for preview purposes. The set of rendering extensions that are used for preview should be identical to those installed with the report server.<br /><br /> **Name** specifies the rendering extension. If you are invoking a rendering extension through code, use this value to call a specific extension.<br /><br /> **Type** specifies the fully qualified class name of the extension class, plus the library name, comma separated.<br /><br /> **Visible** specifies whether the name appears in any user interface. This value can be **True** \(default\) or **False**. If **True**, it appears in user interfaces.|  
|**Data**|Enumerates the data processing extensions that are available to Report Designer for the purpose of connecting to data sources that provide data to reports. The set of data processing extensions used in Report Designer may be identical to those installed with the report server. If you are adding or removing custom extensions, see [Deploying a Data Processing Extension](../Topic/Deploying%20a%20Data%20Processing%20Extension.md).<br /><br /> **Name** specifies the data processing extension.<br /><br /> **Type** specifies the fully qualified class name of the extension class, plus the library name, comma separated.|  
|**Designer**|Enumerates the query builders that are available to Report Designer. Query builders provide a user interface for constructing queries that retrieve data used in reports. Query builders may vary for different data processing extensions. By default, Reporting Services provides one visual data tool user interface for all data processing extensions that are included in the product. However, if you are building or using third\-party data processing extensions, other query builder interfaces may apply.|  
|**PreviewProcessingServiceStartupTimeoutSeconds**|Specifies the period to wait for the preview processing service to start up before showing an error message. The default is 15 seconds.|  
  
## See Also  
 [Reporting Services Configuration Files](../../Topics\TopicNameNotContainA/Reporting-Services-Configuration-Files.md)   
 [Query Design Tools &#40;SSRS&#41;](../Topic/Query%20Design%20Tools%20\(SSRS\).md)  
  
  