---
title: HTML Viewer and the Report Toolbar
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cd86b319-babd-45af-a6a4-f659fdcc40c3
---
# HTML Viewer and the Report Toolbar
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] provides an HTML Viewer that is used to display reports on demand as they are requested from the report server. HTML Viewer provides a framework for viewing reports in HTML. It includes a report toolbar, a parameter section, a credentials section, and a document map. The report toolbar in HTML Viewer includes features you can use to work with your report, including export options so that you can view your report in formats other than HTML. The parameter section and document map appear only when you open reports that are configured to use parameters and a document map control.  
  
 Although you cannot modify the report toolbar, you can configure parameters on a report URL to hide it on a report. For more information about hiding the report toolbar, see [URL Access Parameter Reference](../../Topics\TopicNameNotContainA/URL-Access-Parameter-Reference.md).  
  
## Report Toolbar  
 The report toolbar provides page navigation, zoom, refresh, search, export, print, and data feed functionality for reports that are rendered in the HTML rendering extension.  
  
 Print functionality is optional. When it is available, a Printer icon appears on the report toolbar. On first use, clicking the Printer icon downloads an ActiveX control that you must install. Once the control is installed, clicking the Printer icon opens a Print dialog box so that you can select from the printers that are configured for your computer. Print availability is determined by server settings and browser settings. For more information, see [Print Reports from a Browser with the Print Control &#40;Report Builder and SSRS&#41;](../Topic/Print%20Reports%20from%20a%20Browser%20with%20the%20Print%20Control%20\(Report%20Builder%20and%20SSRS\).md) and [Enable and Disable Client-Side Printing for Reporting Services](../../Topics\TopicNameNotContainA/Enable-and-Disable-Client-Side-Printing-for-Reporting-Services.md).  
  
 The report toolbar is similar to the one shown in the following illustration. The report toolbar that you see may differ from the illustration based on report features or the rendering options that are available.  
  
 ![Report toolbar](../../Images\Image\ImageNotContaina/ssrs_htmlviewer_toolbar.png "ssrs_htmlviewer_toolbar")  
  
 The following table describes commonly used features of the report toolbar. Each feature is identified by the control that you use to access it.  
  
|Use this icon or control||To|  
|------------------------------|-|--------|  
|![Page navigation controls](../../Images\Image\ImageNotContaina/htmlviewer_pagenav.gif "htmlviewer_pagenav")|**Page navigation controls**|Open the first or last page of a report, scroll through a report page by page, and open a specific page in a report. To view a specific page, type the page number and press ENTER.|  
|![Page display controls](../../Images\Image\ImageNotContaina/htmlviewer_pagesize.gif "htmlviewer_pagesize")|**Page display controls**|Enlarge or reduce the size of the report page. In addition to percentage\-based changes, you can select **Page Width** to fit the horizontal length of a report page in the browser window, or **Whole Page** to fit the vertical length of a report in the browser window. A **Zoom** option is supported by [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Internet Explorer 5.5 and later.|  
|![Search field](../../Images\Image\ImageNotContaina/htmlviewer_search.gif "htmlviewer_search")|**Search field**|Search for content in the report by typing a word or phrase that you want to find \(the maximum value length is 256 characters\). The search is case\-insensitive and starts at the page or section that is currently selected. Only visible content is included in a search operation. To search for subsequent occurrences of the same value, click **Next**.|  
|![Export formats](../../Images\Image\ImageNotContaina/htmlviewer_export.GIF "htmlviewer_export")|**Export formats**|Open a new browser window and render the report in the selected format. The formats that are available are determined by the rendering extensions that are installed on the report server. TIFF is recommended for printing. Click **Export** to view the report in the selected format.|  
|![Document map icon](../../Images\Image\ImageNotContaina/htmlviewer_docmap.GIF "htmlviewer_docmap")|**Document map icon**|Show or hide the document map pane in a report that includes a document map. A document map is a report navigation control similar to the navigation pane on a Web site. You can click on items in the document map to navigate to a specific group, page, or subreport.|  
|![Printer icon](../../Images\Image\ImageNotContaina/printer_icon.gif "printer_icon")|**Printer icon**|Open a Print dialog box so that you can specify print options and print a report. On first use, clicking this icon prompts you to download the print control.|  
||**Show and hide icons**|Show or hide parameter value fields and the **View Report** button in a report that includes parameters.|  
|![Browser refresh button on report toolbar](../../Images\Image\ImageNotContaina/htmlviewer_refresh.GIF "htmlviewer_refresh")|**Report refresh icon**|Refresh the report. Data for live reports will be refreshed. Cached reports will be reloaded from where they are stored.|  
|![htmlviewer_datafeed](../../Images\Image\ImageNotContaina/htmlviewer_datafeed.gif "htmlviewer_datafeed")|**Data feed icon**|Generated data feeds from reports.|  
|![ssrs_powerbi_button_reportwviewer](../../Images\Image\ImageNotContaina/ssrs_powerbi_button_reportwviewer.png "ssrs_powerbi_button_reportwviewer")|**Pin to Power BI Dashboard**|Pin support report items to a [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)]. If the button is not visible, the report server has not been integrated with [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)].  For more information, see [Power BI Report Server Integration &#40;Configuration Manager&#41;](../Topic/Power%20BI%20Report%20Server%20Integration%20\(Configuration%20Manager\).md).|  
  
### About Export Formats  
 From the report toolbar, you can select to view your report in a variety of formats. The formats that are available are determined by the rendering extensions that are installed on the report server. When you select another format, a second browser window is used to display the report, using a viewer associated with the export format you selected. If a viewer is not available for the format you select, you can select a different format.  
  
 The following export formats are included in a default report server installation. The list of export formats available to you may vary from those listed here.  
  
|Export format|Description|  
|-------------------|-----------------|  
|XML|View a report in XML syntax. Reports viewed in XML open in a new browser window.|  
|CSV|View a report in a comma\-delimited format. The report opens in an application that is associated with the CSV file type.|  
|PDF|View a report using a client\-side PDF viewer. You must have third\-party PDF viewer \(for example, Adobe Acrobat Reader\) to use this format.|  
|MHTML|View the report in an MIME\-encoded HTML format that keeps images and linked content together with a report.|  
|Excel|View the report in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Excel, an .xlsx file.|  
|PowerPoint|View the report in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] PowerPoint, a .pptx file.|  
|TIFF file|View the report in the default TIFF viewer. For some [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows clients, this is the Windows Picture and Fax Viewer. Select this format to a view a report in a page\-oriented layout.|  
|Word|View the report in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Word, a .docx file.|  
  
## Parameters  
 Parameters are values that are used to select specific data \(specifically, they are used to complete a query that selects the data for your report, or to filter the result set\). Parameters that are commonly used in reports include dates, names, and IDs. When you specify a value for a parameter, the report contains only the data that matches the value; for example, employee data based on an Employee ID parameter. Parameters correspond to fields on the report. After you specify a parameter, click **View Report** to get the data.  
  
 The report author defines the parameter values that are valid for each report. A report administrator can also set parameter values. To find out which parameter values are valid for your report, ask your report designer or administrator.  
  
## Credentials  
 Credentials are user name and password values that grant access to a data source. After you specify your credentials, click **View Report** to get the data. If a report requires you to log on, the data that you are authorized to see might differ from the data that another user sees. Consequently, two users can run the same report and get different results. In addition, some reports contain hidden areas that are revealed based on user logon credentials or selections made in the report itself. Hidden areas in the report are excluded from search operations, producing different search results than when all parts of the report are visible.  
  
## See Also  
 [Specify Credential and Connection Information for Report Data Sources](../../Topics\TopicNameNotContainA/Specify-Credential-and-Connection-Information-for-Report-Data-Sources.md)   
 [Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../Topic/Finding,%20Viewing,%20and%20Managing%20Reports%20\(Report%20Builder%20and%20SSRS%20\).md)   
 [Export Reports &#40;Report Builder and SSRS&#41;](../Topic/Export%20Reports%20\(Report%20Builder%20and%20SSRS\).md)  
  
  