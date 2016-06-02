---
title: Create a trusted location for Power Pivot sites in Central Administration
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
ms.assetid: a666f365-cd93-43a3-9d3d-e429dfc19b66
---
# Create a trusted location for Power Pivot sites in Central Administration
  Excel Services lets you specify which locations are valid repositories for workbooks that you open on a SharePoint server. These locations are called 'trusted locations', and you can use different configuration settings for each trusted location you create. For a deployment of [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] for SharePoint, you might consider creating a trusted location for sites that contain [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] workbooks so that you can apply the settings that work best for [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] data access, while preserving default settings for the rest of the farm.  
  
 This topic contains the following sections:  
  
 [Prerequisites](#prereq)  
  
 [Overview](#overview)  
  
 [Create a Trusted Location for Power Pivot Data Access](#create)  
  
## Prerequisites  
 You must be a farm or service administrator to designate a URL as a trusted location.  
  
 You must know the URL address of the SharePoint site that contains the [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] Gallery or other library that stores your workbooks. To get the address, open the site that contains the library, right\-click **[!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] Gallery**, select **Properties**, and then copy the first part of the Address \(URL\) that contains the server name and site path.  
  
##  <a name="overview"></a> Overview  
 An initial installation of Excel Services specifies 'http:\/\/' as its trusted location, which means that workbooks from any site in the farm can be opened on the server. If you require tighter control over which locations are considered trustworthy, you can create new trusted locations that map to specific sites in your farm, and then vary the settings and permissions for each one.  
  
 Creating a new trusted location for sites that host [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] workbooks is especially useful if you want to preserve default values for the rest of the farm, while applying different settings that work best for [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] data access. For example, a trusted location that is optimized for [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] workbooks could have a maximum workbook size of 50 MB, while the rest of the farm uses the default value of 10MB.  
  
 Creating a trusted location is recommended if you are using [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] Gallery libraries to preview published workbooks and you encounter data refresh warnings instead of the preview image you expect. [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] Gallery renders thumbnail images of reports and workbooks using data and presentation information within the document. If Warn on Data Refresh is enabled for a trusted location, [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] Gallery might not have sufficient permissions to perform the refresh, causing an error to appear instead of the thumbnail image. Adding a site that contains [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] Gallery as a new trusted location can eliminate this problem.  
  
##  <a name="create"></a> Create a Trusted Location for Power Pivot Data Access  
  
1.  In Central Administration, in Application Management, click **Manage service applications**.  
  
2.  Click the Excel Services Service Application.  
  
3.  Click **Trusted File Locations**.  
  
4.  Click **Add Trusted File Location**.  
  
5.  Enter the URL of a site that contains a [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] Gallery library.  
  
6.  In Location Type, select **Microsoft SharePoint Foundation**.  
  
    > [!IMPORTANT]  
    >  UNC and HTTP location types are not supported for [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] data access.  
  
7.  Accept all of the default settings for properties in Session Management, Workbook Properties, and Calculation Behavior.  
  
8.  In Workbook Properties, set **Maximum Workbook Size** to **50**. This aligns the upper limit for workbook file size to the upper limit for file uploads to the parent web application. If your workbooks are larger than 50 megabytes, you must further increase the file size limit. For more information, see [Configure Maximum File Upload Size &#40;Power Pivot for SharePoint&#41;](../Topic/Configure%20Maximum%20File%20Upload%20Size%20\(Power%20Pivot%20for%20SharePoint\).md).  
  
9. In External Data, verify that Allow External Data is set to **Trusted data connection libraries and embedded**. This setting is required for [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] data access in a workbook.  
  
10. Also in External Data, for Warn on Refresh, clear the checkbox for **Refresh warning enabled**. Clearing the checkbox allows [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] Gallery to bypass routine warning messages and show preview images of a workbook instead.  
  
11. Click **OK**.  
  
## See Also  
 [Power Pivot Gallery](../../Topics\TopicNameNotContainA/Power-Pivot-Gallery.md)   
 [Create and Customize Power Pivot Gallery](../../Topics\TopicNameNotContainA/Create-and-Customize-Power-Pivot-Gallery.md)   
 [Use Power Pivot Gallery](../../Topics\TopicNameNotContainA/Use-Power-Pivot-Gallery.md)  
  
  