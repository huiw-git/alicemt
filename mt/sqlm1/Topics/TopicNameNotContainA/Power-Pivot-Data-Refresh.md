---
title: Power Pivot Data Refresh
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ac8358a3-ee71-44c7-8ee6-ac7afe3ebaa4
---
# Power Pivot Data Refresh
  After you create a workbook that contains [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] data, you might want to periodically refresh the data by rerunning a query or command to get updated information from the sources you used originally to create the workbook. This process is called **data refresh**, and you can refresh data on demand in [!INCLUDE[ssGeminiClient](../../Token\Other/ssGeminiClient_md.md)], or as a scheduled operation that runs as an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] process on an application server in a SharePoint farm. For more information, see:  
  
-   [Power Pivot Data Refresh with SharePoint 2010](assetId:///01b54e6f-66e5-485c-acaa-3f9aa53119c9)  
  
-   [Configure the Power Pivot Unattended Data Refresh Account \(Power Pivot for SharePoint\)](assetId:///81401eac-c619-4fad-ad3e-599e7a6f8493)  
  
-   [Configure Stored Credentials for Power Pivot Data Refresh \(Power Pivot for SharePoint\)](assetId:///987eff0f-bcfe-4bbd-81e0-9aca993a2a75)  
  
-   [Schedule a Data Refresh \(Power Pivot for SharePoint\)](assetId:///8571208f-6aae-4058-83c6-9f916f5e2f9b)  
  
-   [View Data Refresh History &#40;Power Pivot for SharePoint&#41;](../Topic/View%20Data%20Refresh%20History%20\(Power%20Pivot%20for%20SharePoint\).md)  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] and SharePoint Server 2013 Excel Services use a different architecture for data refresh of [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] data models. The SharePoint 2013 supported architecture utilizes Excel Services as the primary component to load [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] data models. The previous data refresh architecture used relied on a server running [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] System Service and [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] in SharePoint mode to load data models. For more information, see the following:  
>   
>  -   [Power Pivot Data Refresh with SharePoint 2013](../../Topics\TopicNameNotContainA/Power-Pivot-Data-Refresh-with-SharePoint-2013.md)  
> -   [Upgrade Workbooks and Scheduled Data Refresh &#40;SharePoint 2013&#41;](../Topic/Upgrade%20Workbooks%20and%20Scheduled%20Data%20Refresh%20\(SharePoint%202013\).md)  
  
  