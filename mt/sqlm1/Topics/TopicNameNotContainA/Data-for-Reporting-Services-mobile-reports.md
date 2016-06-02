---
title: Data for Reporting Services mobile reports
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 91138ef8-ddb4-4ac5-a1e4-fa4cf1c58dcc
---
# Data for Reporting Services mobile reports
The [!INCLUDE[PRODUCT_NAME](../../Token\Other/SS_MobileReptPub_Long.md)] data model is simple. Data is imported into [!INCLUDE[PRODUCT_NAME](../../Token\Other/SS_MobileReptPub_Short.md)] as a collection of datasets. Formal relationships between datasets aren't necessary. Lookups from one dataset to another work as long as the key values match. Date/time aggregations are handled by the mobile report runtime and they will match between different datasets, even if the date/time data granularity is different between datasets.   
  
You can import data from two types of sources:   
  
* **Local Excel files**: Select an Excel document and pick which worksheet(s) to import. After import, the data is stored within the mobile report definition. To refresh the data from the original Excel file, use the **Refresh Data** command in the upper-right corner on the [!INCLUDE[PRODUCT_NAME](../../Token\Other/SS_MobileReptPub_Short.md)] **Data** tab. Read more about [preparing Excel data for SSRS mobile reports](../../Topics\TopicNameNotContainA/Prepare-Excel-data-for-Reporting-Services-mobile-reports.md).  
  
* **[!INCLUDE[PRODUCT_NAME](../../Token\Other/SERVER_PRODUCT_NAME.md)] shared datasets**: Browse the list of published datasets on the server and select the ones to add to the mobile report. Mobile reports based on server data always stay connected to the original server datasets and reflect the latest state of the data on the server. See a [list of supported data sources](https://msdn.microsoft.com/library/ms159219.aspx).   
  
  Read more about [getting data from shared datasets in Mobile Report Publisher](../../Topics\TopicNameNotContainA/Get-data-from-shared-datasets-in-Reporting-Services-mobile-reports.md).  
  
After you import data into [!INCLUDE[PRODUCT_NAME](../../Token\Other/SS_MobileReptPub_Short.md)], the rest of the mobile report creation and design experience is the same, regardless of where the data came from.   
  
## Connect mobile report elements to data ##  
  
Each [!INCLUDE[PRODUCT_NAME](../../Token\Other/SHORT_PRODUCT_NAME.md)] element contains one or more data settings. For example, the Radial Gauge element contains two data settings: Main Value and Comparison Value. Each of these settings points to exactly one field (column) in a specific dataset.   
  
The mobile report runtime provides aggregated values for the gauge, based on user selections. Note that the Comparison Value of the same Radial Gauge instance can be bound to a field from a different dataset.   
  
### See also  
-  [Prepare data for Reporting Services mobile reports](../../Topics\TopicNameNotContainA/Prepare-data-for-Reporting-Services-mobile-reports.md)
- [Create and publish mobile reports with SQL Server Mobile Report Publisher](../../Topics\TopicNameNotContainA/Create-mobile-reports-with-SQL-Server-Mobile-Report-Publisher.md)  
- [Get data from shared datasets](../../Topics\TopicNameNotContainA/Get-data-from-shared-datasets-in-Reporting-Services-mobile-reports.md)
- [Retain date formatting for Analysis Services data in mobile reports](Retain%20date%20formatting%20for%20Analysis%20Services%20in%20mobile%20reports%20%7C%20Reporting%20Services.md) 
  
  
