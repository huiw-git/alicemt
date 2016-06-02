---
title: This workbook contains one or more queries that refresh external data.
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aa65c992-eb41-4032-9e11-a9ba871b6a3c
---
# This workbook contains one or more queries that refresh external data.
  For Excel workbooks that contain [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] data, Excel Services shows this warning when it detects connection information and prompts you to enable or disable queries for this workbook.  
  
## Details  
  
|||  
|-|-|  
|Product Name|[!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] for SharePoint|  
|Product Version|[!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)]|  
|Cause|Excel Services is configured to warn on data refresh.|  
|Message Text|This workbook contains one or more queries that refresh external data. A malicious user can design a query to access confidential information and distribute it to other users or perform other harmful actions.<br /><br /> If you trust the source of this workbook, click Yes to enable queries to external data in this workbook. If you are not sure, click No so that changes are not applied to your workbook.<br /><br /> Do you want to enable queries to external data in this workbook?|  
  
## Explanation  
 [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] workbooks contain embedded data connection strings that are used by Excel to communicate with an external [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] server that loads and calculates the data. When warn on data refresh is enabled, Excel Services detects this connection string and warns the user accordingly.  
  
 To filter and slice [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] data in the workbook, queries must be enabled. Be sure that you enable queries for only those [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] workbooks that you trust.  
  
## User Action  
 Click **Yes** to enable queries.  
  
 You can also change the configuration settings so that warn on refresh no longer occurs:  
  
1.  In Central Administration, in Application Management, click **Manage service applications**.  
  
2.  Click **Excel Services Application**.  
  
3.  Click **Trusted File Location**.  
  
4.  Click **http:\/\/** or the location you want to configure.  
  
5.  In External Data, clear the checkbox for **Warn on data refresh**.  
  
6.  Click **OK**.  
  
 Alternatively, you can create a new trusted location for sites that contain [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] workbooks, and then modify the configuration settings for just that site. For more information, see [Create a trusted location for Power Pivot sites in Central Administration](../../Topics\TopicNameContainA/Create-a-trusted-location-for-Power-Pivot-sites-in-Central-Administration.md).  
  
  