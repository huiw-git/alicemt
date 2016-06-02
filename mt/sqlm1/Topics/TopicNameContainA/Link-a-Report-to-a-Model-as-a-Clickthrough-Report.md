---
title: Link a Report to a Model as a Clickthrough Report
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3af42de3-67ef-41c2-bc8a-7045baec6f63
robots: noindex,nofollow
---
# Link a Report to a Model as a Clickthrough Report
  Instead of using the default clickthrough report templates, you can create a Report Builder report and then link it to a specific entity in the report model. When the person viewing the report clicks the interactive data in the main report, this report is displayed as a clickthrough report. To link a report to an entity, use [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Report Manager.  
  
> [!IMPORTANT]  
>  The primary, or base, entity that is used in the report must to be the same entity to which the report is linked.  
  
### To start Report Manager from a browser  
  
1.  Open [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Internet Explorer 6.0 or later.  
  
2.  In the address bar of the Web browser, type the Report Manager URL. By default, the URL is http:\/\/\<*ComputerName*\>\/reports.  
  
### To create a customized clickthrough report  
  
1.  Navigate to the report model to which you want to add the customized clickthrough report.  
  
2.  Double\-click the report model.  
  
3.  Click **Clickthrough**.  
  
4.  Select the entity to which you want to attach the customized clickthrough report.  
  
    > [!NOTE]  
    >  This entity must be the same as the base entity of the customized clickthrough report.  
  
5.  To display the customized report when a single instance of the selected entity is clicked, click the Single instance report **Browse** button.  
  
     \-or\-  
  
     To display the customized report when a multiple instance of the selected entity is clicked, click the Multiple instance report **Browse** button.  
  
6.  Select the report and then click **OK**.  
  
7.  Click **Apply**.  
  
## See Also  
 [Clickthrough Reports &#40;SSRS&#41;](../Topic/Clickthrough%20Reports%20\(SSRS\).md)  
  
  