---
title: The data connection path in the workbook points to a file on the local drive or is an invalid URI. The following connections failed to refresh: Power Pivot Data
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bd22e41a-0931-4d32-888a-633a3046fc5e
---
# The data connection path in the workbook points to a file on the local drive or is an invalid URI. The following connections failed to refresh: Power Pivot Data
  For Excel workbooks that contain [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] data, Excel Services returns this error if it cannot connect to embedded data sources.  
  
## Details  
  
|||  
|-|-|  
|Applies to|[!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] for SharePoint|  
|Product Version|[!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)]|  
|Cause|Excel Services is configured to only allow data connections from .odc files that are in a trusted data connection library.|  
|Message Text|The data connection path in the workbook points to a file on the local drive or is an invalid URI. The following connections failed to refresh: [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] Data|  
  
## Explanation  
 [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] workbooks contain embedded data connections. To support workbook interaction through slicers and filters, Excel Services must be configured to allow external data access through embedded connection information. External data access is required for retrieving [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] data that is loaded on [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] servers in the farm.  
  
## User Action  
 Change the configuration settings to allow embedded data source connections.  
  
1.  In Central Administration, in Application Management, click **Manage service applications**.  
  
2.  Click **Excel Services Application**.  
  
3.  Click **Trusted File Location**.  
  
4.  Click **http:\/\/** or the location you want to configure.  
  
5.  In External Data, in Allow External Data, click **Trusted data connection libraries and embedded**.  
  
6.  Click **OK**.  
  
 Alternatively, you can create a new trusted location for sites that contain [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] workbooks, and then modify the configuration settings for just that site. For more information, see [Create a trusted location for Power Pivot sites in Central Administration](../../Topics\TopicNameContainA/Create-a-trusted-location-for-Power-Pivot-sites-in-Central-Administration.md).  
  
  