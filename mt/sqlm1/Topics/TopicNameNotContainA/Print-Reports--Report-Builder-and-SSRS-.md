---
title: Print Reports (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4bad1b6e-7d94-4b17-9502-ccd3dce0fdd9
---
# Print Reports (Report Builder and SSRS)
  After you save a report to a report server, you can view and print the report from a browser, Report Manager, or any application that you use to view an exported report. Before saving a report, you can print it when you preview it.  
  
 All print processing is performed on demand and on the client computer. There is no server\-side print functionality that enables you to route a print job directly from a report server to a printer that is attached to the Web server. Printers and print options are selected by individual report users by using a standard **Print** dialog box.  
  
 Report authors who design reports specifically for print output can use page breaks, page headers and footers, expressions, and background images to create a print\-based design. Examples of report design elements intended for print output might include terms and conditions that you print on the back of every report, or graphic and text elements that mimic letterhead.  
  
 Due to the way pagination is implemented for different rendering formats, you might not be able to achieve optimum print output results for every report in every rendering format. The following list provides examples:  
  
1.  Report pages are designed to accommodate variable amounts of data. Reports that include a matrix, for example, can cause a page to grow both horizontally and vertically depending on whether a user interactively toggles rows and columns. A user who does not expand a matrix will get different print results than a user who does.  
  
2.  You cannot combine landscape and portrait mode pages in the same report, nor is there a way to create a print\-based layout that replaces or exists alongside the layout of a report as rendered in a browser or other application.  
  
3.  For most exported reports, report printouts include everything that is visible on the report, as viewed by the user on a computer monitor. White space from the report design surface is preserved. To add or remove extra blank pages horizontally, change the report page width.  
  
> [!NOTE]  
>  HTML report printouts may contain only the content on the first page if you are using the browser's Print command. You can achieve better results if you print HTML reports using the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] client printing functionality. For more information, see [Print Reports from a Browser with the Print Control &#40;Report Builder and SSRS&#41;](../Topic/Print%20Reports%20from%20a%20Browser%20with%20the%20Print%20Control%20\(Report%20Builder%20and%20SSRS\).md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
## In This Section  
 [Print Reports from a Browser with the Print Control &#40;Report Builder and SSRS&#41;](../Topic/Print%20Reports%20from%20a%20Browser%20with%20the%20Print%20Control%20\(Report%20Builder%20and%20SSRS\).md)  
 Describes how to use client\-side printing to print reports from your Web browser or Report Manager.  
  
 [Print Reports from Other Applications &#40;Report Builder and SSRS&#41;](../Topic/Print%20Reports%20from%20Other%20Applications%20\(Report%20Builder%20and%20SSRS\).md)  
 Describes how to print reports exported to another application.  
  
 [Print a Report &#40;Report Builder and SSRS&#41;](../Topic/Print%20a%20Report%20\(Report%20Builder%20and%20SSRS\).md)  
 Provides step\-by\-step instructions on how to print a report, how to control the margins on a page, and on how to specify the paper size for reports that will be rendered by hard\-page break renderers: PDF, Image, or Print.  
  
## See Also  
 [Export Reports &#40;Report Builder and SSRS&#41;](../Topic/Export%20Reports%20\(Report%20Builder%20and%20SSRS\).md)   
 [Page Headers and Footers &#40;Report Builder and SSRS&#41;](../Topic/Page%20Headers%20and%20Footers%20\(Report%20Builder%20and%20SSRS\).md)   
 [Images &#40;Report Builder and SSRS&#41;](../Topic/Images%20\(Report%20Builder%20and%20SSRS\).md)   
 [Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](../Topic/Pagination%20in%20Reporting%20Services%20\(Report%20Builder%20%20and%20SSRS\).md)  
  
  