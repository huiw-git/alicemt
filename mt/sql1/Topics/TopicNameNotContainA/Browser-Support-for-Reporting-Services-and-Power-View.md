---
title: "Browser Support for Reporting Services and Power View"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 2016-05-25
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 48a75bbb-0029-4c43-891d-dc8f4fc0ebe1
caps.latest.revision: 121
caps.handback.revision: 0
manager: mblythe
---
# Browser Support for Reporting Services and Power View
This topic summarizes  the browser versions supported for managing and viewing [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)][!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] reports and includes information on browser support for the Report Viewer controls in Visual Studio.  
  
 **Applies to:** [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] SharePoint mode  
  
##  <a name="bkmk_top"></a> In this Topic  
  
-   [Browser Requirements for Viewing Reports](#bkmk_reportviewer)  
  
-   [Browser Authentication Requirements](#bkmk_authentication)  
  
-   [Browser Support for ReportViewer Web Server Controls in Visual Studio](#bkmk_controls)  
  
-   [Power View Browser Support](#bkmk_powerview)  
  
##  <a name="bkmk_reportviewer"></a> Browser Requirements for Viewing Reports  
 The following is the current list of browsers and features supported with the report viewer. The report viewer supports viewing reports from [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] Report Manager and SharePoint libraries.  
  
|**Browser**|**Windows 10**|**Windows 8 and 8.1**|**Windows 7**|**Windows Server 2012 and 2012 R2**|**Windows Server 2008 R2**|**Mac OS X 10.7 – 10.10**|**iOS 6 -9 for iPad**|  
|-----------------|--------------------|---------------------------|-------------------|-----------------------------------------|--------------------------------|-------------------------------|----------------------------|  
|**Microsoft Edge**  (+)|Supported|-|-|-|-|-|-|  
|**Microsoft Internet Explorer 11  & 10**|Supported|Supported|Supported|Supported|Supported|-|-|  
|**Google Chrome** (+)|Supported|Supported|Supported|Supported|Supported|-|-|  
|**Mozilla Firefox**(+)|Supported|Supported|Supported|Supported|Supported|Supported|-|  
|**Apple Safari** (+)|-|-|-|-|-|Supported|Supported|  
  
 **(+)** Latest publicly released version  
  
 If you are using a SharePoint product that is integrated with [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)], see  [Plan browser support in SharePoint 2013](http://technet.microsoft.com//library/cc263526\(office.15\).aspx).  
  
###  <a name="bkmk_authentication"></a> Authentication Requirements  
 Browsers support specific authentication schemes that must be handled by the report server in order for the client request to succeed. The following table identifies the default authentication types supported by each browser running on a Windows operating system.  
  
|**Browser type**|**Supports**|**Browser default**|**Server default**|  
|----------------------|------------------|-------------------------|------------------------|  
|**Microsoft Edge** (+)|Negotiate, Kerberos, NTLM, Basic|Negotiate|Yes. The default authentication settings work with Edge.|  
|**Microsoft Internet Explorer**|Negotiate, Kerberos, NTLM, Basic|Negotiate|Yes. The default authentication settings work with Internet Explorer.|  
|**Google Chrome**(+)|Negotiate, NTLM, Basic|Negotiated|Yes. The default authentication settings work with Chrome.|  
|**Mozilla Firefox**(+)|NTLM, Basic|NTLM|Yes. The default authentication settings work with Firefox.|  
|**Apple Safari**(+)|Basic|Basic|Yes. The default authentication settings work with Safari.|  
  
 **(+)** Latest publicly released version  
  
### Script Requirements for Viewing Reports  
 To use the report viewer, configure your browser to run scripts.  
  
 If scripting is not enabled, you will see an error message similar to the following when you open a report:  
  
-   **Your browser does not support scripts or has been configured to not allow scripts to run. Click here to view this report without scripts**.  
  
 If you choose to view the report without script support, the report is rendered in HTML without report viewer capabilities such as the report toolbar and the document map.  
  
> [!NOTE]  
>  The report toolbar is part of the HTML Viewer component. By default the toolbar appears at the top of every report that is rendered in a browser window. The report viewer provides features include the ability to search the report for information, scroll to a specific page, and adjust the page size for viewing purposes. For more information about the report toolbar or HTML Viewer, see [HTML Viewer and the Report Toolbar](../../Topics/TopicNameNotContainA/HTML-Viewer-and-the-Report-Toolbar.md).  
  
##  <a name="bkmk_controls"></a> Browser Support for ReportViewer Web Server Controls in Visual Studio  
 The ReportViewer Web server control is used to embed report functionality in an ASP.NET web application. The controls are included with Visual Studio and support different browsers and browser versions than the other components described in this topic. The type of browser used to view the application determines the kind of ReportViewer functionality that you can provide in your application. Use the table provided in this topic to determine which of the supported browsers are subject to report functionality restrictions and the supported platforms.  
  
 Use a browser that has script support enabled. If the browser cannot run scripts, you cannot view the report.  
  
||||||||  
|-|-|-|-|-|-|-|  
|**Browser**|**Windows 10**|**Windows 8** and **Windows 8.1**|**Windows 7**|**Windows Server 2012** and **2012 R2**|**Windows Server 2008 R2**|**Mac OS X 10.7 – 10.10**|  
|**Internet Explorer 11  & 10**|Supported|Supported|Supported|Supported|Supported|-|  
|**Google Chrome** (+)|Supported|Supported|Supported|Supported|Supported|-|  
|**Mozilla Firefox**(+)|Supported|Supported|Supported|Supported|Supported|-|  
|**Apple Safari**(+)|-|-|-|-|-|-|  
  
 **(+)** Latest publicly released version  
  
##  <a name="bkmk_powerview"></a> Power View Browser Support  
  
|**Browser**|**Windows 10**|**Windows 8 and 8.1**|**Windows 7**|**Windows Server 2012 and 2012 R2**|**Windows Server 2008 R2**|**Mac OS X 10.7 – 10.10**|  
|-----------------|--------------------|---------------------------|-------------------|-----------------------------------------|--------------------------------|-------------------------------|  
|**Microsoft Internet Explorer 11 & 10**|Supported|Supported|Supported|Supported|Supported|-|  
|**Google Chrome  (\*)**(+)|Supported|Supported|Supported|Supported|Supported|-|  
|**Mozilla Firefox** (+)|Supported|Supported|Supported|Supported|Supported|Supported|  
|**Apple Safari** (+)|-|-|-|-|-|Supported|  
  
 **(+)** Latest publicly released version  
  
 **(\*)** Chrome will stop supporting the Netscape Plug-in API (NPAPI), used by Silverlight. **Power View is dependent on Silverlight**. For more information, see [The Final Countdown for NPAPI](http://blog.chromium.org/2014/11/the-final-countdown-for-npapi.html).  
  
 For more information on the SharePoint 2013 browser support, see [Plan browser support in SharePoint 2013](http://technet.microsoft.com//library/cc263526\(office.15\).aspx).  
  
## See Also  
 [Finding and Viewing Reports in the web portal (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Finding-and-Viewing-Reports-in-the-web-portal--Report-Builder-and-SSRS-.md)   
 [Reporting Services Tools](../../Topics/TopicNameNotContainA/Reporting-Services-Tools.md)   
 [Report Manager  (SSRS Native Mode)](../../Topics/TopicNameNotContainA/Report-Manager---SSRS-Native-Mode-.md)   
 [HTML Viewer and the Report Toolbar](../../Topics/TopicNameNotContainA/HTML-Viewer-and-the-Report-Toolbar.md)   
 [URL Access Parameter Reference](../../Topics/TopicNameNotContainA/URL-Access-Parameter-Reference.md)