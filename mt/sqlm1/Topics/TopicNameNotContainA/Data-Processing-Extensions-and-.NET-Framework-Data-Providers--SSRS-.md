---
title: Data Processing Extensions and .NET Framework Data Providers (SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 42a5afb5-f4c8-4957-b1fd-77bf39afa5be
---
# Data Processing Extensions and .NET Framework Data Providers (SSRS)
  A [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] data processing extension is a component installed with [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)], designed to retrieve data from a specific type of data source and to provide extra functionality to support report design and report processing. A [!INCLUDE[dnprdnshort](../../Token\Other/dnprdnshort_md.md)] data provider is a component available from [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] or third\-party sources that supports [System.Data](assetId:///N:System.Data) interfaces that allow you to retrieve and to modify data from a specific type of data source.  
  
## Understanding a Data Processing Extension  
 A [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] data processing extension supports a subset of the [System.Data](assetId:///N:System.Data) interfaces. Data processing extensions require only read\-only access to a data source, so the interfaces for write and update are not implemented. Each data processing extension can provide custom features to support report processing. For example, a data processing extension might support the following types of features:  
  
-   Managing credentials separately from the connection string  
  
-   Supporting multivalue parameters  
  
-   Retrieving server aggregates, which are calculated on the data source  
  
-   Retrieving data properties as well as data values from the data source  
  
## Understanding a Data Provider  
 A [!INCLUDE[dnprdnshort](../../Token\Other/dnprdnshort_md.md)] data provider \(sometimes known as a driver\) supports a standard set of [System.Data](assetId:///N:System.Data) interfaces for reading, writing, and updating data on a data source. A data provider can be used when there is no data processing extension available for a specific type of data source. Many third\-party standard [!INCLUDE[dnprdnshort](../../Token\Other/dnprdnshort_md.md)] data providers are available.  
  
 Because [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] has an extensible data provider architecture, you can build a custom data processing extension to include the extra functionality supplied by [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] data processing extensions. For more information, see [Implementing a Data Processing Extension](../Topic/Implementing%20a%20Data%20Processing%20Extension.md). For third\-party data processing extensions, see the documentation that comes with the third\-party data processing extension.  
  
> [!NOTE]  
>  A [!INCLUDE[dnprdnshort](../../Token\Other/dnprdnshort_md.md)] data provider or custom data processing extension must be installed and registered before it can be used to access data from a data source. The data processing extension must be installed and registered both on the reporting client to author the report and on the report server to view the published report. Not all data providers are designed to work in a server environment. For more information, see [Register a Standard .NET Framework Data Provider &#40;SSRS&#41;](../Topic/Register%20a%20Standard%20.NET%20Framework%20Data%20Provider%20\(SSRS\).md).and [Deploying a Data Processing Extension](../Topic/Deploying%20a%20Data%20Processing%20Extension.md).  
  
## See Also  
 [Data Processing Extensions Overview](../Topic/Data%20Processing%20Extensions%20Overview.md)   
 [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../Topic/Report%20Embedded%20Datasets%20and%20Shared%20Datasets%20\(Report%20Builder%20and%20SSRS\).md)  
  
  