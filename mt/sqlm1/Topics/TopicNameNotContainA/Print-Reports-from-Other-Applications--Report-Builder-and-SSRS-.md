---
title: Print Reports from Other Applications (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a5560581-fd57-4a45-b7ea-43b21a8a7419
---
# Print Reports from Other Applications (Report Builder and SSRS)
  Report Builder provides an export option that allows you to easily view a report in other applications. The **Export** command is available on the report toolbar that appears at the top of a report when you open it in a browser or Web\-based application. Exporting a report displays it in a different application \(for example, exporting a report to Excel opens the report in [!INCLUDE[ofprexcel](../../Token\Other/ofprexcel_md.md)]\). For printing purposes, exporting a report is recommended only if the application has specific printing features that you want to use.  
  
 To export a report to another application, you must have that application installed. For example, you must have Adobe Acrobat Reader installed on your computer before you can export to the Acrobat \(PDF\) format. If you choose to export a report to TIFF format, the report server places the report in a viewing application that is associated with the TIFF file type. Although the application used depends on which version of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows you have, typically this tool is Windows Picture and Fax Viewer. The default resolution corresponds to a screen resolution of 96 dots per inch \(DPI\). You can increase the resolution in Windows Picture and Fax Viewer to 300 DPI or 600 DPI to match the capabilities of your printer. For more information about adjusting the resolution, see the Windows product documentation.  
  
 If you choose Web archive \(also known as MHTML\), the report is exported to your default browser. Printing from the browser may result in report path information being added at the bottom of every page. In most cases, you can set browser options to omit path information on a printed page. For more information, see the product documentation for the browser you are using.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
## See Also  
 [Print a Report &#40;Report Builder and SSRS&#41;](../Topic/Print%20a%20Report%20\(Report%20Builder%20and%20SSRS\).md)   
 [Print Reports from a Browser with the Print Control &#40;Report Builder and SSRS&#41;](../Topic/Print%20Reports%20from%20a%20Browser%20with%20the%20Print%20Control%20\(Report%20Builder%20and%20SSRS\).md)   
 [Export Reports &#40;Report Builder and SSRS&#41;](../Topic/Export%20Reports%20\(Report%20Builder%20and%20SSRS\).md)   
 [Export a Report as Another File Type &#40;Report Builder and SSRS&#41;](../Topic/Export%20a%20Report%20as%20Another%20File%20Type%20\(Report%20Builder%20and%20SSRS\).md)   
 [Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../Topic/Finding,%20Viewing,%20and%20Managing%20Reports%20\(Report%20Builder%20and%20SSRS%20\).md)  
  
  