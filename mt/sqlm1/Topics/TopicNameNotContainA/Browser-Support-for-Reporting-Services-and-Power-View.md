---
title: Browser Support for Reporting Services and Power View
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 48a75bbb-0029-4c43-891d-dc8f4fc0ebe1
---
# Browser Support for Reporting Services and Power View
  This topic summarizes  the browser versions supported for managing and viewing [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] reports and includes information on browser support for the Report Viewer controls in Visual Studio.  
  
 **Applies to:** [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Native mode | [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint mode  
  
##  <a name="bkmk_webportal"></a> Browser Requirements for the web portal

The following is the current list of browsers supported for the [!INCLUDE[ssRSWebPortal](../../Token\Other/ssRSWebPortal.md)].

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*
- Microsoft Edge \(\+\)
- Microsoft Internet Explorer 10 or 11
- Google Chrome \(\+\)
- Mozilla Firefox \(\+\)

**Apple OS X**  
*OS X 10.9-10.11*

- Apple Safari \(\+\)
- Google Chrome \(\+\)
- Mozilla Firefox \(\+\)

**Apple iOS**  
*iPhone and iPad with iOS 9*

- Apple Safari \(\+\)

**Google Android**  
*Phones and tablets with Android 4.4 (KitKat) or later*

- Google Chrome \(\+\)

 **\(\+\)** Latest publicly released version  
  
##  <a name="bkmk_reportviewer"></a> Browser Requirements for the ReportViewer web control (2015) 
 The following is the current list of browsers supported with the ReportViewer web control (2015). The report viewer supports viewing reports from [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] web portal and SharePoint libraries.  
  
**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

- Microsoft Edge \(\+\)
- Microsoft Internet Explorer 10 or 11
- Google Chrome \(\+\)
- Mozilla Firefox \(\+\)

**Apple OS X**  
*OS X 10.9-10.11*

- Apple Safari \(\+\)
  
 **\(\+\)** Latest publicly released version  
  
 If you are using a SharePoint product that is integrated with [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)], see  [Plan browser support in SharePoint 2016](http://technet.microsoft.com//library/cc263526\(v=office.16\).aspx).  
  
###  <a name="bkmk_authentication"></a> Authentication Requirements  
 Browsers support specific authentication schemes that must be handled by the report server in order for the client request to succeed. The following table identifies the default authentication types supported by each browser running on a Windows operating system.  
  
|**Browser type**|**Supports**|**Browser default**|**Server default**|  
|----------------------|------------------|-------------------------|------------------------|  
|**Microsoft Edge** \(\+\)|Negotiate, Kerberos, NTLM, Basic|Negotiate|Yes. The default authentication settings work with Edge.|  
|**Microsoft Internet Explorer**|Negotiate, Kerberos, NTLM, Basic|Negotiate|Yes. The default authentication settings work with Internet Explorer.|  
|**Google Chrome**\(\+\)|Negotiate, NTLM, Basic|Negotiate|Yes. The default authentication settings work with Chrome.|  
|**Mozilla Firefox**\(\+\)|NTLM, Basic|NTLM|Yes. The default authentication settings work with Firefox.|  
|**Apple Safari**\(\+\)|NTLM, Basic|Basic|Yes. The default authentication settings work with Safari.|  
  
 **\(\+\)** Latest publicly released version  
  
### Script Requirements for Viewing Reports  
 To use the report viewer, configure your browser to run scripts.  
  
 If scripting is not enabled, you will see an error message similar to the following when you open a report:  
  
-   **Your browser does not support scripts or has been configured to not allow scripts to run. Click here to view this report without scripts**.  
  
 If you choose to view the report without script support, the report is rendered in HTML without report viewer capabilities such as the report toolbar and the document map.  
  
> [!NOTE]  
>  The report toolbar is part of the HTML Viewer component. By default the toolbar appears at the top of every report that is rendered in a browser window. The report viewer provides features include the ability to search the report for information, scroll to a specific page, and adjust the page size for viewing purposes. For more information about the report toolbar or HTML Viewer, see [HTML Viewer and the Report Toolbar](../../Topics\TopicNameNotContainA/HTML-Viewer-and-the-Report-Toolbar.md).  
  
##  <a name="bkmk_controls"></a> Browser Support for ReportViewer Web Server Controls in Visual Studio  
 The ReportViewer Web server control is used to embed report functionality in an ASP.NET web application. The controls are included with Visual Studio and support different browsers and browser versions than the other components described in this topic. The type of browser used to view the application determines the kind of ReportViewer functionality that you can provide in your application. Use the table provided in this topic to determine which of the supported browsers are subject to report functionality restrictions and the supported platforms.  
  
 Use a browser that has script support enabled. If the browser cannot run scripts, you cannot view the report.  
  
**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

- Microsoft Edge \(\+\)
- Microsoft Internet Explorer 10 or 11
- Google Chrome \(\+\)
- Mozilla Firefox \(\+\)
  
 **\(\+\)** Latest publicly released version  
  
##  <a name="bkmk_powerview"></a> Power View Browser Support  

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

- Microsoft Internet Explorer 10 or 11
- Mozilla Firefox \(\+\)
  
**Apple OS X**  
*OS X 10.9-10.11*

- Apple Safari \(\+\)
  
 **\(\+\)** Latest publicly released version  
  
 For more information on the SharePoint 2016 browser support, see [Plan browser support in SharePoint 2013](http://technet.microsoft.com//library/cc263526\(v=office.16\).aspx).  
  
## See Also  
[Finding and Viewing Reports in the web portal &#40;Report Builder and SSRS&#41;](assetId:///8556807e-f2e2-4a7b-bb1b-ac5ea1872e51)  
[Reporting Services Tools](../../Topics\TopicNameNotContainA/Reporting-Services-Tools.md)  
[Web portal (SSRS Native Mode)](assetId:///7349e626-6ed5-4d21-b05f-cf042ad9ad70)  
[HTML Viewer and the Report Toolbar](../../Topics\TopicNameNotContainA/HTML-Viewer-and-the-Report-Toolbar.md)  
[URL Access Parameter Reference](../../Topics\TopicNameNotContainA/URL-Access-Parameter-Reference.md)  